---
title: "Can't see XP Disk"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by mr-woof on 2008-10-19
Hi all,

I've only just installed ubuntu 8.04 over the last couple of days on an old 10g ide drive, i also have a sata drive in the pc with xp installed. 

I don't seem to be able to see the two windows partitions anywhere, i've looked in places with no luck. I'm a complete linux noob so i'm just finding my way round the system at the moment, am i missing something very obvious here?

:)

---

### Post by Paqman on 2008-10-19
Install ntfs-config, it'll sort out mounting your Windows drive no problem.

Applications > Add/Remove, first thing that comes up if you search for NTFS.

---

### Post by mr-woof on 2008-10-19
I've installed that, but still nothing in places :confused:

When i run the program, i can see the ubuntu disk and nothing else

---

### Post by bpowell2005 on 2008-10-19
Perhaps you could go to the command prompt and type "sudo fdisk -l" (that's fdisk, space, dash, lower-case L)...this will list the partitions of all the drives Ubuntu can see...post the output here, and from there, we can give you commands to type to mount the NTFS windows drives.

Be careful with fdisk, as it can also EDIT your partitions and that could be real bad if you did that by accident.

---

### Post by mr-woof on 2008-10-19
Disk /dev/sda: 10.0 GB, 10007101440 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7b2b7b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1215     9759456    7  HPFS/NTFS

Only the Ubuntu disk is showing up :(

---

### Post by alzie on 2008-10-19
This sounds odd to me.  Can you still boot into XP?

---

### Post by bpowell2005 on 2008-10-19
> **alzie said:**
> This sounds odd to me.  Can you still boot into XP?

This is a good question! If the disk is installed, fdisk -l should be displaying it (and Ubuntu for that matter!) are you sure the drive is connected and powered up?

---

### Post by mr-woof on 2008-10-19
100% working fine, i'm using it now. 

Could it be something like the sata drive isnt set to master? Would that matter?

---

