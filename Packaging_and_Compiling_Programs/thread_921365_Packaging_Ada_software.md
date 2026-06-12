---
title: "Packaging Ada software"
date: 2008-09-16
forum: Packaging and Compiling Programs
---

### Post by Pro-reason on 2008-09-16
OK, so I know how to use PPA to package C source code which already has a proper configure script and makefile, and I know how to package arbitrary stuff (e.g. images).

How about packaging Ada source code (.adb files).  I'm not sure how to even start with that.

---

### Post by Pro-reason on 2008-09-17
I know the command to compile these files: *gnatmake*.

How can I throw together a script (a configure script, I suppose), that Launchpad will accept, and make a DEB out of?

---

### Post by loell on 2008-09-17
> **Pro-reason said:**
> I know the command to compile these files: *gnatmake*.

How can I throw together a script (a configure script, I suppose), that Launchpad will accept, and make a DEB out of?

probably add **gnatmake** in the rules file?

---

