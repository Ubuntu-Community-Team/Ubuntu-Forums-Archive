---
title: "Build a package without patches"
date: 2009-08-13
forum: Packaging and Compiling Programs
---

### Post by arky on 2009-08-13
I am trying to investigate a problem in gnome-power-manager package. How do you build a package without applying the ubuntu patches.

---

### Post by laney on 2009-08-19
There will be an include in the rules file, deleting that line should do the job. Something like "include /usr/share/dpatch/dpatch.make", but obviously different depending on the patchsys used.

---

### Post by arky on 2009-08-19
Thanks let me try that.

---

### Post by arky on 2009-08-23
There is line in debian/rules. Would commenting this out suffice ?

include /usr/share/cdbs/1/rules/patchsys-quilt.mk

---

