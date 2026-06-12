---
title: "Cross Compiling to FreeBSD"
date: 2009-02-19
forum: Packaging and Compiling Programs
---

### Post by Flare183 on 2009-02-19
Is there a way that I can cross-compile software for FreeBSD on Ubuntu? I have been compiling ports on FreeBSD on my pentium 3 but it takes forever, and my quad core Ubuntu Machine could compile things in seconds when it takes hours on the FreeBSD machine.

---

### Post by Cracauer on 2009-02-20
Linux has a FreeBSD compat mode, like FreeBSD's Linux compat.

If it works well enough  you just slap a full FreeBSD tree into a chroot and you are done.

If it, it's trouble if you want to build more than simple programs that don't require extensive libraries.

---

