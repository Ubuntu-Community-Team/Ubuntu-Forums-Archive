---
title: "Compiling gdkpixbuf"
date: 2011-02-22
forum: Packaging and Compiling Programs
---

### Post by Luan Koerich on 2011-02-22
Hello, everybody.
This is my first post here in Ubuntu Forums.
(English is not my mother language, so forgive me for such poor words).

I am trying to compile GTK+, but I'm not able to install gdkpixbuf (one of GTK's dependecies). All other dependencies are installed, but this.

In fact, I had already compiled GTK+ on Ubuntu 9.10, and I hadn't any problems.
Now I am trying to compile it back, in Ubuntu 10.10.

When I try to configure gdkpixbuf-2.23.1, I get this error:

```

checking for GLIB - version >= 2.25.15... 
*** 'pkg-config --modversion glib-2.0' returned 2.28.0, but GLIB (2.28.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.25.15 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.


```

The fist time I compiled GTK+ and its dependencies, in 9.10, I did not worry about LD_LIBRARY_PATH, or anything like this, and all worked fine.

But now, in 10.10, I tried to follow these steps:
[http://library.gnome.org/devel/gtk/unstable/gtk-building.html](http://library.gnome.org/devel/gtk/unstable/gtk-building.html)
And everything started to go wrong.

Now I am trying to complie everything just using "./configure", with no worries about this 
LD_LIBRARY_PATH and, well, it is not working.

Well, I am new to (this part of) ubuntu and I can't understand the mess I am doing here.
Could anyone help me, please?

Thanks!

---

### Post by -DarkAceZ- on 2011-07-24
I've been trying this too, Arista Transcoder needs a newer version of GTK+ and GTK+ needs glib-2.0 >= 2.27.3 and gdk-pixbuf-2.0 >= 2.21.0 but they will not install.

---

