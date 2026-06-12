---
title: "resizing ubuntu partition by deleting bodering windows partition"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by linux spartan on 2013-02-24
i have two hard disks on my laptop with windows xp on my primary hard disk and on my extended hard disk i have ubuntu on 60% of it and windows on the rest of it excluding the 4GB swapspace but since i dont use windows much i would like to have ubuntu on the whole extended hard disk...there is not much on the windows partition as of yet,just about 50 MB occupied...which would be the best way...not necessarily simplest to go about this without losing data which is my primary concern for the ubuntu partition

---

### Post by x64Architecture on 2013-02-24
did you install Ubuntu through the wubi installer or through the iso?

---

### Post by linux spartan on 2013-02-24
i used .iso):P

---

### Post by x64Architecture on 2013-02-24
Boot from a live Ubuntu cd/usb and use gparted to delete the windows partition and extend the Ubuntu partition.

---

### Post by linux spartan on 2013-03-05
worked...check link to solve resulting grub rescue error [http://ubuntuforums.org/showthread.php?t=2122396](http://ubuntuforums.org/showthread.php?t=2122396)

---

