---
title: "libgtk2.0-dev header file access from C++"
date: 2008-02-29
forum: Packaging and Compiling Programs
---

### Post by GrayedOut on 2008-02-29
Hi,

I'm pretty new to Linux, and I figure I'm doing something simple wrong here, but I'm having a problem with libgtk2.0-dev. I'm developing in C++ (using the g++ compiler) and I've successfully installed a bunch of packages and used their header files with #include <folder/header.h>.

However, on installing the libgtk2.0-dev package from Synaptic, it ended up in the folder usr/include/gtk-2.0/. The header file gtk.h is located at usr/include/gtk-2.0/gtk/gtk.h

So, as I did with the other packages I installed, in my C++ code I wrote:

#include <gtk-2.0/gtk/gtk.h>

But this time it causes a problem at compile, with a load of messages like:

In file included from main.cpp:48:
/usr/include/gtk-2.0/gtk/gtk.h:31:21: error: gdk/gdk.h: No such file or directory

This is confusing - it's like gtk itself is expecting its own header files to be in usr/include/gtk/ (or /gdk/), not usr/include/gtk-2.0/gtk/

I am missing something obvious here?

Thanks,

-GO

---

### Post by WW on 2008-02-29
[GDK](http://en.wikipedia.org/wiki/GDK) is not the same as [GTK+](http://en.wikipedia.org/wiki/GTK%2B).  It is a different, lower-level library.

I don't know which package provides the GDK header files, but I'm sure someone will drop in soon and let you know.

---

### Post by GrayedOut on 2008-02-29
Ah, serves me right - thanks for the comment, and I'll have a poke around at this, but here's a more verbose version of the output I have in case this sheds more light on it:

In file included from main.cpp:48:
/usr/include/gtk-2.0/gtk/gtk.h:31:21: error: gdk/gdk.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:32:32: error: gtk/gtkaboutdialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:33:31: error: gtk/gtkaccelgroup.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:34:31: error: gtk/gtkaccellabel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:35:29: error: gtk/gtkaccelmap.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:36:31: error: gtk/gtkaccessible.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:37:27: error: gtk/gtkaction.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:38:32: error: gtk/gtkactiongroup.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:39:31: error: gtk/gtkadjustment.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:40:30: error: gtk/gtkalignment.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:41:26: error: gtk/gtkarrow.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:42:32: error: gtk/gtkaspectframe.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:43:30: error: gtk/gtkassistant.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:44:25: error: gtk/gtkbbox.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:45:24: error: gtk/gtkbin.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:46:29: error: gtk/gtkbindings.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:47:24: error: gtk/gtkbox.h: No such file or directory

(etc.)

I hadn't realised the difference in the first error line from the rest when I first pasted it, and didn't want to post the entire epic error list (which is several times larger than above) - sorry about that!

---

### Post by bruce89 on 2008-02-29
Normal GTK+ is in C, consider using GTKmm for C++.

---

