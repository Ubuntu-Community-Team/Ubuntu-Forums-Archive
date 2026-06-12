---
title: "how do i increase my linux space and decrease windows space"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by hanzj on 2012-03-25
Hello, my computer came with Windows 7. I installed Linux on the same hard drive but a different partition (i think that's what it's called). The hard drive came with about 350 GB in total. Windows took about 75% and Linux took 25%. How can we reverse that? I want my Linux space to be 75%. I'm a newbie. Please give easy instructions. Thank you.

---

### Post by zombifier25 on 2012-03-25
Use GParted for resizing partitions. Its interface should be easy enough to use. Boot in your computer using a live Ubuntu CD (which contains GPrated) or GParted CD and launch GPrated, shrink the Windows partition and expand the Linux one.

---

### Post by kazztan0325 on 2012-03-25
Hi hanzj,

As for resizing partition, you would be able to refer to following thread.

**"[ubuntu] How to partition disk?"**
[http://ubuntuforums.org/showthread.php?t=1942710]("http://ubuntuforums.org/showthread.php?t=1942710")

Hope this helps.

---

### Post by hanzj on 2012-03-25
must i do the Gparted job while using LiveCD? Can't I do the Gparted job while logged into the Linux OS?

---

### Post by hanzj on 2012-03-25
kazztan, thanks for the link. it looks like that it answered my question about the need for using a live CD/usb to partition.

---

### Post by hanzj on 2012-03-25
rather than downloading 700 MB just to do the LIVE CD Gparted job, is there an OS with a smaller download size that also has gparted, and can do the job just as well as the Live Ubuntu CD/usb?

---

### Post by Deuce1912 on 2012-03-25
> **hanzj said:**
> rather than downloading 700 MB just to do the LIVE CD Gparted job, is there an OS with a smaller download size that also has gparted, and can do the job just as well as the Live Ubuntu CD/usb?

Certainly. Just use the gparted live CD.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Hope it helps.

- Deuce1912

---

### Post by kazztan0325 on 2012-03-25
I myself prefer to use **"Parted Magic"** for partitioning hard drive.

[http://partedmagic.com/doku.php]("http://partedmagic.com/doku.php")

---

### Post by hanzj on 2012-03-25
why do you prefer parted magic?

---

### Post by Mark Phelps on 2012-03-25
First of all, despite all the OTHER advice you're being given, it's generally a BAD idea to use GParted to shrink a Windows OS partition -- if that OS is Vista or Win7.  Both of those are very touchy about their OS filesystems being tampered with from outside -- which is what you're doing with GParted.

A much safer approach, presuming you want Vista/Win7 to be bootable when you're done, is to use the MS Windows Disk Management utility to do the shrinkage.

Which brings us to my second point -- that utility might not let you reverse the 75/25 ratio you have at present.  It prevents you from shrinking the MS Windows OS partition  too far to prevent damage to it.  So, it it doesn't let you shrink the 75 to 25, then take what it allows; otherwise, you risk damaging the filesystem.

---

### Post by hanzj on 2012-03-26
> **Mark Phelps said:**
> First of all, despite all the OTHER advice you're being given, it's generally a BAD idea to use GParted to shrink a Windows OS partition -- if that OS is Vista or Win7.  Both of those are very touchy about their OS filesystems being tampered with from outside -- which is what you're doing with GParted.

A much safer approach, presuming you want Vista/Win7 to be bootable when you're done, is to use the MS Windows Disk Management utility to do the shrinkage.
Thanks for this advice. I'll do as you say then, and use MS Windows Disk Management utility to do the shrinkage.

> **Mark Phelps said:**
> 
Which brings us to my second point -- that utility might not let you reverse the 75/25 ratio you have at present.  It prevents you from shrinking the MS Windows OS partition  too far to prevent damage to it.  So, it it doesn't let you shrink the 75 to 25, then take what it allows; otherwise, you risk damaging the filesystem.
Ok. I'll do whatever the Microsoft Disk Management utility can do. 

Thank you once again. 
If other people  could confirm this advice, I'd appreciate it.

---

### Post by kazztan0325 on 2012-03-26
> **Mark Phelps said:**
> A much safer approach, presuming you want Vista/Win7 to be bootable when you're done, is to use the MS Windows Disk Management utility to do the shrinkage.

Which brings us to my second point -- that utility might not let you reverse the 75/25 ratio you have at present.  It prevents you from shrinking the MS Windows OS partition  too far to prevent damage to it.  So, it it doesn't let you shrink the 75 to 25, then take what it allows; otherwise, you risk damaging the filesystem.

Mark Phelps pointed out the most important thing for us.
I should have awoken to that first, but I did't remember the important thing until Mark Phelps pointed it out..., sorry for my stupidity and thank you Mark Phelps for your indication.

@hanzj:
I think you might want to Defragment your Windows drive before shrinking Windows partition to get space for Ubuntu as much as possible even though Windows Disk Management utility would not let you shrink partition as you wanted.

By the way...
> **hanzj said:**
> why do you prefer parted magic?
Because 'GParted Live' adopts **Fluxbox** as its DE, 'Parted Magic' adopts **LXDE** as its DE, and LXDE is more easier to use for me than Fluxbox, this is the reason why I prefer 'Parted Magic'.

---

### Post by Vaphell on 2012-03-26
i'd add that anything partition related has non-zero chance of data loss so back up things you can't afford to lose (you should either way, the only copy of anything can be destroyed for whatever reason)
Windows V/7 has some internal/recovery crap scatered over the whole partition and these things are generally not movable by default with windows tools, thus limiting the 'compression' rate. I managed to compress windows things from minimum 100GB offered by win tools to desired 50 with some fancy standalone partitioning freeware (i don't recall the name, it was quite some time ago). Google for a program that can move pinned down windows files without damaging the system.
I made my orders in windows, restart, during boot phase partitioner kicked in, did its thing and the system worked afterwards - success! :-)

---

### Post by Zill on 2012-03-26
hanzj:  My advice, however you do it, is to *first* **backup all your data**.

Moving stuff around is potentially risky on any system so, if you value your data, backup everything you don't want to lose.

---

### Post by kazztan0325 on 2012-03-26
> **Vaphell said:**
> Windows V/7 has some internal/recovery crap scatered over the whole partition and these things are generally not movable by default with windows tools, thus limiting the 'compression' rate. I managed to compress windows things from minimum 100GB offered by win tools to desired 50 with some fancy standalone partitioning freeware (i don't recall the name, it was quite some time ago). Google for a program that can move pinned down windows files without damaging the system.
Hi Vaphell,
I guess maybe *"some fancy standalone partitioning freeware"* which you mentioned would be **"EaseUS Partition Master Home Edition"**..., do I guess correctly?
Here is the link to the website:
[http://www.partition-tool.com/]("http://www.partition-tool.com/")

---

### Post by Vaphell on 2012-03-26
hard to tell :) the laptop was not mine, i messaged the owner with a question wether the program is still installed by any chance and if that's the case - what's the name of it. Waiting for reply :)

---

### Post by hanzj on 2012-03-27
MarkPhelps,
I have defragmented the C: drive and used the Disk Management Utility to shrink C: Drive from 195 GB to 164 GB (there still is 35 GB of free space). There is now an allocated 32.59 GB partition. How do I make that partition joined to the Linux partition?

---

### Post by hanzj on 2012-03-27
> **Vaphell said:**
> 
Windows V/7 has some internal/recovery crap scatered over the whole partition and these things are generally not movable by default with windows tools, thus limiting the 'compression' rate. I managed to compress windows things from minimum 100GB offered by win tools to desired 50 with some fancy standalone partitioning freeware (i don't recall the name, it was quite some time ago). Google for a program that can move pinned down windows files without damaging the system.

I'd love to hear from MarkPhelps (who suggests using only the Disk Management utility) and others whether using this "fancy standalone partitioning freeware" is as good as or better than Disk Management for my system. If indeed the/a standalone partitioning freeware is just as good or better, I'd love to hear what is the best freeware. Is it EaseUS, as Kazztan0325 guessed?

---

### Post by Derek Karpinski on 2012-03-27
[http://ubuntuforums.org/showpost.php?p=11795449&postcount=10](http://ubuntuforums.org/showpost.php?p=11795449&postcount=10)

---

### Post by Mark Phelps on 2012-03-27
> **hanzj said:**
> MarkPhelps,
I have defragmented the C: drive and used the Disk Management Utility to shrink C: Drive from 195 GB to 164 GB (there still is 35 GB of free space). There is now an allocated 32.59 GB partition. How do I make that partition joined to the Linux partition?

There's no such thing as an unallocated partition.  There is unallocated space -- which is space on the drive that is not contained in any partitions.

You can't join partitions of different filesystems.

To enlarge an existing partition (e.g., your Ubuntu partition), boot from an Ubuntu Desktop CD, select Try Ubuntu, open Gnome Partition Editor -- and use it to expand the Ubuntu partition to enclose the recently unallocated space.  But that space must be immediately adjacent to the Ubuntu partition.  If there is a partition in between, you can not do the expansion because you can not go around partitions.

---

### Post by Mark Phelps on 2012-03-27
> **hanzj said:**
> I'd love to hear from MarkPhelps ...

OK, the FREE MS Windows partitioning tools available for download are:
1) EASEUS Partition Master
2) Partition Wizard
3) MiniTool Partition Wizard

These all work with current NTFS filesystems, and since they are MS Windows utilities, they will allow you to shrink Vista/Win7 OS partitions without problems -- just don't shrink them all the way.  Leave 20 -30 % free space.

---

### Post by troymius on 2012-03-27
I 100% agree with Mark to stay away from gparted in this case.

Just last week I wanted to shrink the Win partition on my new computer from 1Tb to 150Gb. Windows would not let me shrink more than ~50%. Then I came across a page that explained that "system restore" has to be disabled if I wanted to shrink it further. It worked very well and I did not have to use anything but Windows itself.

Here is one link that explains the steps 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
I am sure I used a different link but I can't find it now. Hopefully Win 7 and Vista are not too different in this.

---

### Post by kazztan0325 on 2012-03-27
> **hanzj said:**
> I'd love to hear from MarkPhelps (who suggests using only the Disk Management utility) and others whether using this "fancy standalone partitioning freeware" is as good as or better than Disk Management for my system. If indeed the/a standalone partitioning freeware is just as good or better, I'd love to hear what is the best freeware. Is it EaseUS, as Kazztan0325 guessed?

There is another partitioning tool for Windows:
**"PARAGON Partition Manager 11 Free Edition"**
[http://www.paragon-software.com/home/pm-express/]("http://www.paragon-software.com/home/pm-express/")

It is hard to say which is the best tool among them (including Mark Phelps introduced to us).

I would like to suggest hanzj:
Since you have already gotten free space, you might want to enlarge your Ubuntu partition following Mark Phelps advice first.
You would be able to try other partitioning tools for Windows later when you have time.

---

### Post by hanzj on 2012-03-28
> **Mark Phelps said:**
> There's no such thing as an unallocated partition.  There is unallocated space -- which is space on the drive that is not contained in any partitions.

You can't join partitions of different filesystems.

To enlarge an existing partition (e.g., your Ubuntu partition), boot from an Ubuntu Desktop CD, select Try Ubuntu, open Gnome Partition Editor -- and use it to expand the Ubuntu partition to enclose the recently unallocated space.  But that space must be immediately adjacent to the Ubuntu partition.  If there is a partition in between, you can not do the expansion because you can not go around partitions.

Mark,
You're right. When I wrote "32 allocated partition", I meant "unallocated space".

---

### Post by hanzj on 2012-03-28
Mark & Kazztan,
Thanks. Will download Gnome Partition Editor soon and try to make the 32 GB unallocated space a part of the 87 GB Linux partition. The 32 GB unallocated space and the 87 GB Linux partition are side by side, according to the Disk Management Utility in Windows.

---

### Post by hanzj on 2012-03-28
> **Mark Phelps said:**
> OK, the FREE MS Windows partitioning tools available for download are:
1) EASEUS Partition Master
2) Partition Wizard
3) MiniTool Partition Wizard

