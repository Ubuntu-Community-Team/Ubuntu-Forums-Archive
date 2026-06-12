---
title: "Deep Format Help"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Syndacate on 2008-07-28
Hey,

I do some computer repair on the side.  Some guy gave me an external USB drive (with an ATA in it :crook:) and said that windows couldn't access it.  Upon loading it with Gparted I found that the disk's file system was damaged (it read the whole drive as unallocated space) - and my XP couldn't read it either.

So I mounted it in gparted but due to the lack of window manager in fluxbox I decided to do it in Ubuntu - So I did - and it still reads everything.

I'm backing the drive up now, my goal is to take all his stuff off of it, format, reformat it with ntfs-3g, and then dump his stuff back on it.  Here's where I run into problems.

It's copying to a different hard drive as I write this - but when it's done, how can I do a "deep" format - I'm talking total format, not just a quick format like in fdisk that takes 30 seconds and just writes 0's throughout the drive.  I'm not sure the difference in this format and a "deep" format like XP does b4 you install it - but I want to do a deep format due to the state of the drive.

How can I do that?  I realize I can just open fdisk and do a quick format in 30 seconds but that's not going to do anything, I'm looking for deep.

After that, I'm assuming like Gentoo, I can just type 
```
mke2fs -j /dev/hdd1
```
and it'll write ext3 to it, but I'm wondering:
A)  What would the command be to format to NTFS (I have NFS tools here)
B)  Is there **ANY** chance that Linux formatting a drive into NTFS would be somehow not as *compliant* for Windows machines as XP writing the file system in NTFS format?

Any input would be greatly appreciated.

PS:  How much should I charge for this...it's rather old system, 40Gb ATA drive, only 16 used.  I usually do whole computers, not sure how to charge for drives.


THANKS!

---

### Post by halitech on 2008-07-28
maybe instead of formating the drive, just use Gparted to remove any current partitions, connect it back to a windows machine and format it from there then copy the stuff back on?

far as charging, not sure, maybe a case of beer? :D

---

### Post by bodhi.zazen on 2008-07-28
If you really want to you can use dban :

[http://www.dban.org/](http://www.dban.org/)

Be careful with that thing.

From there you can either format it with gparted, the command line, or even from Windows, your choice ...

---

