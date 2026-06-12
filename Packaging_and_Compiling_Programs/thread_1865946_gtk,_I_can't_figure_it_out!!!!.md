---
title: "gtk, I can't figure it out!!!!"
date: 2011-10-20
forum: Packaging and Compiling Programs
---

### Post by kr651129 on 2011-10-20
I'm trying to use gtk, I've built it from source and even did an apt-get and no matter what I do this is my output from netbeans.  I keep googleing it but can't seem to come up with anything.

```
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .clean-conf
make[1]: Entering directory `/home/kclark/NetBeansProjects/Deb Creator'
rm -f -r build/Debug
rm -f dist/Debug/GNU-Linux-x86/deb_creator
make[1]: Leaving directory `/home/kclark/NetBeansProjects/Deb Creator'

CLEAN SUCCESSFUL (total time: 63ms)
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/kclark/NetBeansProjects/Deb Creator'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/deb_creator
make[2]: Entering directory `/home/kclark/NetBeansProjects/Deb Creator'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/main.o.d
g++    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.cpp
In file included from main.cpp:9:0:
/usr/include/gtk-2.0/gtk/gtk.h:32:21: fatal error: gdk/gdk.h: No such file or directory
compilation terminated.
make[2]: *** [build/Debug/GNU-Linux-x86/main.o] Error 1
make[2]: Leaving directory `/home/kclark/NetBeansProjects/Deb Creator'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/kclark/NetBeansProjects/Deb Creator'
make: *** [.build-impl] Error 2

BUILD FAILED (exit value 2, total time: 331ms)
 
```

---

### Post by kr651129 on 2011-10-21
bump

---

### Post by killswitchguy on 2011-10-22
try this [http://live.gnome.org/DeveloperTools/Installation/Ubuntu](http://live.gnome.org/DeveloperTools/Installation/Ubuntu) just used sudo apt-get install to all the files mentioned. I hope it helps, i am having problems with Glade and i suggest you don't use it at all.

---

