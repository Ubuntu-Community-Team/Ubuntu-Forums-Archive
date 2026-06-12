---
title: "Learn CMake (together)"
date: 2009-04-02
forum: Packaging and Compiling Programs
---

### Post by pocketchange on 2009-04-02
I'm currently trying to learn cmake.  I only have a moderate knowledge of autotools, but so far I've found cmake so much simpler.  I've gotten so excited about cmake that I'm trying to write up a brief post for porting an application to cmake.  Having only been using it for one day, I figured I could use some help.  The package I'm trying to change from autotools to cmake is "dsh".  I picked it arbitrarily because it's simple with a few extras thrown in (locales, man pages for different locales, a few configure features, has tests, etc).

At the end of this post, I'd like to have something that works so I can send a patch upstream.  Here's what I have so far:

**Get the source and unpack it.**
```
wget http://www.netfort.gr.jp/~dancer/software/downloads/dsh-0.25.10.tar.gz
tar xzvf dsh-0.25.10.tar.gz
mv dsh-0.25.10 dsh-0.25.10.orig
tar xzvf dsh-0.25.10.tar.gz
cd dsh-0.25.10
```

**Clean up the autotools mess**
```
rm -rf depcomp configure compile autogen.sh \
config.sub config.rpath config.guess aclocal.m4 \
missing Makefile.am mkinstalldirs Makefile.in \
m4 configure.ac install-sh
```

**Edit the CMakeLists.txt file**
```
vim CMakeLists.txt
```

and paste in the following configuration:

```
# Project Information
project(dsh)
cmake_minimum_required(VERSION 2.6)
set(PACKAGE_NAME \"dsh\")
set(PACKAGE_VERSION \"0.25.10\")
include(FindGettext)

# Variables
set(dsh_SRC dsh.c  linkedlist.c  parameter.c)

# Find what's needed to build the package
find_package(Gettext)

# Building
add_definitions(-ansi -pedantic -Wall)
add_definitions(-DPACKAGE_NAME=${PACKAGE_NAME} -DVERSION=${PACKAGE_VERSION})
add_executable(dsh ${dsh_SRC})

# Installation
install(TARGETS dsh DESTINATION bin)

# Report
message(STATUS GETTEXT_FOUND = ${GETTEXT_FOUND})
```


**Start the out-of-source build**
```
mkdir build
cd build
cmake ..
```

Now, this will fail.  I get errors about PACKAGE and getline.  Anyone care to jump in and help me through this?  When I'm all done, I'll write it up more coherently so others can learn too.  

Here is what I know is missing from my cmake implementation thus far:
[LIST]
[*]locale support
[*]installing man pages
[*]config.h support
[*]configure options need porting
[/LIST]

--
Shane

---

### Post by pocketchange on 2009-04-02
I modified my CMakeLists.txt to force out-of-source builds (just to keep things neat).  Here's my new version:

```
# Project Information
project(dsh)
cmake_minimum_required(VERSION 2.6)
set(PACKAGE_NAME \"dsh\")
set(PACKAGE_VERSION \"0.25.10\")
include(FindGettext)

if( CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR AND NOT MSVC_IDE )
  message(FATAL_ERROR "In-source builds are not allowed.
Please create a directory and run cmake from there, passing the path
to this source directory as the last argument.
This process created the file `CMakeCache.txt' and the directory `CMakeFiles'.
Please delete them.")
endif()

# Variables
set(dsh_SRC dsh.c  linkedlist.c  parameter.c)

# Find what's needed to build the package
find_package(Gettext)

# Building
add_definitions(-ansi -pedantic -Wall)
add_definitions(-DPACKAGE_NAME=${PACKAGE_NAME} -DVERSION=${PACKAGE_VERSION})
add_executable(dsh ${dsh_SRC})

# Installation
install(TARGETS dsh DESTINATION bin)

# Report
message(STATUS GETTEXT_FOUND = ${GETTEXT_FOUND})

```

I also tried adding configure_file support by adding the line:
```
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/config.h.in ${MAKE_CURRENT_BINARY_DIR}/config.h)
```

but I got this error:

```
CMake Error: Could not open file for write in copy operation /config.h.tmp
CMake Error: : System Error: Permission denied
CMake Error at CMakeLists.txt:22 (configure_file):
  configure_file Problem configuring file
