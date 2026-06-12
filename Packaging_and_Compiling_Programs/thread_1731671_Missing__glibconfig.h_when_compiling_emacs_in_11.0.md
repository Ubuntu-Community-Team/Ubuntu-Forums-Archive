---
title: "Missing  glibconfig.h when compiling emacs in 11.04 beta 2"
date: 2011-04-17
forum: Packaging and Compiling Programs
---

### Post by kaptajnbligh on 2011-04-17
Upgraded to 11.04 beta 2 yesterday. Emacs had this strage bug where buffers were not listed in the buffer menu. 

Anyways, I downloaded the lastest stable emacs trying to build it myself.

Compiling with gtk2 toolkit now gives this error:

```

In file included from /usr/include/glib-2.0/glib/galloca.h:34:0,
                 from /usr/include/glib-2.0/glib.h:32,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from xterm.h:44,
                 from dispnew.c:56:
/usr/include/glib-2.0/glib/gtypes.h:34:24: fatal error: glibconfig.h: No such file or directory
compilation terminated.
make[1]: *** [dispnew.o] Error 1

```Strange thing is that glibconfig.h is on my system:

```

$ locate glibconfig.h
/usr/lib/i386-linux-gnu/glib-2.0/include/glibconfig.h

```Any idea how to fix this?

---

### Post by kaptajnbligh on 2011-04-18
Turned out to be a macro substitution error in configure.

Solution:

[http://lists.gnu.org/archive/html/bug-gnu-emacs/2011-04/msg00307.html](http://lists.gnu.org/archive/html/bug-gnu-emacs/2011-04/msg00307.html)

---

