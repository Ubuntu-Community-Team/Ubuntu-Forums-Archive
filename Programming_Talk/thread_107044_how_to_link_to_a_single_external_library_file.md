---
title: "how to link to a single external library file?"
date: 2005-12-22
forum: Programming Talk
---

### Post by rvbhute on 2005-12-22
I want to link to Dislin <www.dislin.de> library file. There are two files available - "dislin-9.0.a" and "dislin-9.0.so" ;both are in the same directory as the source file. Also, the "dislin.h" which is included from the source file, is in the same directory.

In Mingw based Dev-C++ IDE, I simply added the .a file in the linker parameters. In Linux, at the command line, How do I go about? Which file do I use and how do I include it?

---

### Post by thumper on 2005-12-22
I think (not tested) that to link with the static library put dislin-9.0.a on the command line for g++.

To link against the shared lib, I am fairly sure that there needs to be libdislin-9.0.so defined somewhere.

Perhaps there is a symlink for libdislin.so -> dislin-9.0.so

If this is the case then you use -ldislin on the command line for building the executable.  Note that it is a lowercase L not an uppercase i.

---

### Post by rvbhute on 2005-12-22
Yes, the second way worked. I even tried installing (ie extracting and setting shell variables) but it seems Dislin has some conflict with Ubuntu. I've given it up till I get time to poke around, right now, I need to make sure that the code works well atleast on one platform :smile: .

---

