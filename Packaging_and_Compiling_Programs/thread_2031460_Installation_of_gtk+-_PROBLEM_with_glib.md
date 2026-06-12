---
title: "Installation of gtk+- PROBLEM with glib"
date: 2012-07-22
forum: Packaging and Compiling Programs
---

### Post by khankamil19 on 2012-07-22
to install gtk+-2, several other softawres are needed to be installed eg

[LIST]
[*][GLib 2.32]("http://ftp.gnome.org/pub/gnome/sources/glib/2.32/")
[*][Pango 1.30]("http://ftp.gnome.org/pub/gnome/sources/pango/1.30/")
[*][Gdk-Pixbuf 2.26]("http://ftp.gnome.org/pub/gnome/sources/gdk-pixbuf/2.26/")
[*][ATK 2.4]("http://ftp.gnome.org/pub/gnome/sources/atk/2.4/")
[/LIST]
I have problem with the installation of "Pango 1.30", when I type
./configure 

in the directory of Pango 1.30, it give me the following error,


checking for GLIB - version >= 2.31.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.31.22, but GLIB (2.30.0)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.31.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).



Please help me out in this regard. how to deal with it.

---

### Post by Laiquendi on 2012-07-22
Did you try things written in the error message?
```
You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
```

---

### Post by khankamil19 on 2012-07-22
The problem is that I dont know how to check or evaluate the error. can you please breifly explain what should I do step by step?
2nd matter is that, is there any linux OS available with built-in gtk+ installed? I need it because I have software which can run under linux platform only if the gtk is installed.

---

