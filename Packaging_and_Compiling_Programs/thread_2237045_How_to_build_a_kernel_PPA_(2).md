---
title: "How to build a kernel PPA (2)"
date: 2014-07-30
forum: Packaging and Compiling Programs
---

### Post by rjvbertin on 2014-07-30
I'm running Kubuntu 14.04, with a custom kernel I rebuild every so many upstream updates. The 2 hosts I run Linux on are a netbook with and AMD C60 and an HP G62 that's over 4y old, also with an AMD CPU. So there's some incentive to run a kernel with as many optimisations as possible, but in terms of code generation (-O3 -march=amdfam10) and patches, the Con Kolivas patches to be exact.

I'd love to publish this work of preparation via a PPA, rather than doing the building just for myself only (and waiting for it to finish).

An older thread ([http://ubuntuforums.org/showthread.php?t=1682345](http://ubuntuforums.org/showthread.php?t=1682345)) gives a few outlines, but doesn't really go into the specifics, neither how to prepare the source (patches applied, or in debian/patches ... knowing that the CK patches must be applied before doing make xconfig), nor how to ensure the build will use the right .config file.
Is there a more complete set of instructions somewhere?

---

