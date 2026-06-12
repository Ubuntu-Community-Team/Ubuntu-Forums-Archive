---
title: "Error while compiling Tibia server (CMAKE ERROR)"
date: 2013-07-16
forum: Packaging and Compiling Programs
---

### Post by ph4sm4 on 2013-07-16
Hello Ubuntu forums! This is my first thread here but I've been using ubuntu for a very long time.

So latley I've been trying to setup a tibia server on ubuntu and everything worked smoothley until I did the command > sudo cmake .. when I do so I get this error:
> -- BUILD TYPE: RelWithDebInfo
CMake Error at /usr/share/cmake-2.8/Modules/FindBoost.cmake:1202 (message):
  Unable to find the requested Boost libraries.

  Unable to find the Boost header files.  Please set BOOST_ROOT to the root
  directory containing Boost or BOOST_INCLUDEDIR to the directory containing
  Boost's headers.
Call Stack (most recent call first):
  CMakeLists.txt:101 (FIND_PACKAGE)


CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:91 (MESSAGE):
  Could NOT find GMP (missing: GMP_LIBRARY GMP_INCLUDE_DIR)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:252 (_FPHSA_FAILURE_MESSAGE)
  cmake/FindGMP.cmake:15 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:111 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!

It looks like it couldn't find some GMP package, I've been trying to find sollutions by googleing the error etc but after 3 hours I still didn't have an sullotion so hope any one of you do!
Thank you! (Im running ubuntu 12)
- Phasma

---

