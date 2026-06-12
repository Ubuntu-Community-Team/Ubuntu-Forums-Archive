---
title: "C++"
date: 2006-12-30
forum: Programming Talk
---

### Post by fredster001 on 2006-12-30
Hi everyone,

I have recently installed ubuntu (the latest version) and like it.

Which is the best available compiler for C++ ??
Where do i get it?

Thanks very much

fredster001

---

### Post by neowolf on 2006-12-30
The 'G++' C++ compiler is part of GCC, the GNU Compiler Collection.
To get everything needed to compile languages supported by GCC and kernel drivers install the build-essential meta-package.
GCC supports C, C++, Objective-C, Fortran, Java, and Ada.


sudo apt-get install build-essential;
vim test.cpp;
g++ test.cpp -o test;
./test

---

