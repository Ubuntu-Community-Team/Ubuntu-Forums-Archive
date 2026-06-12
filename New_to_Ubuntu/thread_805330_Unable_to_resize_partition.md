---
title: "Unable to resize partition?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by venicia on 2008-05-23
I have Ubuntu booted up on a LiveCD and am currently trying to resize the partition so I can install a dual-boot of WinXP onto the laptop. However..

[img]http://img372.imageshack.us/img372/961/partitionfz4.png[/img]

I am unable to resize the partition. At all. Even the windows to increase/decrease size are grayed out.

My current partitions:
/dev/hda1 (swap) 368 MB
/dev/hda2 (boot) 7 GB
/dev/hda3 48 GB

---

### Post by overdrank on 2008-05-23
HI and is that partition mounted? You will have to unmount to resize.

---

### Post by louieb on 2008-05-23
What file system is it formated with? (ext3 or NTFS or ...).
How much data does it have in it?

Post a screen shot of the main GParted window or or post the output of 
**sudo fdisk -l **(lower case L)

---

### Post by venicia on 2008-05-23
My laptop is currently shut off, lemme reboot it to get a screenshot.
It is not mounted, it's ext3, and there is nearly no data on it.

---

### Post by forrestcupp on 2008-05-23
Try doing it with the [GParted LiveCD](http://gparted-livecd.tuxfamily.org/).  That should work.

---

### Post by louieb on 2008-05-23
> **venicia said:**
> 
It is not mounted, it's ext3, and there is nearly no data on it.

Can think of a few reasons it would not resize, but a nearly empty ext3 partition isn't one of them.  Saw the GParted live CD is being maintained again. The version on it should be newer that the one on the live CD. 
or the latest version is in the system rescue cd. Lately I've been using VisParted (a fork of the GParted project) [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")

---

### Post by venicia on 2008-05-24
Ah, my bad. I got several of my laptops confused. The filesystem is jfs, not ext3.

---

### Post by louieb on 2008-05-24
Think your out of luck. according to the [feature page]("http://gparted.sourceforge.net/features.php") GParted can't shrink jfs.

---

### Post by venicia on 2008-05-24
Ahh. Well, that sucks. Guess I'll have to reformat it then.
Thanks for the help, even though it should have been blatantly obvious if I had looked at the documentation for GParted in the first place, haha.

---

