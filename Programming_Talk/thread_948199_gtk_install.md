---
title: "gtk install"
date: 2008-10-15
forum: Programming Talk
---

### Post by epotn on 2008-10-15
im trying to install gtk dev so i can hopefully make some gui program or w/e
but i get this when i try to install:


```

checking for GLIB - version >= 2.17.6... 
*** 'pkg-config --modversion glib-2.0' returned 2.18.1, but GLIB (2.16.4)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.17.6 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.
```

thanks
epotn

---

### Post by geirha on 2008-10-15
```
aptitude search glib.*-dev
```
You probably need [libglib2.0-dev](apt://libglib2.0-dev)

---

### Post by jespdj on 2008-10-15
What version of Ubuntu are you using? It sounds like there is a version conflict for the version of GTK; maybe you have GTK development files that are of a different (newer) version than the GTK libraries that are installed on your system.

How did you install the GTK development header files? Did you download the GTK header files from [www.gtk.org](www.gtk.org) for GTK 2.17?

Don't do that; instead, install the package libgtk2.0-dev:
```
sudo apt-get install libgtk2.0-dev
```
This will install GTK header files that match the GTK version installed in your OS.

---

### Post by geirha on 2008-10-15
Ah, sorry, was too quick with my post earlier. Indeed, you do have the glib dev pacakge installed. Are you trying to compile gtk yourself? I recommend you use libgtk2.0-dev from the repository and use that. If you really want to compile the newest gtk yourself, you need to also do the same for glib and the other dependancies.

---

