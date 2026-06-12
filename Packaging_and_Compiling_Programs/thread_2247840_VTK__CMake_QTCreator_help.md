---
title: "VTK  CMake QTCreator help"
date: 2014-10-10
forum: Packaging and Compiling Programs
---

### Post by cp43tcW on 2014-10-10
Hello, I am new to VTK and CMake and I am trying to open a program written in C++ in QTCreator. When I attempt run CMake I get the following error:

```

CMake Error at /usr/share/cmake-2.8/Modules/FindVTK.cmake:135 (MESSAGE):
VTK not found.  Set the VTK_DIR cmake cache entry to the directory
containing VTKConfig.cmake.  This is either the root of the build tree, or
PREFIX/lib/vtk for an installation.  For VTK 4.0, this is the location of
UseVTK.cmake.  This is either the root of the build tree or
PREFIX/include/vtk for an installation.
Call Stack (most recent call first):
CMakeLists.txt:4 (FIND_PACKAGE)

```

I'm pretty inexperienced with Linux and I don't really understand what the error means or how to fix it. Can someone please help me out? Where should the files I need to modify be located and what do I need to change?

---

