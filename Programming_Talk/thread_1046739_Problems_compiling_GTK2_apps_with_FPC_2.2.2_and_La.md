---
title: "Problems compiling GTK2 apps with FPC 2.2.2 and Lazarus [SOLVED]"
date: 2009-01-21
forum: Programming Talk
---

### Post by gpremuda on 2009-01-21
Lazarus cannot compile GTK2 apps with GTK greate or equal to 2.13.4, e.g. on Ubuntu 8.10 we have GTK 2.14.

A quick workaround that works is to pass --noinhibit-exec to ld, that is "-k--noinhibit-exec" to FPC command-line. The ld will then treat unresolved references as mere warnings, and will produce working executable (assuming your program doesn't actually call obsoleted GTK2 functions).

Of course, you can also upgrade to FPC from SVN. Above workaround is useful only if you have to stick to released FPC 2.2.2. 

Original post at [http://lists.freepascal.org/lists/fpc-pascal/2009-January/019838.html](http://lists.freepascal.org/lists/fpc-pascal/2009-January/019838.html)

---

