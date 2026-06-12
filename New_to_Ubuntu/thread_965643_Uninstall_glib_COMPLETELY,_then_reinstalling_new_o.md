---
title: "Uninstall glib COMPLETELY, then reinstalling new one"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Racecar56 on 2008-10-31
HELP! And this problem is getting me angry too!
I want to install atk so I can get gtk, and atk says this:

> 
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.19.0, but GLIB (2.18.2)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

How to I shred all of glib off? I want to upgrade glib so I can get ATK!
And I don't want to install an older version either, and I am using Intrepid Ibex.

[COLOR="Red"]PROBLEM SOLVED!
I ran sudo ldconfig and then ./configur'd ATK. It worked![/COLOR]

---

### Post by ezramorris on 2008-10-31
Hi,
Please mark your thread as solved if you no longer have this problem.
Thanks. :-)

---

