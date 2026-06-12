---
title: "Need help with cmake"
date: 2008-05-16
forum: Packaging and Compiling Programs
---

### Post by kinuser on 2008-05-16
I am pretty new to linux (less then a week) and trying to figure how to use the cmake complier to load this program.  I already did the

sudo apt-get install cmake

but now when I try to run it this message comes up, anyone know how to help me at all??

:~/Desktop/ivphelm/src$ cmake ./
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error: The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a simple test program.
It fails with the following output:
 

CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done


if I should post this in another place I could do that too, wasn't sure if this is the right place or not.  Any help would be great!  Thanks

---

### Post by kinuser on 2008-05-16
Never mind, I actually got it, just had to install the GNU C++ and C compilers.

---

### Post by rockinrobstar on 2008-06-14
specifically you need to do:
apt-get install g++
(the metapackage - the specific version packages don't seem to work)

---

