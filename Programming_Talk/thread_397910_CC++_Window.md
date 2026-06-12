---
title: "C/C++ Window"
date: 2007-03-31
forum: Programming Talk
---

### Post by dJnEvS on 2007-03-31
How do i create a Window in C or C++ ?
I dont think its simple, i just want to see a example code to see how it works.
So, if anyone knows how this works, and/or has a source code of it. Please let me know.

What im looking for:
1. How to make a new (empty) Window
2. How to add components in the window (textbox, button etc.)


Thank you,
Sven

---

### Post by moephan on 2007-03-31
Sven,

You need to choose a UI library. I suggest Gtk because it is the "native" Gnome library, and it is easy to create interface with a tool call Glade. There are plenty of threads on using Glade and Gtk, so this info should get you started with more searches.

I just noticed this stick thread which you should probably look over as well:
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

Cheers, Rick

PS: There are other UI libraries to choose from as well, you can check around about that too.

---

### Post by dJnEvS on 2007-03-31
Im trying to install GTK stuff,
but gtk cant compile because of atk,
and atk cant compile because of glib.

./configure of atk returns this:
```
checking for GLIB - version >= 2.5.7...
*** 'pkg-config --modversion glib-2.0' returned 2.12.4, but GLIB (2.13.0)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
```

So, i need to uninstall gtk 2.12.4,
but how do i do that.

---

### Post by Mirrorball on 2007-03-31
.

---

