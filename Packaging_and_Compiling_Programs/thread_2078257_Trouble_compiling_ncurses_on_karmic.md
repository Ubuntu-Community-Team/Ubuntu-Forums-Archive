---
title: "Trouble compiling ncurses on karmic"
date: 2012-10-30
forum: Packaging and Compiling Programs
---

### Post by JaySeeJC on 2012-10-30
Having trouble compiling ncurses 5.7 on karmic. 
```
cd ../objects;   -I../c++ -I../include -I. -DHAVE_CONFIG_H  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64  -DNDEBUG -I. -I../include -I/home/champjon/.usr/include/ncurses  -c ../c++/cursesf.cc
/bin/sh: -I../c++: not found
make: *** [../objects/cursesf.o] Error 127

```
I don't have root access on this machine so i'm trying to trying to compile some useful utilities for myself. Many of them require ncurses, but i'm getting the above error.

---

### Post by itcotbtoemik on 2012-10-31
> **JaySeeJC said:**
> Having trouble compiling ncurses 5.7 on karmic. 
[CODE]cd ../objects;   -I../c++ -I../include -I. -DHAVE_CONFIG_H  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64  -DNDEBUG -I. -I../include -I/home/champjon/.usr/include/ncurses  -c ../c++/cursesf.cc
/bin/sh: -I../c++: not found
make: *** [../objects/cursesf.o] Error 127


When running the configure script, no C++ compiler (including g++) was found.
There is a configure option --without-cxx

If you are compiling with your own libraries, it also helps to use the --enable-rpath option (for shared libraries).

These are described in the top-level INSTALLATION file in ncurses' sources.

---