These all work with current NTFS filesystems, and since they are MS Windows utilities, they will allow you to shrink Vista/Win7 OS partitions without problems -- just don't shrink them all the way.  Leave 20 -30 % free space.
Which do you think is best? And why should there be 20 to 30 percent free space?

---

### Post by Mark Phelps on 2012-03-28
> **hanzj said:**
> Which do you think is best? And why should there be 20 to 30 percent free space?

I've used them all and it boils down to which screen interface you prefer to use (i.e., Look and Feel).

You need the free space because Windows needs free space in its OS partition to work properly.  If you shrink it all the way down, there's the risk it won't boot or if it will, a few boots later, it then won't boot.

---

### Post by Mark Phelps on 2012-03-28
> **hanzj said:**
> Mark & Kazztan,
Thanks. Will download Gnome Partition Editor soon and try to make the 32 GB unallocated space a part of the 87 GB Linux partition. The 32 GB unallocated space and the 87 GB Linux partition are side by side, according to the Disk Management Utility in Windows.


GParted should work fine ... but be aware that it is S...L...O...W.

It will run two passes -- the first checks the integrity of the file system and tests the operation.  So basically, it will take twice as long as you expect.  And do NOT interrupt it or power off the PC until it's done -- even if it takes HOURS!  That will leave you with a corrupted filesystem and possibly, no way to recover short of reinstallation.

