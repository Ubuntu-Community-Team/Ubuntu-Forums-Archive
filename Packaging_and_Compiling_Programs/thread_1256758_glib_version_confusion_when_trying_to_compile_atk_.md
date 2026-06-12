---
title: "glib version confusion when trying to compile atk (for gimp)"
date: 2009-09-03
forum: Packaging and Compiling Programs
---

### Post by ceti331 on 2009-09-03
am trying to compile the gimp under ubuntu 9 (frustratingly i had all this compiling a while back)
got the source (2.6.7), went on to get others:-
atk-1.27.90  gegl-0.1.0  gtk+-2.16.6      pango-1.24.5
babl-0.1.0   gimp-2.6.7  glib-2.20.5  intltool-0.40.6

./configure, make, make install in each.. 
However on getting to atk, configure is telling me this.
Q1 Any ideas how to fix? where *is* the old version of glib? 

checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.20.5, but GLIB (2.20.1)
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
walter@walter-laptop:~/src/atk-1.27.90$

---

### Post by Bachstelze on 2009-09-03
Why did you compile glib from source? The versin shipped with your Ubuntu is perfectly sufficient.

---

