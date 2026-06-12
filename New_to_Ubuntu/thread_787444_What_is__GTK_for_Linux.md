---
title: "What is  GTK for Linux?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-08
I was reading that a few programs for installing on Linux require a GTK windowing system in order to work... what is that?
Does Ubuntu include it?

Thanks
b.

---

### Post by Sef on 2008-05-08
From [Gnome]("http://developer.gnome.org/doc/GGAD/z4.html"):

>  GTK+

GTK+, or the Gimp Tool Kit, is the GUI toolkit used in Gnome applications. GTK+ was originally written for the Gimp (GNU Image Manipulation Program --- [http://www.gimp.org](http://www.gimp.org)), but has become a general-purpose library. GTK+ depends on glib.

The GTK+ package includes GDK, the Gimp Drawing Kit, which is a simplification and abstraction of the low-level X Window System libraries. Since GTK+ uses GDK rather than calling X directly, a port of GDK permits GTK+ to run on windowing systems other than X with relatively few modifications. GTK+ and the Gimp have already been ported to the Win32 platform in this way.



---

### Post by perce on 2008-05-09
GTK are graphic libraries. To make things short, the programs that draw the windows, the menus, and things like that. Ubuntu has them installed by default.

---