---

### Post by hanzj on 2012-03-31
Just wondering. What happens if I try to reclaim (with Gparted) the unallocated space (that Windows Disk Management Utility freed up) while logged into my Linux partition/OS?

---

### Post by kazztan0325 on 2012-03-31
> **hanzj said:**
> What happens if I try to reclaim (with Gparted) the unallocated space (that Windows Disk Management Utility freed up) while logged into my Linux partition/OS?

**"Partitions that are in use cannot be modified. They are locked by the operating system that uses them."**
(quoted from [http://www.dedoimedo.com/computers/gparted.html#mozTocId661277]("http://www.dedoimedo.com/computers/gparted.html#mozTocId661277"))

---

### Post by hanzj on 2012-03-31
Yeah, the partition in question needs to be unmounted. And unmounting the partition you're currently in is probably practically the same as shutting off the computer.

---

### Post by hanzj on 2012-04-03
I was able to put Gparted Live onto USB. I booted off that USB drive. I then right-clicked  the unallocated space and chose "New", but then I got the error message:
> 
**It is not possible to create more than 4 primary partitions**
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

What should I do?
And let's say I didn't have 4 primary partitions. How do I join the unallocated space to the  /dev/sda5/ (Linux) partition?

---

### Post by kazztan0325 on 2012-04-03
> **hanzj said:**
> What should I do?
And let's say I didn't have 4 primary partitions. How do I join the unallocated space to the  /dev/sda5/ (Linux) partition?

You already have 4 primary partitions:
 - /dev/sda1 (Windows Boot Loader)
 - /dev/sda2 (Windows C drive)
 - /dev/sda4 (Extended partition)
 - /dev/sda3 (Recovery partition for Windows)

You have only to enlarge /dev/sda4 (Extended partition) and /dev/sda5 (Ubuntu partition) to achieve your aim.

Operate the following process:
1.  Right-Click on /dev/sda4 (Extended partition).
2.  Click Resize/Move on context menu.
3.  Resize/Move dialog will appear.
4.  Drag left edge of the partition toward left to make it maximum size.
5.  Click on Resize/Move button.
6.  Right-Click on /dev/sda5 (Ubuntu partition).
7.  Repeat the process 2. - 5.
8.  Click Apply button on toolbar.
9.  Just wait until GParted would complete resizing operation.

---

### Post by hanzj on 2012-04-04
thanks. After hours, Gparted finished its job. If there is any other partitioning/resizing tasks that would be good to do, please let me know. Attached is screenshot after reclaiming the unallocated space for Linux.

---

### Post by kazztan0325 on 2012-04-04
> **hanzj said:**
> thanks. After hours, Gparted finished its job. If there is any other partitioning/resizing tasks that would be good to do, please let me know.

You are welcome, hanzj!

I think you have no tasks that would be good to do, though you couldn't shrink Windows partition as you wanted at first.

If you have time, you may try other partitioning tools for windows to shrink windows partition a little more than now, however I am not sure how much space you would be able to get...

---

