---
title: "CMake, how do I add libraries, includes, header files?"
date: 2012-03-05
forum: Programming Talk
---

### Post by test_tube_baby on 2012-03-05
I have a cpp program which uses MRPT (Mobile Robots programming toolkit) libraries, and compiles using CMake.

I want to include some more libraries in my cpp program, for example Aria and OpenCV.

When I normally compile Aria and OpenCV programs, I don't use CMake, but I use a makefile which includes the CFLAGS and the LDFLAGS.

However, how do I use these with CMake? I have tried a lot but I get the 'undefined reference to' errors.

Can someone provide me with a step-by-step guide to adding third-party headers to a CMake file? The only header I want included is Aria.h

This is my CMakeLists.txt file, you can see that I have tried to include Aria libraries but it still doesn't work.

```

PROJECT(mrpt_example1)

CMAKE_MINIMUM_REQUIRED(VERSION 2.4)
if(COMMAND cmake_policy)
      cmake_policy(SET CMP0003 NEW)  # Required by CMake 2.7+
endif(COMMAND cmake_policy)

# --------------------------------------------------------------------------
#   The list of "libs" which can be included can be found in:
#     http://www.mrpt.org/Libraries
#
#   The dependencies of a library are automatically added, so you only 
#    need to specify the top-most libraries your code depend on.
# --------------------------------------------------------------------------
find_path(usr/local/Aria/include NAMES Aria.h PATHS /usr/local/Aria/include/ REQUIRED)
#add_library(${ARIA_DIR}/include/ Aria.h)

find_library(ARIA_LIBRARY NAMES lAria lArNetworking lpthread ldl lrt PATHS /usr/local/Aria/lib)


include_directories(${ARIA_DIR}/include)
link_directories(${ARIA_DIR}/lib)

FIND_PACKAGE( MRPT REQUIRED base)

# Declare the target (an executable)
ADD_EXECUTABLE(mrpt_example1  
	test.cpp
	)
TARGET_LINK_LIBRARIES(mrpt_example1 ${MRPT_LIBS} ${ARIA_LIBS})

# Set optimized building:
IF(CMAKE_COMPILER_IS_GNUCXX AND NOT CMAKE_BUILD_TYPE MATCHES "Debug")
	SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -mtune=native")
ENDIF(CMAKE_COMPILER_IS_GNUCXX AND NOT CMAKE_BUILD_TYPE MATCHES "Debug")

```

---

