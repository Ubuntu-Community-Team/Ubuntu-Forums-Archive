---
title: "Duplicate files in /home"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by pdlethbridge on 2011-12-19
I keep getting doubles in all my home files in each OS and even duplicates within them.  taking up my cloud space

---

### Post by Bucky Ball on 2011-12-19
Not sure screenshot helps much. Which /home folder? You don't have a separate /home partition and therefore have a /home folder in each install (inside /).

Which install are you talking about???

---

### Post by pdlethbridge on 2011-12-19
I have a home folder in  each OS. I don't have a separate home partition. Should I

---

### Post by mörgæs on 2011-12-19
Changed the thread title to a more informative one.

---

### Post by pdlethbridge on 2011-12-19
I have been progressing though them and giving each one a good try The hard driv lises each one stating with Ubuntu 10.04

---

### Post by grahammechanical on 2011-12-19
At least you only have one swap partition. It is a bit on the big side at 29GB.

I have 4 versions of Ubuntu on my disk. Three of them have their own home folder on the partition. One of them (my main, working Ubuntu) has a /home partition.

Some on this forum would recommend having the same /home partition for each installation. I have not tried that. I do access the folders and files on the /home partition whenever I am using one of the other Ubuntus. 

Right now I am using an install of 12.04 development branch but I do work on documents stored on the /home folder of my 11.10 Ubuntu.

I only use Ubuntu One on the 11.10 Ubuntu. If you set up Ubuntu One or whatever on-line storage you have, on each install then of course you will have folders from each install taking up Cloud/storage space

Regards.
Regards.

---

### Post by pdlethbridge on 2011-12-20
It was easier to keep ever thing the same:P siz but I had it at 20 when I first started and to me it didn't matter if I lost 10 gigs. The OS are happy in there 30 gig partitions. Why rock the boat for 10 gigs:):)

---

### Post by N00b-un-2 on 2011-12-20
Why would you need 1,2,3.... what is that 6 installs of essentially the same exact OS on the same computer?  I suppose I could understand keeping an install of the latest LTS and then the latest normal release, but why on earth would you have two installs of the SAME OS!?  Ever heard of virtual box?
Also, what is up with having that 260+ GB of unpartitioned space at the end of the drive?  I might suggest since you are not running Windows on this computer that you may want to reformat the hard drive with a GUID partition table, because GPT supports up to 128 Primary partitions.
Another recommendation would be to use the large unpartitioned space as /home partition and configure ALL of your Ubuntu/Mint installs to use the same /home.  Or you could do what I do and just create "Documents, Downloads, Music, Movies & Pictures" folders on a large partition and symlink to those folders from your /home folder on each OS.  I have my computer set up this way running Xubuntu 11.10, Windows 7 Ult & Snow Leopard 10.6.8 and its nice to have all of my files in the same place across all OSes.

---

### Post by N00b-un-2 on 2011-12-20
or you could partition your drive as a single large extended partition and then have infinite logicals inside it.  However, should you choose to do that be aware that some OSes aside from Linux need to be installed on a Primary (I know Windows, Solaris and some BSDs do for sure)

---

### Post by pdlethbridge on 2011-12-20
The first partitions are all primary
dev/sda1 is Ubuntu 10.04LTS
dev/sda2 is Ubuntu 10.10
sda3 is swap file and sda4 is the extended partition may have what you think are duplicate Os's but are different  in what is on them. 11.04 is stock with unity but the next 11.04 has kde full loaded and the next one use gnome

---

### Post by N00b-un-2 on 2011-12-21
I still fail to see the point of running 4 of the SAME Linux distro on one machine.  You can have Gnome2, Gnome Shell, Unity, KDE, and any other desktop environment you want for that matter on one instance of Ubuntu.  You just pick which one you want to use at the GDM/KDM/LDM/SLIM/the options are practically limitless...
I have eyes, I can clearly see how you partitioned your hard drive, but it makes no sense to do what you've done and leave a massive unpartitioned segment of your drive and divide up the first half among redundant operating systems.  You essentially have the equivalent of Windows 2000, Windows XP, Windows Vista and Windows 7 installed on one hard drive, which just doesn't make any sense.  A single copy of XP or 7 would do everything you need so I just don't see the point.  Or if you're a mac guy, it's like have Tiger, Leopard, Snow Leopard and Lion installed on the same computer.

My sincere recommendation is to backup your files to an external HD and sort through the duplicates later, format your hard drive and start over with ONE copy of Ubuntu.

---

