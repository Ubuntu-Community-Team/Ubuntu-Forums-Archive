---
title: "Compiling errors and using Cmake Set Policy"
date: 2010-01-23
forum: Packaging and Compiling Programs
---

### Post by fbonniwell on 2010-01-23
Hello,

I'm new to the world of compiling in Linux and I thought this is the best place to ask questions! :D

I discovered the project I'm trying to compile has two **add_executable** targets that share the same name in two different folders. Both of these **add_executable** targets are in two separate CMakeList.txt files. 

for example

/home/mdtom//icap/core/CMakeList.txt

/home/mdtom//icap/gui/CMakeList.txt


When compiling in Ubuntu jaunty 9.04 with cmake 2.6, it has the new cmake_policy parameters to help programmers. 

The  --help-policy CMP0002 suggested I use the OUTPUT_NAME property but I get entirely new errors when trying the following"


```
 

#/home/programmer/toolb/icap/core/CMakeList.txt

ADD_EXECUTABLE(test_f1 test.cpp)
SET_TARGET_PROPERTIES(test_f1 OUTPUT_NAME test)

 #/home/programmer/toolb/icap/gui/CMakeList.txt

ADD_EXECUTABLE(test_f2 main.cpp)
SET_TARGET_PROPERTIES(test_f2 OUTPUT_NAME test)
```Is there a better approach to eliminating the error or am I on the right path?
I'm open to any suggestions.

Below is the output from the cmake.

Thanks,

F


mdtom@ubuntu:~/icap/build$ cmake ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'ImageMagick++'
--   found ImageMagick++, version 6.4.5
-- checking for module 'gtkmm-2.4>=2.10'
--   found gtkmm-2.4, version 2.16.0
-- checking for module 'cairomm-1.0'
--   found cairomm-1.0, version 1.6.4
-- checking for module 'gthread-2.0'
--   found gthread-2.0, version 2.20.1
CMake Warning (dev) at gui/CMakeLists.txt:12 (add_executable):
  Policy CMP0002 is not set: Logical target names must be globally unique.
  Run "cmake --help-policy CMP0002" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring done
CMake Warning (dev) at core/CMakeLists.txt:25 (add_executable):
  Policy CMP0003 should be set before this line.  Add code such as

    if(COMMAND cmake_policy)
      cmake_policy(SET CMP0003 NEW)
    endif(COMMAND cmake_policy)

  as early as possible but after the most recent call to
  cmake_minimum_required or cmake_policy(VERSION).  This warning appears
  because target "test" links to some libraries for which the linker must
  search:

    Magick++, MagickCore

  and other libraries with known full path:

/home/mdtom//icap/core/libcore.a
/home/mdtom//icap/build/ext/newmat/libnewmat.a

  CMake is adding directories in the second list to the linker search path in
  case they are needed to find libraries from the first list (for backwards
  compatibility with CMake 2.4).  Set policy CMP0003 to OLD or NEW to enable
  or disable this behavior explicitly.  Run "cmake --help-policy CMP0003" for
  more information.
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Generating done
-- Build files have been written to: /home/mdtom/icap/build
mdtom@ubuntu:~/icap/build$

---

