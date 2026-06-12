---
title: "Need help with custom CMake script"
date: 2010-08-31
forum: Programming Talk
---

### Post by James78 on 2010-08-31
Hi, I'm having trouble with using CMake right now.

Currently, I have CMake setup find any required libraries and link them, all for Linux. But now I have ported my program to be able to compile with Windows and Linux, however I'd rather handle this all through CMake as it's easier.

What I would like to do, is SET(COMPILE_WINDOWS TRUE) on root/cmakelists.txt, then in root/src/cmakelists.txt put everything below "set(MAIN" in a conditional if (IF NOT COMPILE_WINDOWS), and have an if(COMPILE_WINDOWS) for CMakeMingw (copied from the CMake wiki site, and I posted it below).

For CMakeMing, I'm going to probably do something like this:

my idea: root/cmakelists.txt
```
cmake_minimum_required (VERSION 2.8.1)

# set to true to compile for Windows instead of Linux
set(COMPILE_WINDOWS false)

project(rstools)

add_subdirectory(src)
```

my idea: root/src/cmakelists.txt
```
# Set all variables..
set(MAIN defines.hpp functions.cpp functions.hpp main.cpp main.hpp parseflags.cpp parseflags.hpp)

if (not COMPILE_WINDOWS)
    set(CMAKE_MODULE_PATH "../cmake/modules/")

    # Make sure required dependencies are installed...
    find_package(libpopt-dev REQUIRED)
    find_package(libcurl4-openssl-dev REQUIRED)
    include_directories(${LIBPOPT_INCLUDE_DIR} ${LIBCURL4_OPENSSL_DEV_INCLUDE_DIR})
    set(LIBS ${LIBS} ${LIBPOPT_DEV_LIBRARY} ${LIBCURL4_OPENSSL_DEV_LIBRARY})

    add_executable(rstools ${MAIN})
    target_link_libraries(rstools ${LIBS})
endif

if (COMPILE_WINDOWS)
    set(CMAKE_SYSTEM_NAME Windows)

    # which compilers to use
    set(CMAKE_CXX_COMPILER i586-mingw32msvc)

    # here is the target environment located
    set(CMAKE_FIND_ROOT_PATH  /usr/i586-mingw32msvc /home/alex/mingw-install)

    # adjust the default behaviour of the FIND_XXX() commands:
    # search headers and libraries in the target environment, search 
    # programs in the host environment
    set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)
    set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
    set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)

    set(LIBS ../libraries/win32/libcurl.dll ../libraries/win32/libeay32.dll ../libraries/win32/libiconv-2.dll ../libraries/win32/libintl-2.dll ../libraries/win32/popt1.dll ../libraries/win32/ssleay32.dll)

    add_executable(rstools.exe ${MAIN})
    target_link_libraries(rstools.exe ${LIBS})
    # copy libraries to same location as built exe here??
endif (COMPILE_WINDOWS)
```

Now that what I'm doing should be pretty clear, here is my question. You can see where my libraries are located. When the program compiles, I need the libraries to copy to the same build folder as the executable (which would be root/build/src), but, as I'm specifying again, I need them to copy over ONLY when the program compiles, and not before.

How can I do this?

(Sorry for the long post, but I needed to make sure my ideas where understood so they come across clearly)

You can see my CMake configuration below..
root/src/cmakelists.txt
```
# Set all variables..
set(MAIN functions.cpp functions.hpp main.cpp parseflags.cpp parseflags.hpp)
set(CMAKE_MODULE_PATH "../cmake/modules/")

# Make sure required dependencies are installed...
find_package(libpopt-dev REQUIRED)
find_package(libcurl4-openssl-dev REQUIRED)
include_directories(${LIBPOPT_INCLUDE_DIR} ${LIBCURL4_OPENSSL_DEV_INCLUDE_DIR})
set(LIBS ${LIBS} ${LIBPOPT_DEV_LIBRARY} ${LIBCURL4_OPENSSL_DEV_LIBRARY})

add_executable(rstools ${MAIN})
target_link_libraries(rstools ${LIBS})
```

root/cmakelists.txt
```
cmake_minimum_required (VERSION 2.8.1)

project(rstools)

add_subdirectory(src)
```

CMakeMingw
```
# the name of the target operating system
SET(CMAKE_SYSTEM_NAME Windows)

# which compilers to use for C and C++
SET(CMAKE_C_COMPILER i586-mingw32msvc-gcc)
SET(CMAKE_CXX_COMPILER i586-mingw32msvc-g++)

# here is the target environment located
SET(CMAKE_FIND_ROOT_PATH  /usr/i586-mingw32msvc /home/alex/mingw-install )

# adjust the default behaviour of the FIND_XXX() commands:
# search headers and libraries in the target environment, search 
# programs in the host environment
set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)
```

---

### Post by James78 on 2010-09-02
Figured it out on my own. Doing this copied the files on BUILD to the executable output directory.
```
ADD_CUSTOM_TARGET(
    "DLL files"
    ALL
    ${CMAKE_COMMAND} -E copy_directory ${LIB_PATH} ${CMAKE_CURRENT_BINARY_DIR}
)
```

---

