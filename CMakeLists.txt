cmake_minimum_required(VERSION 3.12)
project(leonid-sharp LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)

file(GLOB_RECURSE leonid-sharp-source "./src/*.cpp")
add_library(leonid-sharp STATIC ${leonid-sharp-source})
target_include_directories(leonid-sharp PUBLIC include)

if (CMAKE_BUILD_TYPE STREQUAL "Release")
    target_compile_definitions(leonid-sharp PUBLIC LEO_RELEASE)
else ()
    target_compile_definitions(leonid-sharp PUBLIC LEO_DEBUG)
endif ()

# sandbox
add_executable(leonid-sharp-sandbox sandbox.cpp)
target_link_libraries(leonid-sharp-sandbox PRIVATE leonid-sharp)
