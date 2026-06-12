---
title: "Need help with drive partitions.."
date: 2008-09-25
forum: New to Ubuntu
---

### Post by steve04 on 2008-09-25
Hi, I just built a new computer this week and would like to triple boot XP, Vista, and a build of Linux (I want Ubuntu but for some reason my ASUS Mobo has a ton of trouble getting it to install so I may do another build).  The only drive I currently have partitioned is a 100 GB ntfs one with Windows XP installed on it.  I found this tutorial [http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452) to triple boot but I already have XP installed.. this shouldn't matter right?  I would assume it would be the same steps if I did a different build of Linux as well.  I have a program to go in and I can add other partitions.  I decided to make the Vista (ntfs) 150 GB, the Linux Home one 50 GB (ext3), and the Linux Swap 5 GB (linux-swap).  This leaves me with over 400 GB of space left.  I want to use this drive as storage for MP3s, pictures, etc... when I try to make a 5th partition, the program says I can't make any more.  It won't let me make the 5th one primary OR extended (the above 4 are primary).  Do I HAVE to give linux that 5 GB swap or is the 50 GB i used in the home directory enough?  Sorry if this sounds confusing but I'd basically like to Tri-boot and have an extra partition only for media (Fat32).  Any way to do this?  Thanks in advance!

---

### Post by mikewhatever on 2008-09-25
You can't have more then four primary partitions on one HDD. Delete one of them, presumably Ubuntu swap and create an extended one.
Swap is usually required, but 5GB is way too big, 1-2 GB should be enough.

---

### Post by steve04 on 2008-09-25
So my drives should look like this?

XP (ntfs) 100 GB [Primary] - Already made/installed
Vista (ntfs) 150 GB [Primary]
Linux Home (ext3) 50 GB [Primary]
Extra Drive (fat32) 450 GB [Extended]

I tried to do this and then make another extended for swap but it wouldn't let me do it.  When I am setting up Linux, what do I pick as my swap if I only have these 4 partitions?  Sorry if these are dumb questions but I don't know a lot about Linux setup, only that you need a "home" and "swap."

---

### Post by mikewhatever on 2008-09-25
Yes, kind of like this. I think XP and Vista must live on primary partitions, yet, it doesn't matter for Ubuntu. For example, I have all four, /, /home, swap and share on an extended partition, which means that they are all logical ones. Logical partitions live within the extended one, so that if you have just one extended partition, it's possible to create a number (don't know how many) of logical partitions in that space.

---

### Post by The Cog on 2008-09-25
I will assume you are really talking about just one drive, with many partitions. 

I guess you already have XP and Vista on partitions 1 and 2. I would suggest making partition 3 an extended partition filling the rest of the disk. You can put all your logical partitions inside that one. 

FYI, Linux numbers the partitions this way:
Primary partitions are sda1 - sda4, whether all 4 occupy any space or not. This way, the logical partitions are always sda5 upwards.

I suggest that you have sda5 and sda6 as two 20G or 25G ext3 partitions, for your linux root and another spare for trying out other distros or the next release. Then a few G of linux swap on sda7, then sda8 as /home filling the rest of the disk.

Don't use partition magic or any windows app to create the Linux partitions because they aren't always reliable - use gparted on the live CD or the partitioning dialog that you find in the installer.
I can't imagine you needing more than 20G for a Linux root partition, so I would sugget

---

