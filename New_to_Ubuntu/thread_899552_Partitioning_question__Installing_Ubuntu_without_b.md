---
title: "Partitioning question:  Installing Ubuntu without breaking Vista"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Envergure on 2008-08-24
I want to install Ubuntu on a single-HDD laptop which already has Vista Home Premium 64bit on it.

When I open Vista's Explorer I see two drives (that is, two partitions):
C: (142 GB) - Has Vista and all my files
D: (139 GB) - Empty

However the Ubuntu installer shows four partitions:
/dev/sda1 (14 GB) - Maybe the restore partition
/dev/sda2 (153 GB)* - Same as C:
/dev/sda3 (149 GB)* - Same as D:
/dav/sda4 (4 GB) - Unknown (maybe *this* is the restore partition)

So here's the problem:  This HDD can only have four partitions before the rest of it becomes "unusable".  So if i want to install Ubuntu i have to delete either sda1 or sda2 but for all i know either action may kill Vista and STUPID ACER DIDN'T GIVE ME A RESTORE DISK!

So what do i do?


(sry for shouting)

---

### Post by Drakkor on 2008-08-24
Yeah, I have an Acer that's about 4 months old,and put Ubuntu Hardy on partition D:\, Grub will allow selection of OS on boot with Ubuntu default,(you can change this if you want)and Vista as the other OS. Hope this helps :)

---

### Post by Gonz_91 on 2008-08-24
My guess is that the safer way to do it is to delete the empty partition, use one part for ubuntu and merge the other part with the vista partition.

IMHO, though I might be as n00b as you...



Shame on Acer for not providing recovery discs

---

### Post by sandysandy on 2008-08-24
from live CD post output of [COLOR="Blue"]sudo fdisk -lu.[/COLOR] (from terminal)

regards

---

### Post by Drakkor on 2008-08-24
One observation with Acer that I don't care for is that their hdd seems to be proprietary,such as the "hidden" recovery partition,and the fact that I have found that it won't allow boot disks to work,such as I tried using Gparted,or even booting to an XP disk,it doesn't allow it. So I don't know
if wiping the whole drive,and starting over is possible,or just replacing the hdd altogether !

---

### Post by bodhi.zazen on 2008-08-24
> **Envergure said:**
> I want to install Ubuntu on a single-HDD laptop which already has Vista Home Premium 64bit on it.

When I open Vista's Explorer I see two drives (that is, two partitions):
C: (142 GB) - Has Vista and all my files
D: (139 GB) - Empty

However the Ubuntu installer shows four partitions:
/dev/sda1 (14 GB) - Maybe the restore partition
/dev/sda2 (153 GB)* - Same as C:
/dev/sda3 (149 GB)* - Same as D:
/dav/sda4 (4 GB) - Unknown (maybe *this* is the restore partition)

So here's the problem:  This HDD can only have four partitions before the rest of it becomes "unusable".  So if i want to install Ubuntu i have to delete either sda1 or sda2 but for all i know either action may kill Vista and STUPID ACER DIDN'T GIVE ME A RESTORE DISK!

So what do i do?


(sry for shouting)

You can have more then 4 partitions. You can only have 4 primary partitions.

Delete the empty partition, and make an extended partition. In the extended partition you can place logical partitions. You need a minimum of 2, one or ubuntu (root or /) and swap. Actually you can likely do without swap ...

Swap size should be RAM X2, max 1 GB, unless you wish to use hibernation, in which case swap = RAM.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by Envergure on 2008-08-24
OK, here's what i've learned so far:
-- sda1 is the restore partition
-- sda4 is an image of the Vista recover DVD

> **bodhi.zazen said:**
> Swap size should be RAM X2, max 1 GB, unless you wish to use hibernation, in which case swap = RAM.
I have 4G of RAM!

---

### Post by bodhi.zazen on 2008-08-24
> **Envergure said:**
> OK, here's what i've learned so far:
-- sda1 is the restore partition
-- sda4 is an image of the Vista recover DVD


I have 4G of RAM!

The more ram you have , the less you need swap.

If you are NOT going to use hibernation, your swap can likely be 512 Mb

If you ARE going to use hibernation, swap = 4.1 Gb

---

### Post by cjm5229 on 2008-08-24
Since you have in image of the recovery CD I would burn that to a DVD first. Then you could delete both that and sda3. make an extended Partition and then make about a 10GB / partition a 4GB Swap and the rest /home. or if you want to do it the easy way just install it in Windows using Wubi, you can install it to drive D. My Brother-In-Law has an Acer Aspire that I put Ubuntu on both ways. It was installed with Wubi in Vista until He got so loaded up with Viruses I had to reinstall Vista, Then I partitioned it for him , and installed it on it's own HDD. Then I created A Password in his Windows so he couldn't use it.:) No more Problems.:lolflag:

---

### Post by prosperysbeer on 2008-08-24
please read the fdocumentes on the following link
 [http://nerdstock.org/acer_vista_mandriva.en]("http://nerdstock.org/acer_vista_mandriva.en")

it will tell all you need to know about the acer dual boot install

---

