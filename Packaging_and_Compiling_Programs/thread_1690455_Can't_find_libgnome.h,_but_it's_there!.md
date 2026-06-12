---
title: "Can't find libgnome.h, but it's there!"
date: 2011-02-18
forum: Packaging and Compiling Programs
---

### Post by captnemo on 2011-02-18
Development under Gtk has been going on fine using the following flags in my makefile

CFLAGS  = -Wall -lao `pkg-config --cflags gtk+-2.0 gmodule-2.0`
LDFLAGS = -lao `pkg-config --libs gtk+-2.0 gmodule-2.0`

Today I decided to use some functions from libgnome.  So I added the following include:

#include <libgnome/libgnome.h>

And the compiler complains that it cannot find libgnome.h

So I go look in /usr/include/libgnome-2.0/libgnome and libgnome.h is there.

So then I checked pkg-config:                

pkg-config --list-all | grep gnome

Failed to open '/usr/lib/pkgconfig/gst-python-0.10.pc': No such file or directory
gnome-screensaver              gnome-screensaver - gnome screensaver
libgnome-2.0                   libgnome - libgnome
gnome-doc-utils                gnome-doc-utils - GNOME Documentation Utilities
gnome-vfs-2.0                  gnome-vfs - The GNOME virtual file-system libraries
gnome-vfs-module-2.0           gnome-vfs-module - The GNOME virtual file-system module include info
gnome-icon-theme               gnome-icon-theme - A collection of icons used as the basis for GNOME themes
gnome-mime-data-2.0            gnome-mime-data - Base set of file types and applications for GNOME
gnome-system-tools             gst - Gnome System Tools


It's there.  So I have no clue why the compiler can't find the header file.

---

### Post by captnemo on 2011-02-18
Additional note:  I just installed the enormous gnome-devel package using Synaptic and same problem.  The compiler can't find libgnome.h

---

### Post by SevenMachines on 2011-02-18
You should be adding libgnome-2.0 to the pkg-config command, you havent done that in the cflags you mention above
Are you adding libgnome-2.0 to the pkg-config line?
```
$ apt-file search libgnome.h|grep include
libgnome2-dev: /usr/include/libgnome-2.0/libgnome/libgnome.h
```
So thats what contains the header
```
 $ sudo apt-get install libgnome2-dev
```
```
p$ dpkg -L libgnome2-dev|grep .pc
/usr/lib/pkgconfig/libgnome-2.0.pc
```

So you want libgnome-2.0 to the pkg-config command 
```
$ pkg-config --cflags --libs libgnome-2.0
-DORBIT2=1 -D_REENTRANT -pthread -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0  -pthread -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lgmodule-2.0 -lORBit-2 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
```

---

### Post by captnemo on 2011-02-18
That was it.  Adding libgnome-2.0 to the cflags fixed it.  I had assumed that invoking gtk+-2.0 captured all of the gnome stuff at once for the compiler and linker.

Thank you very much!  Now it makes sense.

---

