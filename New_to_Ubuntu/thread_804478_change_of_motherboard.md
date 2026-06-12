---
title: "change of motherboard"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jonathan21 on 2008-05-23
I recently started having problems with my motherboard I  was wondering how you get ubuntu to pickup new motherboard drivers without reinstalling ubuntu.I have gotten kernal panic error when changing motherboard.chipset is different.

---

### Post by saj0577 on 2008-05-23
Im no expert at this sort of problem but I will try to help untill someone more knowledgable helps out. 

You tested the new motherboard definately works with ubuntu? Live CD?

Saj

---

### Post by marufaberlin on 2008-05-23
that's a difficult task, my approach would be the following:

make two partitions:

partition 1: your old linux
partition 2: clean install of a distro (will be deleted later)

[LIST=1]
[*]boot partition 2
[*]chroot to partition 1
[*]grab a kernel source tarball
[*]make it
[*]get additional modules & install
[*]boot partition 1
[*]reinstall kernel using apt
[*]use module-assistant (or do it manually) to install additional modules
[*]delete partition 2 and grow file system on partition 1 to fit
[/LIST]

but no guarantees, might just go wrong...


what about a new, clean install? you can still mount your old home folder and reinstall apps?

hope this helps.

---

### Post by jonathan21 on 2008-06-02
had to eventually backup and reinstall thanks guys for your help.

---

### Post by davidsrsb on 2008-06-02
Linux is normally very tolerant of major hardware changes, as there is no equivalent of the Windows registry. Usually problems are down to the use of RAID or subtle changes in the way the disk controller handles the drive geometry.

---

### Post by stchman on 2008-06-02
> **jonathan21 said:**
> I recently started having problems with my motherboard I  was wondering how you get ubuntu to pickup new motherboard drivers without reinstalling ubuntu.I have gotten kernal panic error when changing motherboard.chipset is different.

From what I understand about the Linux kernel the new hardware drivers will be enabled since all the drivers are in the kernel.

If this does not work reinstalling Hardy takes about 20 minutes.

---

