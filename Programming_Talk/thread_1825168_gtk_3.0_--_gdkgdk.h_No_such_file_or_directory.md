---
title: "gtk 3.0 -- gdk/gdk.h: No such file or directory"
date: 2011-08-14
forum: Programming Talk
---

### Post by kr651129 on 2011-08-14
I installed gtk 3.0 because I'd like to get into GUI programming in Ubuntu.  When I try and build my source in NetBeans I get the following output

```
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/kclark/NetBeansProjects/gtk_test'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/gtk_test
make[2]: Entering directory `/home/kclark/NetBeansProjects/gtk_test'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/main.o.d
g++    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.cpp
make[2]: Leaving directory `/home/kclark/NetBeansProjects/gtk_test'
make[1]: Leaving directory `/home/kclark/NetBeansProjects/gtk_test'
In file included from main.cpp:9:0:
/usr/local/include/gtk-3.0/gtk/gtk.h:32:21: fatal error: gdk/gdk.h: No such file or directory
compilation terminated.
make[2]: *** [build/Debug/GNU-Linux-x86/main.o] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2

BUILD FAILED (exit value 2, total time: 325ms)

```

Ideas?

---

### Post by slavik on 2011-08-15
did you install the gtk -dev library?

---

### Post by kr651129 on 2011-08-15
I'm not sure, I thought I did, it is entirely possible that I overlooked it.  I'll have to check after work.

```
sudo apt-get install gtk3-dev
```

is this correct or what would the package be?

---