```

---

### Post by pocketchange on 2009-04-03
I've gotten a little further.  I solved the config.h problem because I mis-typed MAKE_* instead of CMAKE_*.  I added checks for the headers in dsh.c

Here's my newest rev:

```
# Project Information
project(dsh)
cmake_minimum_required(VERSION 2.6)
set(PACKAGE_NAME \"dsh\")
set(PACKAGE_VERSION \"0.25.10\")
include(FindGettext)
include(CheckIncludeFiles)

if( CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR AND NOT MSVC_IDE )
  message(FATAL_ERROR "In-source builds are not allowed.         
Please create a directory and run cmake from there, passing the path
to this source directory as the last argument.                      
This process created the file `CMakeCache.txt' and the directory `CMakeFiles'.
Please delete them.")                                                         
endif()    

# Variables
set(dsh_SRC dsh.c  linkedlist.c  parameter.c)

# Find what's needed to build the package
find_package(Gettext)
check_include_files("sys/types.h" HAVE_SYS_TYPES_H)
check_include_files("sys/wait.h" HAVE_SYS_WAIT_H)
check_include_files("sys/stat.h" HAVE_SYS_STAT_H)
check_include_files("stdio.h" HAVE_STDIO_H)
check_include_files("stdlib.h" HAVE_STDLIB_H)
check_include_files("string.h" HAVE_STRING_H)
check_include_files("unistd.h" HAVE_UNISTD_H)
check_include_files("fcntl.h" HAVE_FCNTL_H)
check_include_files("locale.h" HAVE_LOCALE_H)
check_include_files("assert.h" HAVE_ASSERT_H)
check_include_files("errno.h" HAVE_ERRNO_H)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/config.h.in ${CMAKE_CURRENT_BINARY_DIR}/config.h)

# Building
add_definitions(-ansi -pedantic -Wall)
add_definitions(-DPACKAGE=${PACKAGE_NAME} -DVERSION=${PACKAGE_VERSION})
add_executable(dsh ${dsh_SRC})

# Installation
install(TARGETS dsh DESTINATION bin)

# Report
message(STATUS GETTEXT_FOUND = ${GETTEXT_FOUND})

```

---

### Post by pocketchange on 2009-04-03
**CACHE setting for VARIABLES**
With this, I used the CACHE feature because everything is typically installed into the CMAKE_INSTALL_PREFIX, but obviously this can't include the stuff in /etc, so we want that to be set independently

```
set(DSHCONFDIR ${SYSCONFDIR} CACHE PATH "The configuration directory")
```

**Reporting and Troubleshooting**
I added a section at the end of my file that handles reporting so I can visually see what variables are set to.  This is handy because variables in cmake don't have to be initialized so if you accidentally type the wrong name (see MAKE vs CMAKE spelling error above) then it continues on but just goes with a blank value.  Here's how to generate a quick report at the end of a build:

```
# Report
message(STATUS "----- GETTEXT_FOUND    : ${GETTEXT_FOUND}")
message(STATUS "----- LOCALEDIR        : ${LOCALEDIR}")
message(STATUS "----- DSH_COMMANDLINE  : ${DSH_COMMANDLINE}")
message(STATUS "----- DSHCONFDIR       : ${DSHCONFDIR}")

```

**Out-of-Source Builds**
One thing I noticed is that if I do an out-of-source build, the config.h ends up in my build directory which, in reality, could be named anything.  I have to somehow include the config.h so I added this line to my CMakeLists.txt:

```
add_definitions(-ansi -pedantic -Wall -I${CMAKE_CURRENT_BINARY_DIR})

```

The -I should include the build directory so the build system can find config.h.  We could have pointed config.h to the source directory, but that would have defeated the idea of out-of-source builds.


**Things I'm still trying to get to work**
Compile still doesn't complete entirely because of getline stuff
I haven't tried to get tests to work at all, so that's still a TODO

---

### Post by pocketchange on 2009-04-03
**Forcing out-of-source builds**
This is code forcing out-of-source builds.  Credit goes to the llvm project where I got this.  I don't know if there's any way to keep it from getting as far as creating the CMakeCache.txt and CMakeFiles before failing.

```
if( CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR AND NOT MSVC_IDE )
  message(FATAL_ERROR "In-source builds are not allowed.
Please create a directory and run cmake from there, passing the path
to this source directory as the last argument.
This process created the file `CMakeCache.txt' and the directory `CMakeFiles'.
Please delete them.")
endif()

```

**Config.h files**
This is in the CMakeLists.txt file:

```
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/config.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/config.h)
```

This is what the config.h.cmake file should look like:
```
#cmakedefine HAVE_SYS_WAIT_H

/* Define to 1 if you have the <unistd.h> header file. */
#cmakedefine HAVE_UNISTD_H

/* Name of package */
#cmakedefine PACKAGE "${PACKAGE_NAME}"

/* Define to the address where bug reports for this package should be sent. */
#cmakedefine PACKAGE_BUGREPORT

/* Define to the full name of this package. */
#cmakedefine PACKAGE_NAME "${PACKAGE_NAME}"

/* Define to the full name and version of this package. */
#cmakedefine PACKAGE_STRING

/* Define to the one symbol short name of this package. */
#cmakedefine PACKAGE_TARNAME

/* Define to the version of this package. */
#cmakedefine PACKAGE_VERSION "${PACKAGE_VERSION}"

/* If setnetgrent returns void like AIX systems, set this */
#cmakedefine SETNETGRENT_RETURNS_VOID

/* Define to 1 if you have the ANSI C header files. */
#cmakedefine STDC_HEADERS

/* Version number of package */
#cmakedefine VERSION "${PACKAGE_VERSION}"

```

Notice that VERSION and PACKAGE are quoted.  This was to prevent build errors when this was used in printf.

---

