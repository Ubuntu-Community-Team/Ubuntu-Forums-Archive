---
title: "compiling boost with monodevelop"
date: 2012-03-01
forum: Packaging and Compiling Programs
---

### Post by jebsector on 2012-03-01
I keep getting errors like the following when trying to compile boost through monodevelop.  I have a makefile that works fine, but since monodevelop works on other systems and my makefile doesn't, I was wanting to work with boost through monodevelop..

The errors I get are like the following:

/usr/include/boost/system/error_code.hpp(0,0): Error: undefined reference to `boost (Data Carbon)

This is what the command is doing before it generates these errors:

g++ -o "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/Data Carbon" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/main.o" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/IdxInt32_B.o" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/LH_Int32.o" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/spooky.o" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/testIdx.o" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/testInt32Idx.o" "/media/8B96-EEF6/projects/Data Carbon/Data Carbon/bin/Debug/TestInt32_LH_Idx.o" -Lboost_system -Llibboost_filesystem

Any help is always appreciated..

the '-L' is coming from compiler flags set up in monodevelop, and I have pointed the include path to /usr/include/boost'.

---

### Post by MadCow108 on 2012-03-02
```
-Lboost_system -Llibboost_filesystem 
```
looks wrong, you want
```
-lboost_system -lboost_filesystem
```
note the missing lib

you have probably added the libraries under the *Paths* instead of *Libraries* in the project options-> build -> code generation

---

### Post by jebsector on 2012-03-02
Ah - that worked.  I switched /usr/includes/boost to a library path instead of an include path, and switched over to what you had for the inclusion flags for the system and filesystem libraries.  

Compiles fine now.  Thanks,

---

