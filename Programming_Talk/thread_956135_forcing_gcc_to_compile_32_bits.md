---
title: "forcing gcc to compile 32 bits"
date: 2008-10-22
forum: Programming Talk
---

### Post by billvb on 2008-10-22
Hello Everyone,

Right now i'm using a 64-bit system (x86_64).  I have an application I wrote for a 32 bit system (and fails if compiled for 64 bits).  Therefore, I want to force gcc to compile for a 32 bit environment.  This will go in a Makefile and will be distributed, so I want it to force 32 bits for any system.

However, the flags detailed in the man page for gcc (i.e., -m32 m32-bit -milp32 -mgp32 etc) either do not work (unrecognized command line option) or gives a compile error in some libraries.

Any ideas?

Thanks.

---

### Post by Ferrat on 2008-10-22
have you installed all the 32-bit libs that you need ect? 
very basic I know but something that's easy to miss

---

### Post by dwhitney67 on 2008-10-22
Use the -m32 option with gcc.

---

