---
title: "cross-compile(on ubuntu for win32) glib gnet application"
date: 2009-11-19
forum: Programming Talk
---

### Post by IOException on 2009-11-19
Hi, all

I never met with cross-compile before. I need some glib/gnet application to be compiled for win32.

I've encountered with following problems:

1) first of all I need win32 versions of glib
 To do that I got src from here: [http://www.gtk.org/download-windows.html](http://www.gtk.org/download-windows.html) and was guided by [http://library.gnome.org/devel/glib/unstable/glib-cross-compiling.html](http://library.gnome.org/devel/glib/unstable/glib-cross-compiling.html) instruction
   
but ./configure failed by absence of libintl.h header. Ok. 
I've tried to install gettext from sources (from here [http://www.gtk.org/download-windows.html](http://www.gtk.org/download-windows.html))

./configure - ok
make -nok


Did anyone do cross-compile glib on ubuntu for windows? May be I should use some other distribution for this?

---

### Post by IOException on 2009-11-19
2) next problem is to get gnet for win32 (I would got already compiled glib for win32 ([http://www.gtk.org/download-windows.html](http://www.gtk.org/download-windows.html)) if gnet ./configure not required thread-safe glib version, but glib for win32 from ([http://www.gtk.org/download-windows.html](http://www.gtk.org/download-windows.html)) isn't thread-safe (as gnet ./configure says))

---

