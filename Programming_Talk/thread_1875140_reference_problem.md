---
title: "reference problem???"
date: 2011-11-04
forum: Programming Talk
---

### Post by liquidmonkey on 2011-11-04
i'm trying to do a tutorial with PCL and have the code ready to go but when i try and make it, its not working.

in fact, its only the includes that are giving me problems and i often get confused by these :(

includes from myPCL.cpp

#include <iostream>
#include <pcl/io/pcd_io.h>
#include <pcl/point_types.h>


CMakeLists.txt file

cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(myPCL)
find_package(PCL 1.2 REQUIRED)
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})
add_executable(myPCL myPCL.cpp)
target_link_libraries(pcd_write ${PCL_LIBRARIES})


when i type 'make myPCL' i get...
first-pcl.cpp:2:27: fatal error: pcl/io/pcd_io.h: No such file or directory

now the actual PCL files are here...
~/usr/local/include/pcl-1.3/pcl

and my program file is here...
~/Dropbox/01/test

is it the includes that need to be changed or the CMakeLists file stuff?
as i said, i get so confused with this stuff, please be gentle.
thanks!

---

### Post by karlson on 2011-11-04
Next time use please use code tags.

when you compile if you are using a relative path for the header files you have to provide a compiler with the additional directories for header search like:

```

g++ -I/home/user/usr/local/include/pcl-1.3 <blah blah blah>

```

---

### Post by liquidmonkey on 2011-11-04
and what if i'm using a make file?
just put that line in the make file?

---

### Post by karlson on 2011-11-04
> **liquidmonkey said:**
> and what if i'm using a make file?
just put that line in the make file?

You need to make sure that in the line that defines compilation of the file -I is included.

There are great many ways to make sure this happens.

INCLUDES = -I<blah>

gcc $(INCLUDES) <blah blah blah> 

is just one of them.

---

