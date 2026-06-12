---
title: "Command line method of removing LVM during installation?"
date: 2015-08-07
forum: Packaging and Compiling Programs
---

### Post by roland-logikalsolutions on 2015-08-07
Building a custom ISO for client and preseeding responses. All is fine except when a machine currently has LVM (Logical Volume Manager) stuff installed. Since this will execute from within an installation procedure I do not have a full bash shell, etc. The standard partitioning which happens with Ubuntu will not remove the LVM and installation fails.

Under normal circumstances regular ISO users click on "manual" and forcibly delete all partition information. These users aren't technical and the installation needs to never show them anything about partitioning.

Is there a command line method, which will work from within the Live CD installation _without_ installing other packages, to nuke all partition information?

---

### Post by TheFu on 2015-08-08
LVM is installed onto paritions too. Just delete the partitions.

Don't know how to de-build an lv, vg, pe cleanly inside the installer environment.  Deleting the partition is the best/shortest way. Clearly any data inside would be gone.

BTW - using an LVM setup always could make your installation much easier.  Only 2 partitions needed - 1 for /boot the other for everything else.  Then shove whatever you need inside the pe, vg, and create LVs for swap, /, /var, /home based on total storage available.  Oh and please don't make /boot as small as the default sizes from a stock install. Those are 50% too small - 800MB should be the min, IMHO.

---

