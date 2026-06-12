---
title: "cant find my external hardrive"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ichiakahoshi on 2008-06-06
this may seem like a real simple question but i cant seem to find, let alone access my external hardrive.

im using ubuntu 8 with a KDE desktop and have plugged my external harddrive in through a USB port but cant find it?

help please, ive got all my loverly music on there and im sure my linux experience will be greatly enhanced with my tunes ^_^

---

### Post by malathion on 2008-06-06
Odds are your disk simply isn't mounted. In a terminal, do

```
sudo fdisk -l
```

That's l as in "list". Please post the results here.

---

### Post by ichiakahoshi on 2008-06-08
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   83  Linux
/dev/sda2           30018       30394     3028252+   5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1      121601   976760001    c  W95 FAT32 (LBA)

(i hope this helps)

thanks

---

### Post by malathion on 2008-07-25
Sorry for the late reply. It looks like you have two drives, sda and sdf, neither of which is partitioned. You will need to partition and format those drives before you can mount them in linux. Be careful to ensure that you back up all your data before messing around with partition editors!

---

### Post by Bucky Ball on 2008-07-25
Malathion ?

sda = sda1, sda2, sda5: all formatted and containing the appropriate linux partitions.
sda=1 x 250Gb hard drive, that is all. The partitions are normal.
sdf = 1 x terrabyte drive, containing sdf1, a 1 terrabyte fat32 partition by the looks of it.

Don't wipe or format anything, it is all present and correct!!!

As for mounting the USB drive, try this;

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Plug in the usb drive, then switch it on (as in don't boot with the drive plugged in an switched on for the purpose of this exercise). Doesn't automount? Odd. Good luck.

---

### Post by hogwartsnigel on 2008-07-25
Remember formatting will delete all your hard drive contents including your tunes. You shouldn't need to.
Click places, and open the media folder does the drive show there as an unmounted drive? If so right click and mount?

Hope that helps

Nigel

---

### Post by ichiakahoshi on 2008-07-26
thanks for all your advice, i re installed unbuntu on my PC and the external harddirve issue and a few others have sprted them selfes out. must of been a problem with the installation.

thanks again

---

### Post by hogwartsnigel on 2008-07-26
No worries, hope you have endless computing fun as you whistle a merry tune (along with the song playing and not instead of..) 
Nigel

---

