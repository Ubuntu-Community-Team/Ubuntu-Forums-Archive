---
title: "Missing stddef.h"
date: 2008-01-21
forum: Packaging and Compiling Programs
---

### Post by tccuser523 on 2008-01-21
stddef.h is said to be missing from /usr/include.  What package do I install to get stddef.h into there?

---

### Post by stroyan on 2008-01-21
You need the libc6-dev package for stddef.h.
You can get that and other useful build packages with 'sudo apt-get install build-essential'.
In general you can look for the package that provides a header file with apt-file- ```
sudo apt-get install apt-file
sudo apt-file update
apt-file search stddef.h
```
You can also install the packages required to build a particular package from source by using 'apt-get build-dep *pkg*'.

---

### Post by ninewives on 2008-03-11
I was having the same problem even though I had build-essentials installed, and then I noticed that build-essentials is satisfied with libc6 instead of libc6-dev.  So, you may have to install libc6-dev even if you have build-essentials.  Anyway, this was immensely helpful, thanks!  No more mystery impossible-to-find files!

---

### Post by earthforce_1 on 2009-11-18
I am running into the same problem - I upgraded from 8.04->8.10->9.04->9.10

and have libc6 and libc6-dev and linux headers installed:

sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~/bin/test$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

Compiling a simple socket program yields:
gcc client.c
In file included from client.c:1:
/usr/include/stdio.h:34:21: error: stddef.h: No such file or directory
In file included from /usr/include/stdio.h:75,
                 from client.c:1:
/usr/include/libio.h:53:21: error: stdarg.h: No such file or directory
In file included from /usr/include/stdio.h:75,
                 from client.c:1:

The first few lines of client.c are:
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <string.h>

---

