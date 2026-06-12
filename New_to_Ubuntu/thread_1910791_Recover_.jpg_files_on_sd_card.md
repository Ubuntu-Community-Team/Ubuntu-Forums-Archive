---
title: "Recover .jpg files on sd card"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by bob brazie on 2012-01-17
Ubuntu 11.10

Does anyone know of a utility that could recover deleated .jpg files off of a sd card?

Preferably an app that is not terminal based.

I did a google search but found nothing helpful and the Ubuntu software center is hard to search for something if the app name is not knwon.

Thanks in advance. Bob.

---

### Post by westie457 on 2012-01-17
Hi you could try this one, [http://www.r-tt.com/free_linux_recovery/](http://www.r-tt.com/free_linux_recovery/)

or if you still have access to Windows this is a good one, [http://www.piriform.com/recuva](http://www.piriform.com/recuva)

Both have a GUI.

---

### Post by bluexrider on 2012-01-17
> **bob brazie said:**
> Ubuntu 11.10

Does anyone know of a utility that could recover deleated .jpg files off of a sd card?

Preferably an app that is not terminal based.

I did a google search but found nothing helpful and the Ubuntu software center is hard to search for something if the app name is not knwon.

Thanks in advance. Bob.
use testdisk with photorec. Straight forward recovery.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[IMG]http://www.cgsecurity.org/photorec.png[/IMG]

---

### Post by rbc on 2012-01-17
+1 for photorec. It is, in fact, run from terminal, but after the slightest bit of reading, you’ll be able to get through it. And it can be installed from the software center

---

### Post by bob brazie on 2012-01-18
Installed but I can't figure out how to use the thing. No menues to point to the erased CD card.

---

### Post by rbc on 2012-01-18
With the SD card inserted, can you run this and post back:
sudo fdisk -l (That's a lower case L, not a number one)

And are you trying photorec, or one of westie457's suggestions?

---

### Post by bob brazie on 2012-01-18
[sudo] password for bob: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6d45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964603903   482300928   83  Linux
/dev/sda2       964605950   976771071     6082561    5  Extended
/dev/sda5       964605952   976771071     6082560   82  Linux swap / Solaris

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     1999871      999904+   6  FAT16
bob@bob-HP:~$

---

### Post by bob brazie on 2012-01-18
Thanks to everyone I tried Photorec. Figured it out through the on screen promps and recoverd the pictures.

Thanks to everyone again. Bob.

---

### Post by rbc on 2012-01-18
Good to hear of your success

---

