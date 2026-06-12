---
title: "Partioning... how do I do this?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by onana on 2008-05-17
I have tried to partition my HDD with the partition editor built into Hardy. I have also tried partitioning with Knoppix, nothing seems to be working. This is the first time I have tried to do anything with partitioning, so I don't understand what I am doing.

I am trying to make a 10G separate partition so that I can back up my /home folder. I want to try a fresh install of Hardy to see if it will help fix my graphics problem. I really do not want to lose anything if possible. 

Thanks so much in advance to anyone who can help this poor lost soul :)

Oh yeah, maybe I should add that I am running Hardy on a Toshiba Satellite laptop.

---

### Post by volkswagner on 2008-05-17
What is the output of

```
sudo fdisk -l
```

---

### Post by Promaster91 on 2008-05-17
Try [this]("http://gparted.sourceforge.net/").

---

### Post by ladr0n on 2008-05-17
What filesystem type are you using?  It's odd that knoppix's partition editor didn't work.  
Anyway, try using the Parted Magic live cd to do your partitioning.  It uses a modified version of GParted, and I've always had a good experience with it.

---

### Post by onana on 2008-05-17
> **volkswagner said:**
> What is the output of

```
sudo fdisk -l
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32243224

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4700    37752718+  83  Linux
/dev/hda2            4701        4864     1317330    5  Extended
/dev/hda5            4701        4864     1317298+  82  Linux swap / Solaris

Disk /dev/sda: 1027 MB, 1027416576 bytes
16 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x8e1e92c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1991     1003305    e  W95 FAT16 (LBA)

---

### Post by volkswagner on 2008-05-17
It looks as though you have no windows partition.  You seem to have a 1Gig usb stick in.

If you are trying to install windows, you will need to shrink your current linux partition.  To do this is must be done from the live cd and unmount the drives.

---

### Post by onana on 2008-05-17
I do have a 1G USB drive in, but that is nowhere near the size I need.

I am not trying to install windows. All I want to do is create a separate partition so that I can back up my home folder.

---

### Post by onana on 2008-05-17
Ok, I was able to create my partition with the Parted Magic livecd (its wonderful, I love it!). 

But now I can't change permissions to use it and it won't work in root either. What do I do.

Did I do something wrong? Or did I miss something when I created the partition?

---

