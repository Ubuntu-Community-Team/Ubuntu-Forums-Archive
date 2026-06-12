---
title: "Building firefox on 9.04 64bit - configure can't find gtk+-2.0"
date: 2009-07-06
forum: Packaging and Compiling Programs
---

### Post by thaidog on 2009-07-06
I am new to developing on Ubuntu and I am trying to build firefox but the configure dies with:

checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 glib-2.0 gobject-2.0 gdk-x11-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gtk+-unix-print-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-unix-print-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-unix-print-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gobject-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gobject-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gobject-2.0' found Package gdk-x11-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdk-x11-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gdk-x11-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 glib-2.0 gobject-2.0 gdk-x11-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
*** Fix above errors and then restart with "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/root/test/mozilla-1.9.1'
make: *** [/root/test/mozilla-1.9.1/../mozilla-build/Makefile] Error 2
root@tylerm-laptop:~/test/mozilla-1.9.1#
################################################## ##############

Since it's ubuntu I'm sure I have gtk+-2.0.
Any ideas?

ubuntu 9.04 64bit

---

### Post by badeagle on 2009-07-09
looks like you need dev packages

sudo aptitude install build-essential
sudo aptitude install libgtk2.0-dev

you're going to have to find the packages that it complains it needs but with -dev at the end :P and install them

---

