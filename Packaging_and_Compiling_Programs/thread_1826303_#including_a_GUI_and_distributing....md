---
title: "#including a GUI and distributing..."
date: 2011-08-16
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-08-16
I have a command-line program, in C++, that does what it is supposed to do, however I wish to distribute it (which means a GUI):

a) which GUI library would you recommend?

b) How do I put in a convenient place so that the library goes with the program? Most GUI libraries have makefiles which end up in /usr/lib or wherever, and that means:

```
#include <GUI.h>
``` wont work on somebody else's pc. How do I get around this?

c) I appreciate this is a commonly asked question, but where do I find standards and instructions for creating Ubuntu .deb packages? Obviously, my program is nowhere near the standards needed for the repositories, but I plan to make it a lot better over the coming months. Thanks for the help! :D

---

### Post by SevenMachines on 2011-08-16
(a) There are probably a million answers based on personal preference here, personally I'd say the well established gtk or qt, there are bindings for a lot of languages for the both of them too. There are plenty of others too though, many speak highly of them . Personally when I have to do gui's :*( I use glade gui designer, keep as much of the design out of code, and gtkmm, the c++ gtk bindings. If you're using qt there's qt-designer(?) to do the same sort of thing, dont code your gui! You'll probably get a much bigger range and depth of gui opinion on the programming forum though.

(b) This really depends on what language especially that you use. Bottom line is, libraries are set up to be used! Choose the language and gui set first and the rest will follow!

A c++ and gtkmm example...  
Dev packages often come with pkg-config data which can automatically generate the right paths and compile options for you, for example, for a gtkmm 3.0 app called mygtkapp I could do something like
```
$ g++ -o mygtkapp mygtkapp.cpp `pkg-config --cflags --libs gtkmm-3.0`
```which sorts out everything for you. Actually it works out as
```
$ g++ -o mygtkapp mygtkapp.cpp -pthread -DGSEAL_ENABLE -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/gtkmm-3.0 -I/usr/lib/gtkmm-3.0/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-3.0 -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/gtk-3.0/unix-print -I/usr/include/gdkmm-3.0 -I/usr/lib/gdkmm-3.0/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include  -pthread -lgtkmm-3.0 -latkmm-1.6 -lgdkmm-3.0 -lgiomm-2.4 -lpangomm-1.4 -lgtk-3 -lglibmm-2.4 -lcairomm-1.0 -lgdk-3 -latk-1.0 -lcairo-gobject -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lpango-1.0 -lfreetype -lfontconfig -lgmodule-2.0 -lcairo -lsigc-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
```You can see why pkg-config is a time saver!! 

(c) See the all new Ubuntu Packaging Guide [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
    And the comprehensive Debian New Maintainers Guide [http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)

It looks like a lot of reading but if you choose a standard way of building your src, gnu autotools, A simple makefile, cmake, setup.py, ant, etc... most are covered by debhelper and cdbs which makes packaging *much* more straightforward

---

### Post by MG&amp;TL on 2011-08-17
Thank you. Really helpful. :)

I thought it was difficult and pointless, and that's true, but at least there's guides for the difficult and pointles bits. Thanks!

---

