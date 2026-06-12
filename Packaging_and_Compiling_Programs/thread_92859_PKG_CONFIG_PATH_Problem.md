---
title: "PKG_CONFIG_PATH Problem"
date: 2005-11-20
forum: Packaging and Compiling Programs
---

### Post by sonny on 2005-11-20
Hi, it's been a while without posting anything, but I have found a problem that I don't understand, I'm trying to find a chart editor (a gui based one) with a lot of functions and flexibility, I've found SciGraphica wich requires 4 package to be prevously installed in the system:
glib-2.8.4
gtk+-2.8.7
atk-1.10.1
cairo-1.0.0

I've installed; with much effort and patience, glib-2.8.4, I'm sure it's installed, in Ubuntu we have 2.8.3 so I had to remove it and do some more stuff, anyway, I have the other programs installed except for the main package because I can't pass the ./configure in the atk package, when I do: ./configure in the atk-1.10.1 package I get the following error:

checking for pkg-config... (cached) /usr/local/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.8.4, but GLIB (2.8.3)
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

But as I said, I already installed the glib-2.8.4 library, my question is, where can I modify the PKG_CONFIG_PATH variable, and if it's a big file, how can I distinguish the line?

An other questions, I'm trying to get working the StarChart package of StartOffice, I fixed some dependencies problems, but now I get:

./starchart: can't load library '/usr/lib/libXt.so.6'
        Permission denied
./starchart: can't find library 'libXt.so.6'

The library is a soft link to libXtst.so.6.0.1, here are the current permissions:

-rw-r--r--  1 root root 418308 2005-09-12 03:11 libXt.a
lrwxrwxrwx  1 root root     14 2005-11-20 02:23 libXt.so -> libXt.so.6.0.0
lrwxrwxrwx  1 root root     14 2005-11-20 02:23 libXt.so.6 -> libXt.so.6.0.0
-r--r--r--  1 root root 314228 2005-09-12 03:11 libXt.so.6.0.0

I tryed many combanitions of the file's permissions but the only one that gives a diferent result is allowing the execute permission, getting the following error:

./starchart: can't load library '/usr/lib/libXt.so.6'
        Exec format error
./starchart: can't find library 'libXt.so.6'

As this is a library, I don't expect it to be execute, how can I fix this?.

Thanks for all your help, I know you wont let me down.

---

### Post by tripleee on 2006-01-06
Why don't you simply install the version for Ubuntu which is in the universe? At least it's there for Breezy/amd64:

```
me@breezy/amd64$ apt-cache show scigraphica
Package: scigraphica
Priority: optional
Section: universe/math
Installed-Size: 2992
Maintainer: David Schleef <ds@schleef.org>
Architecture: amd64
Version: 0.8.0-9ubuntu2
Replaces: scigraphica-common, scigraphica-gnome
Depends: gdk-imlib1, libc6 (>= 2.3.2.ds1-4), libglib1.2 (>= 1.2.0), libgtk1.2 (>= 1.2.10-4), libgtkextra17, libncurses5 (>= 5.4-1), libreadline4 (>= 4.3-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxi6 | xlibs (>> 4.1.0), libxml1 (>= 1:1.8.14-3), python2.4 (>= 2.3.90), zlib1g (>= 1:1.2.1), python (<< 2.5), python (>= 2.4), python2.4-numeric, python-gtk-1.2, defoma, psfontmgr (>= 0.4.8)
Conflicts: scigraphica-common, scigraphica-gnome
Filename: pool/universe/s/scigraphica/scigraphica_0.8.0-9ubuntu2_amd64.deb
Size: 777886
MD5sum: 40ad9051dea2724c805f46b6001d4dde
Description: Scientific graphics and data manipulation (shared files)
 SciGraphica is a scientific application for data analysis and technical
 graphics. It pretends to be a clone of the popular commercial (and
 expensive) application "Microcal Origin". It fully supplies plotting
 features for 2D charts.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by Castar on 2006-06-09
It's too old! 0.8.0 when 2.1.0 is around...

---

