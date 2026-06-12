---
title: "[SOLVED] Swap partition will not mount during install."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by dshaker on 2008-10-15
Situation:  I have an old (4 yr) HP laptop that I want to convert to Ubuntu from Win XP.  I have booted from the 8.04.1 desktop i386 CD.  The OS seems to work fine.  I have invoked the install program that is displayed as an icon on the desktop.

The problem: One of the options which I need to specify during the installation is the disk partitioning.  I have a 30GB disk on this machine.  If I select Guided partitioning, it makes a single 30GB EXT3 partition with a swap partition as a logical partition within it (or so I understand) and then, when it comes time, during the
install, to mount the EXT3 partition, it tells me that it can't.

If I use manual partitioning, I have tried specifying a 25GB EXT3 journaling file system and a 5GB swap partition.  Then it uniformly tells me that it can't mount the swap partition.  Changing the locations of the partitions on the disk seems to have no effect on the ability of the system to mount the swap.

What am I doing wrong?

---

### Post by Duck2006 on 2008-10-15
> If I use manual partitioning, I have tried specifying a 25GB EXT3 journaling file system and a 5GB swap partition.

Try 1Gb for the swap partition.

---

### Post by wolfen69 on 2008-10-15
first off, you don't need 5gb of swap. secondly, see [this]("http://ubuntuforums.org/showthread.php?t=939529&highlight=mount+swap") thread for swap help.

---

### Post by dshaker on 2008-10-15
So the theory is that my swap partition is too big to mount?

---

### Post by Duck2006 on 2008-10-15
> **dshaker said:**
> So the theory is that my swap partition is too big to mount?

Yes, the swap partition is far to big.

---

### Post by dshaker on 2008-10-15
That worked!  Thanks!

---

