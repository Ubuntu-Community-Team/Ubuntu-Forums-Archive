---
title: "error 17 while restoring grub"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by sharks on 2008-05-23
error 17 while restoring grub.any solutions?

---

### Post by brigux on 2008-05-23
simple solution: reinstall the OS, and when the option of installing the boot loader comes up, set it to install on MBR.

---

### Post by sharks on 2008-05-23
should i reinstall it completely or is there a way to install grub alone

---

### Post by alienexplorers on 2008-05-23
Why not try the SUper Grub Disk to reinstall grub.  Just google the name and download  it and save it to CD.

---

### Post by bumanie on 2008-05-23
You should be able to reinstall grub via the live cd or if that doesn't work you can try super grub disc, which is a live cd that, as per the name, often resolves grub problems.
Please post output of terminal command > sudo fdisk -l (that's a lower case L, not a number one) This can be done from the live cd.

---

### Post by sharks on 2008-05-23
i have found the solution myself,anyway thanks for u guys
[http://ubuntuforums.org/showthread.php?t=804696](http://ubuntuforums.org/showthread.php?t=804696)

---

