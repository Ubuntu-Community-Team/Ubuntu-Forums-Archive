---
title: "Compiling 32-bit code with gcc failure"
date: 2016-12-26
forum: Packaging and Compiling Programs
---

### Post by Edward_Diener on 2016-12-26
If I compile 64-bit code using gcc, with the -m64 switch, everything succeeds. If I compile 32-bit code using gcc, with the -m32 switch, I receive the error:

/usr/include/c++/5/cstdio:41:28: fatal error: bits/c++config.h: No such file or directory
compilation terminated.

What package do I need in order to compile 32-bit code with gcc ?

---

