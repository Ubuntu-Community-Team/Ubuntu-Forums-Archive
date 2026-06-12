---
title: "GCC cannot find GTK headers"
date: 2007-04-16
forum: Packaging and Compiling Programs
---

### Post by PointSource on 2007-04-16
Hi.

As explained above, GCC has trouble finding the header files for GTK development. I'm quite sure I have all the "-dev" deb packages installed.

Errors include "callbacks.c:5:21: error: gtk/gtk.h: No such file or directory".

Is there a $PATH-like variable that needs to be set?

By the way, I'm using Anjuta as my IDE. 

TIA

---

### Post by PointSource on 2007-04-16
OK, I found the problem, the IDE needed include paths.

The command line worked all the time.

---

