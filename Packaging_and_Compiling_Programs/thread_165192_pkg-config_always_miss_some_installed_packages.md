---
title: "pkg-config always miss some installed packages"
date: 2006-04-24
forum: Packaging and Compiling Programs
---

### Post by jeff zhu on 2006-04-24
I use ubuntu just for a month , but this problem puzzle me for several weeks .
 
In many projects , I need to build from source code . 
when the configure script doing its job , it usurally use pkg-config to check for needding  package .

mang times , pkg-config cant find the package .
such as libxml2.
but I look up the dir /usr/lib , i find libxml2.so is there .

using dpkg -L package i can find the installed directory of libxml2 .
but cant find the cooresponding Head file of this library .

why does ubuntu such unfriendly to the developers ?

---

### Post by BlueEagle on 2007-05-06
pkg-config is updated by the xx-dev packages, so even if the lib itself is installed the header/development files might not be. Do a search for the package and check that any coresponding *-dev package is also installed.

Hope that helps.

---

### Post by WW on 2007-05-06
As an example of what BlueEagle said, if you are compiling a program that requires libxml2, then you will need the package **libxml2-dev**.  This package will provide the header files, and the static version of the library.  The package **libxml2** only provides the shared version of the library.

---

