---
title: "GLEW linkage error cmake"
date: 2012-02-29
forum: Programming Talk
---

### Post by gufide on 2012-02-29
Hi, I tried to include GLEW in my project, but I must use cmake because I choose to use kdevelop. here's my error:
```
[100%] Building CXX object CMakeFiles/fractal.dir/main.cpp.o
Linking CXX executable fractal
/usr/bin/ld: CMakeFiles/fractal.dir/main.cpp.o: undefined reference to symbol '__glewDeleteShader'
/usr/bin/ld: note: '__glewDeleteShader' is defined in DSO /usr/lib/libGLEW.so.1.5 so try adding it to the linker command line
/usr/lib/libGLEW.so.1.5: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [fractal] Error 1
make[1]: *** [CMakeFiles/fractal.dir/all] Error 2
make: *** [all] Error 2
*** Failed ***

```here's my cmakeList:

```
cmake_minimum_required(VERSION 2.6)
project(fractal)




# Set version information in a config.h file
set(myproject_VERSION_MAJOR 1)
set(myproject_VERSION_MINOR 0)
include_directories("${PROJECT_BINARY_DIR}")

# Define sources and executable
set(EXECUTABLE_NAME "fractal")
add_executable(fractal main.cpp) 

# Detect and add SFML
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" ${CMAKE_MODULE_PATH})
find_package(SFML 1.6 REQUIRED system window graphics network audio)
target_link_libraries(${EXECUTABLE_NAME} ${SFML_LIBRARIES})
INCLUDE(FindOpenGL REQUIRED)
INCLUDE(FindGLEW REQUIRED)
INCLUDE_DIRECTORIES(${OPENGL_INCLUDE_DIR})
INCLUDE_DIRECTORIES(${GLEW_INCLUDE_DIR})
# Install target
install(TARGETS ${EXECUTABLE_NAME} DESTINATION bin)


# CPack packaging
include(InstallRequiredSystemLibraries)
set(CPACK_PACKAGE_VERSION_MAJOR "${myproject_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${myproject_VERSION_MINOR}")
include(CPack)

```this is the find glew:
```
#
# Try to find GLEW library and include path.
# Once done this will define
#
# GLEW_FOUND
# GLEW_INCLUDE_PATH
# GLEW_LIBRARY
#

IF (WIN32)
FIND_PATH( GLEW_INCLUDE_PATH GL/glew.h
$ENV{PROGRAMFILES}/GLEW/include
${GLEW_ROOT_DIR}/include
DOC "The directory where GL/glew.h resides")

IF (NV_SYSTEM_PROCESSOR STREQUAL "AMD64")
FIND_LIBRARY( GLEW_LIBRARY
NAMES glew64 glew64s
PATHS
$ENV{PROGRAMFILES}/GLEW/lib
${PROJECT_SOURCE_DIR}/src/nvgl/glew/bin
${PROJECT_SOURCE_DIR}/src/nvgl/glew/lib
DOC "The GLEW library (64-bit)"
)
ELSE(NV_SYSTEM_PROCESSOR STREQUAL "AMD64")
FIND_LIBRARY( GLEW_LIBRARY
NAMES glew GLEW glew32 glew32s
PATHS
$ENV{PROGRAMFILES}/GLEW/lib
${PROJECT_SOURCE_DIR}/src/nvgl/glew/bin
${PROJECT_SOURCE_DIR}/src/nvgl/glew/lib
DOC "The GLEW library"
)
ENDIF(NV_SYSTEM_PROCESSOR STREQUAL "AMD64")
ELSE (WIN32)
FIND_PATH( GLEW_INCLUDE_PATH GL/glew.h
/usr/include
/usr/local/include
/sw/include
/opt/local/include
${GLEW_ROOT_DIR}/include
DOC "The directory where GL/glew.h resides")

FIND_LIBRARY( GLEW_LIBRARY
NAMES GLEW glew
PATHS
/usr/lib64
/usr/lib
/usr/local/lib64
/usr/local/lib
/sw/lib
/opt/local/lib
${GLEW_ROOT_DIR}/lib
DOC "The GLEW library")
ENDIF (WIN32)

SET(GLEW_FOUND "NO")
IF (GLEW_INCLUDE_PATH AND GLEW_LIBRARY)
SET(GLEW_LIBRARIES ${GLEW_LIBRARY})
SET(GLEW_FOUND "YES")
ENDIF (GLEW_INCLUDE_PATH AND GLEW_LIBRARY)


include(FindPackageHandleStandardArgs)
find_package_handle_standard_args(GLEW DEFAULT_MSG GLEW_LIBRARY GLEW_INCLUDE_PATH)
```

thanks

---

### Post by gufide on 2012-03-01
help me please, i'm new to cmake and I don't know how to find bug, I just want GLEW to work.

---

### Post by MadCow108 on 2012-03-01
adding ${GLEW_LIBRARIES} to target_link_libraries and moving the FindGLEW higher (or target_link_libraries lower) should suffice.

---

### Post by gufide on 2012-03-01
thanks, compile now working, but I got a warning:
```
/usr/bin/ld: warning: libGLEW.so.1.5, needed by /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../../lib/libsfml-graphics.so, may conflict with libGLEW.so.1.6

```

should I change it to 1.6 in cmake or 1.5 in my project?

---

### Post by MadCow108 on 2012-03-01
depends whether libsfml works with 1.6 and if you can recompile it against 1.6
if not you have no other choice than using 1.5 for your project as well.

---

