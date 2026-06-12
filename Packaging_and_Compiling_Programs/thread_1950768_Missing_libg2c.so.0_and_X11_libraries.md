---
title: "Missing libg2c.so.0 and X11 libraries"
date: 2012-04-01
forum: Packaging and Compiling Programs
---

### Post by LaszloParkanyi on 2012-04-01
Because of the deprecated libg2c.so.0 library I had to recompile one of my graphics programs. The problem is that I cannot specify correctly the X11 libraries. In my present Makefile X11 libraries are referred to as

  -L/usr/X11R6/lib -lX11

libx11-dev is installed.  Can anyone help?

---

### Post by MadCow108 on 2012-04-01
what is the actual problem?

---

