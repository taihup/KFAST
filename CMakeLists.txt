CMAKE_MINIMUM_REQUIRED(VERSION 2.8 FATAL_ERROR)

project(KFAST)

set(CMAKE_CXX_STANDARD 17)

FIND_PACKAGE(OpenCV REQUIRED)

SET(CMAKE_CXX_FLAGS "-pedantic -Ofast -std=gnu++17 -fomit-frame-pointer -mavx2 -march=native -mfma -flto -ftree-vectorize")

file(GLOB ROSTEN_SRC Rosten/*.c)

add_library(fast STATIC ${ROSTEN_SRC})
SET_TARGET_PROPERTIES(fast PROPERTIES LINKER_LANGUAGE C)

ADD_EXECUTABLE(KFAST main.cpp)
TARGET_LINK_LIBRARIES(KFAST ${OpenCV_LIBS} fast)
