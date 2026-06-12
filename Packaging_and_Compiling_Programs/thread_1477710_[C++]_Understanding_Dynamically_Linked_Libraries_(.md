---
title: "[C++] Understanding Dynamically Linked Libraries (Win &amp; Lin)"
date: 2010-05-09
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-05-09
From what I understand about shared (dynamically linked) libraries on Windows:  First an executable will search its own directory for the library.  If it is not found, it will look in PATH.  

Now I have just learned how to create and link to shared libraries on Linux using the GNU C++ compiler, and this is what I have experienced:  I have been able to link to a shared library in one of three ways.  First by absolute path, the library has to be in the specified path no matter what, or the executable will fail to link to it:
```
g++ test.cpp mylib.h /home/user/Programming/test/libmylib.so -o test
```Next, linking to the library in the executables directory.  The library must be in the same directory as the executable:
```
g++ test.cpp mylib.h ./libmylib.so -o test
```
And last, linking to the library which must be placed somewhere in PATH:
```
g++ test.cpp mylib.h libmylib.so -o test
```

What I want to understand is do I have to choose between one of these methods?  Or can I combine the executable dir & PATH methods and place my lib in either executable dir or PATH?  I know that I can add the executables dir to PATH, but I was wondering if this could be done without adjusting environment variables.

---

