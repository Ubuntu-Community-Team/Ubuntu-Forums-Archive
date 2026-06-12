---
title: "KDevelop Problem"
date: 2007-12-13
forum: Programming Talk
---

### Post by snickers295 on 2007-12-13
hi i just installed kdevelop and every time i try to compile something i get this:
```
cd '/home/snickers295/Test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/snickers295/Test/debug' && cd '/home/snickers295/Test/debug' && CXXFLAGS="-O0 -g3" "/home/snickers295/Test/configure" --enable-debug=full && cd '/home/snickers295/Test/debug/src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k test.lo
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

```
i have installed autoconf and automake but this still happens.
i am using kubuntu 7.10 and kdevelop 3

---

### Post by luisromangz on 2007-12-14
It complains about an specific version of autoconf, you should check if you have it installed in your system, as there are multiple versions in the repositories.

---

### Post by snickers295 on 2007-12-14
```
autoconf (GNU Autoconf) 2.53
Written by David J. MacKenzie and Akim Demaille.

Copyright 2002 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
snickers295@mdsmiths:~/Test$

```
the output when i try to compile
```
cd '/home/snickers295/Test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && cd '/home/snickers295/Test/debug' && CXXFLAGS="-O0 -g3" "/home/snickers295/Test/configure" --enable-debug=full && cd '/home/snickers295/Test/debug/src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k test.lo
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

```

---

### Post by llangwm on 2007-12-24
try ... 
sudo apt-get install libtool

and ... 
sudo apt-get install automake

then try again - oh, and happy christmas! :)

---

