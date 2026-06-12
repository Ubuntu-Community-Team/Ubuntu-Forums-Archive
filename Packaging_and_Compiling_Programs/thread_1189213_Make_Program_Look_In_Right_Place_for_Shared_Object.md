---
title: "Make Program Look In Right Place for Shared Objects"
date: 2009-06-16
forum: Packaging and Compiling Programs
---

### Post by ananswam on 2009-06-16
I am trying to compile a program on another machine on which I do not have the ability to modify environment variables or add packages or do anything outside of my home directory. I want to compile a program that uses a bunch of shared libraries so I put the shared libraries and the source in the same folder, so that I have the following in the same directory:

arnewman.cpp

shlibs (this is a subdirectory containing following files):
libarpack++.so.2.0.0  libarpack.so.2.1  libblas.so.3gf.0  libgfortran.so.2.0.0  liblapack.so.3gf.0

Then I compile using:
g++ -o arnewman arnewman.cpp -I./shlibs/arpack++ ./shlibs/libarpack++.so.2.0.0 ./shlibs/libarpack.so.2.1 ./shlibs/libblas.so.3gf.0 ./shlibs/libgfortran.so.2.0.0 ./shlibs/liblapack.so.3gf.0 -O3

This compile works, but when I run the program I get an error message saying that the program cannot locate libarpack++.so.2 . How do I tell the linker where to look for the shared libraries at runtime. I tried using rpath but had no luck. I also can't do a static link because one of the static libraries has some sort of flaw (I think gfortran) that leads to wrong results at runtime. Also, does this have anything to do with sonames vs actual names? Thanks for the help.

---

