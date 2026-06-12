---
title: "Got error when compiling a program with gtest using cmake"
date: 2018-01-08
forum: Packaging and Compiling Programs
---

### Post by dtf2 on 2018-01-08
Hello.
My system - xubuntu 17.10

I am writing a program with cmake build system and I want to use googletest for unit testing.

But when I am trying to
```
find_package(GTest REQUIRED)
```
in CMakeLists.txt I am getting

>   Running "/usr/bin/cmake -E server --pipe=/tmp/cmake-uPJNmn/socket --experimental" &#1074; /home/dtf/src/TestStock1/build.

 CMake Error at /usr/share/cmake-3.9/Modules/FindPackageHandleStandardArgs.cmake:137 (message):
   Could NOT find GTest (missing: GTEST_LIBRARY GTEST_MAIN_LIBRARY)
 Call Stack (most recent call first):
   /usr/share/cmake-3.9/Modules/FindPackageHandleStandardArgs.cmake:377 (_FPHSA_FAILURE_MESSAGE)
   /usr/share/cmake-3.9/Modules/FindGTest.cmake:146 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
   CMakeLists.txt:10 (find_package)
 

 

 Configuring incomplete, errors occurred!
 See also "/home/dtf/src/TestStock1/build/CMakeFiles/CMakeOutput.log".



Package googletest in installed.

What else I forgot to do?

---

### Post by sisco311 on 2018-01-08
Hi, dtf2!

Is the gtest development package installed on your system?
```
sudo apt install libgtest-dev
```

---

### Post by dtf2 on 2018-01-09
> Is the gtest development package installed on your system?
Yes, it is.

However, description says that the package is deprecated and everyone should use googletest package instead.
I tried with googletest alone and with googletest and libgtest-dev installen simultaneously.
No success.

---

### Post by dtf2 on 2018-01-13
Well, decided to find the libraries myself and.. I cant oO.

It seems that *googletest* package only contains only sources, not binary libraries.
That's why cmake cannot found them.

So it seems that the right question is: how to actually set up google test on ubuntu 17.10?

Or maybe I missed something and the package does have libraries inside.
Could anyone check?

---

