---
title: "Debian packaging postinst"
date: 2010-06-03
forum: Packaging and Compiling Programs
---

### Post by Mt.Olympus on 2010-06-03
I have created my own debian packages and I was wondering on how to setup a post install script on the debian package.

---

### Post by SevenMachines on 2010-06-04
debhelper will install debian/<package>.postinst (or just debian/postinst) automagically, and maintainer scripts of the same form (prerm, postrm, etc). if you're using debhelper that will do it, dh_make generates some examples if you want skeletons of the actual scripts to look at

---

