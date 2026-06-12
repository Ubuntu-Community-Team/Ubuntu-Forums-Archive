---
title: "How to get dev. packages? (need .pc) files"
date: 2005-11-02
forum: Programming Talk
---

### Post by dzonekl on 2005-11-02
Hello, 

I am trying to build the jdic library (Java desktop) on the latest ubuntu. 
Here I run into problems as the make file is expecting some .pc files as includes to the compilation: 

See snap of make file here: 

EXTRA_INCLUDES = `pkg-config --cflags glib-2.0` \
                 `pkg-config --cflags libgnome-2.0` \
                 `pkg-config --cflags gnome-vfs-2.0`\
                 `pkg-config --cflags gnome-vfs-module-2.0` \
                 `pkg-config --cflags bonobo-activation-2.0` \
                 `pkg-config --cflags libbonobo-2.0` \
                 `pkg-config --cflags ORBit-2.0` \
                 `pkg-config --cflags gconf-2.0`

these .pc files are normally part of the library distributions, but can't be resolved by the pkg-config utility on Ubuntu. (I tried to locate the .pc files on my system but coudn't find them). 

My question: Do I need to install separate dev packages for glib, gnome, orbit etc... to get the .pc files? 

Thanks for the help.

If you are interrested, I am trying to include the jdic library in my application named jPodder. ([www.jpodder.com)](www.jpodder.com)). To have a good working Ubuntu release.

---

### Post by LorenzoD on 2005-11-06
The development files for any package will be in a corresponding <package>-dev package. So for libgnome, you would have to install libgnome-dev as well.

---

