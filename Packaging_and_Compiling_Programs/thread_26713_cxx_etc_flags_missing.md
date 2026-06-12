---
title: "cxx etc flags missing?"
date: 2005-04-13
forum: Packaging and Compiling Programs
---

### Post by Luca Picello on 2005-04-13
Hi all,
I use cmake ([www.cmake.org](www.cmake.org)) program to generate makefiles.
I have new and strange error message :

-- Check for working C compiler: CMAKE_C_COMPILER_FULLPATH-NOTFOUND

It seems to be referred to a note in the README:

Strange compile errors on Unix. Make sure that you specify the environment variables CXX and CC prior to running CMake.

doing "#echo $CXX" and "#echo $CC" I have nothing set.

I installed gcc and g++ and lots of packages hoping they autoconfigure those environment variables but nothing happens.

Any idea?
thanks

Luca

---

