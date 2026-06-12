---
title: "glib.h: No such file or directory"
date: 2011-06-13
forum: Packaging and Compiling Programs
---

### Post by Boneymin on 2011-06-13
I have never built a project in Ubuntu before and I am trying to come to grips with the GNU build tools and process.

When I try to make I get the 'glib.h - no such file or directory'.

This is the output of 'pkg-config --cflags --libs glib-2.0'

-I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -L/usr/lib/i386-linux-gnu -lglib-2.0

Do these compiler options look ok? Should the 'i386-linux-gnu' be there?

---

### Post by MadCow108 on 2011-06-14
the options look ok, what are you trying to compile?

i386-linux-gnu are the new multiarch triplets, which allow installing libraries from multiple architectures on the same system (e.g. amd64 and i386)
[http://wiki.debian.org/Multiarch/Implementation](http://wiki.debian.org/Multiarch/Implementation)

---

