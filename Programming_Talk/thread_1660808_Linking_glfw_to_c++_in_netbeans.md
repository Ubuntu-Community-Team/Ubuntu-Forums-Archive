---
title: "Linking glfw to c++ in netbeans"
date: 2011-01-05
forum: Programming Talk
---

### Post by farisk on 2011-01-05
Hey, Im a java programmer whose trying to adopt to c++. Id like to know how I can link the glfw library so I can use it in my application in c++. I've Installed  libglfw-dev and libglfw2 from using aptitude but have no idea where it is or how to use it in netbeans.Help is much appreciated thanks.

---

### Post by dwhitney67 on 2011-01-06
g++, which is the typical C++ compiler/linker used under Linux, provides the following options:  -L and -l

The former (-L) is used to specify the location of the library you wish to link with.  If the library you wish to use is located within an area that has been cached by *ldconfig*, then you do not need to specify this option, for it will be found automatically.

The latter option (-l) is used to specify the library you wish to link with.  The *lib* portion of the library name, nor the file extension, are specified with this option.  Thus if you wish to link with libglfw.so, you would specify "-lglfw".

I would recommend that you learn to build your project from the command line using these options; something like the following (which may be incomplete):
```

g++ -Wall -g MySourceFile.cpp -lglfw

```
Once you have mastered how to do this, and develop a certain level of appreciation as to how it works, then I would suggest that you tinker with your IDE (whether it be NetBeans, CodeBlocks, or whatever) to accomplish the same.  IMO, using an IDE without knowledge of the fundamentals is shear foolishness.

P.S.  Some development packages offer the ability to use 'pkg-config' to obtain compiler and linker options for building your project.  You should reference the documentation for GLFW to see if it offers such.

Compiler options:   pkg-config --cflags <package name>
Linker options:   pkg-config --libs <package name>

or all together:   pkg-config --cflags --libs <package name>

---

