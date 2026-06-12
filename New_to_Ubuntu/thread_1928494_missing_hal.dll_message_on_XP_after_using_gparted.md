---
title: "missing hal.dll message on XP after using gparted"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Spicywoo on 2012-02-20
Hello, everybody! 

As I consider myself a relative nincompoop, I do not wish to rush headlong from the frying pan into the fire! My problem seems simple, after a few days of poking around, trying to find a solution to a full partition, I decided to format an unallocated partition to ntfs, with a view to extending the windows xp to a more comfortable size.

Whatever I do, I do not want to risk losing my kubuntu os, whiich i love, and NEED although I do have Ubuntu installed on my Dell E4300. 
So my problem is a dual boot issue. Windows XP (sp 3) is on an extended partition, which probably explains why Windows doesn't recognize it. Does that sound right? I seem to remember reading that Windows must be installed on an active partition. So my question would be how do I change this ntfs partition, which is listed under an extended one (as sd9). 
I really must do a refresher of partitioning, esp. clean... 

I am currently burning a CDRW with Ubuntu secured remix, which looks like supplying at least info on my installation. Is this a good way forward for me or is there a simpler approach? Of course, I could simply re-install XP, but then I'm scared s....less of losing Kubuntu. There you have it.

---

### Post by ajgreeny on 2012-02-20
> **Spicywoo said:**
> I decided to format an unallocated partition to ntfs, with a view to extending the windows xp to a more comfortable size.

Whatever I do, I do not want to risk losing my kubuntu os, whiich i love, and NEED although I do have Ubuntu installed on my Dell E4300. 
So my problem is a dual boot issue. Windows XP (sp 3) is on an extended partition, which probably explains why Windows doesn't recognize it. Does that sound right? I seem to remember reading that Windows must be installed on an active partition. So my question would be how do I change this ntfs partition, which is listed under an extended one (as sd9). 
I really must do a refresher of partitioning, esp. clean... 

I am currently burning a CDRW with Ubuntu secured remix, which looks like supplying at least info on my installation. Is this a good way forward for me or is there a simpler approach? Of course, I could simply re-install XP, but then I'm scared s....less of losing Kubuntu. There you have it.
You are almost correct about windows partition requirements, but it is that it needs to be on a primary partition, not a logical partition inside an extended partition.  In theory XP *_can_* be made to boot on a logical partition, but it's a heck of a palaver and not worth the hassle.

It is probably easiest to reinstall windows XP on the space you have, but it may require a bit of partition activity, so can you show us a gparted screenshot (you can install it in your kubuntu OS if that's easiest).  Gparted is much the best for this purpose, particularly as it is the only partitioning application that I understand.  Using it yu should be able to either make a new ntfs partition, or just delete some space ready for a new ntfs partition that can be formatted when you install XP.

---

### Post by Bucky Ball on 2012-02-20
> **ajgreeny said:**
> You are almost correct about windows partition requirements, but it is that it needs to be on a primary partition, not a logical partition inside an extended partition.  In theory XP *_can_* be made to boot on a logical partition, but it's a heck of a palaver and not worth the hassle.



Think OP made a typo and XP is on a primary (or wouldn't be running without, as you say, previous amount of palaver).

Windows will not see the Ubuntu partition. Doesn't know what an EXT* partition is. Probably just says 'healthy' if it says anything at all about it. 

Do NOT alter Win partitions with Gparted. This is a recipe for disaster. Extended/shrink with Win software.

I would boot from the Ubuntu CD, 'Try Ubuntu', start the partition editor (Gparted) and have a good look round. You need to know exactly what is where and make a plan of action BEFORE attempting any resizing, creating of partitions. Post a screen shot from Gparted here and we can help.

Any haphazard approach risks demolitioning partitions and data in a nano-second with one click. I would commence the partitioning refresher now before making any more changes. ;)

---

### Post by ajgreeny on 2012-02-20
> **Bucky Ball said:**
> Think OP made a typo and XP is on a primary (or wouldn't be running without, as you say, previous amount of palaver).

Windows will not see the Ubuntu partition. Doesn't know what an EXT* partition is. Probably just says 'healthy' if it says anything at all about it. 

Do NOT alter Win partitions with Gparted. This is a recipe for disaster. Extended/shrink with Win software.

I would boot from the Ubuntu CD, 'Try Ubuntu', start the partition editor (Gparted) and have a good look round. You need to know exactly what is where and make a plan of action BEFORE attempting any resizing, creating of partitions. Post a screen shot from Gparted here and we can help.

Any haphazard approach risks demolitioning partitions and data in a nano-second with one click. I would commence the partitioning refresher now before making any more changes. ;)
Whilst I agree with most of what you say, I do not think there is a problem with XP of shrinking the XP main partition using gparted as long as you do not move the start point of the partition.  You can therefore successfully shrink tan XP partition by moving the right hand end to the left, but if you tried the opposite way, I agree that you would be in big trouble.

In fact, though I may not have made myself totally clear, I was not suggestion that the OP did anything other than look at the partitions on disk with gparted, and if he wished delete the XP partition before reinstalling.  What I wanted to do was see what is currently on disk, and the best way to do that with windows inability to see any ext partitions, is to run gparted and have a good look.

---

