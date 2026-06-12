---
title: "Im having big problems just installing ubuntu 7.1"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by danishdart on 2008-04-22
Hello everyone! First post here. I'm trying to do a dual boot
but its not working Ill try and explain what I've done so far.
My setup:

MBO:A8N-E
CPU:3700+ A64 (939)
3 X HARD-DISK
1 IDE 80GB
1 SATA 250GB
1 SATA 250GB

My main problem I think has to do with the partitioning but I'm not sure.
First SATA drive is partitioned like this:
first 20GB for win-xp(ntfs)8GB free. Then 198GB for general storage(ntfs)43GB free. Then 13GB for Ubuntu(ext3) and a 2GB
swapfile for Ubuntu.
The other 2 drives are used for storage and contain 1 partition each, both ntfs.
After installing Ubuntu 7.1 , removing the cd and rebooting the computer it boots straight into Windows. No dual-boot menu!! Why?
This is the closest I have come to getting Ubuntu working other
than through the live-cd which works flawlessly by the way.

Previously I tried to install the 64 bit Ubuntu 8.04 and 7.1
but both were so buggy that they were impossible to install.
8.04 went straight to command-line. No graphic interface!
7.1 loaded to live but always crashed during installation.
Incidentally the ether-net network doesn't work either but I want
Ubuntu up and running before I start to play with that.
So what is going on here? Where am I going wrong?
Any help please?

---

### Post by Ub1476 on 2008-04-22
Are you sure Ubuntu installed into the same HDD as Windows? If you plan on installing Ubuntu on another HDD, read [here]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(installing)").

You can also install Ubuntu 8.04 Hardy Heron inside Windows, just mount the ISO from Windows. There is a slightly performance decrease, and suspend/hibernate does not work.

If you make 20GB free space available for Ubuntu, you can choose to use this option upon installing by selecting "Use free space available". This will automatically create boot /home and the filesystem under /, while swap is separated on another partition. 

You say it's buggy while using the live CD. Do you have little ram?

---

### Post by danishdart on 2008-04-23
> **Ub1476 said:**
> Are you sure Ubuntu installed into the same HDD as Windows? If you plan on installing Ubuntu on another HDD, read [here]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(installing)").

You can also install Ubuntu 8.04 Hardy Heron inside Windows, just mount the ISO from Windows. There is a slightly performance decrease, and suspend/hibernate does not work.

If you make 20GB free space available for Ubuntu, you can choose to use this option upon installing by selecting "Use free space available". This will automatically create boot /home and the file-system under /, while swap is separated on another partition. 

You say it's buggy while using the live CD. Do you have little ram?

Let me try and clarify here. When I said buggy using the live CD    
I was only referring to the 64 bit Ubuntu(7.1 or 8.04) 32 bit
 seems to be working fine(7.1), except it refuses to dual boot. 
I have  2GB of ram so that should be plenty.
I have installed Ubuntu to the same hard-drive as Windows and for
all I know it seems to be installed there.
I have used the manual partition method and created a 13Gb ext3 partition 
and 2GB swap-file at the end of the drive containing windows.
So I imagine it looks  something like this:

--Windows,20GB(NTFS)--Storage,198GB(NTFS)--Ubuntu,13GB(EXT3)--Ubuntu swap-file,2GB--

roughly.

I am not interested in running Ubuntu in anything other than a dual boot configuration and I don't think it is too much to ask
since I'm sure there are plenty of people before me that has done it and got it to work. So.. What am I missing here?

---

### Post by erlyrisa on 2008-04-23
If I rememebr correctly...

the default install (for me Gutsy) didn't ask me where I wanted to install grub and just defaulted.... (I have no idea where too!?)

You probably haven't installed grub....

Pop your CD back in, boot from it...

and at a terminal type

man grub

--learn how to use it, and where it is you would like to install.

Note: - If you haven't done this before you can reuin your setup - so make sure your willing to part with all the data on your hardrive before you go about doing this!!!.

---

### Post by Ub1476 on 2008-04-23
Yep, you probably forgot to install GRUB. You can do it through the live CD, or download [Super Grub]("http://www.supergrubdisk.org/"), which can boot every OS installed on the system, and install GRUB (or lilo).

And, Grub is usually installed into the MBR.

---

### Post by candtalan on 2008-04-23
> **danishdart said:**
> First SATA drive is partitioned like this:
first 20GB for win-xp(ntfs)8GB free. Then 198GB for general storage(ntfs)43GB free. Then 13GB for Ubuntu(ext3) and a 2GB
swapfile for Ubuntu.

Your mention of the partitions for ubuntu and its swap suggest  that you chose to do a manual install(?)
During the manual install, at the partition mount points display, iirc the mount point for / will be used to include the boot directory (right click at this early stage and edit partition, and view conventional options) and this will be used when booting because it is referenced from the MBR, which itself will have been changed to point to the /boot directory in your new linux system directory before the install process was completed.

I do not know if it is possible to avoid installing grub in the MBR, so I am curious that your machine does not apparently use the grub modified MBR when booting.

---

### Post by RobHK on 2008-04-23
> **Ub1476 said:**
> Yep, you probably forgot to install GRUB. You can do it through the live CD, or download [Super Grub]("http://www.supergrubdisk.org/"), which can boot every OS installed on the system, and install GRUB (or lilo).

And, Grub is usually installed into the MBR.

SuperGrub is definitely the way to go. It boots from the CD, so I'll log off and check it and then post what to do.

---

### Post by RobHK on 2008-04-23
> **RobHK said:**
> SuperGrub is definitely the way to go. It boots from the CD, so I'll log off and check it and then post what to do.
Download SuperGrub and burn it to a CD.

-Boot from the CD. The first screen disappears afte a few seconds and you get a menu.
- Select SuperGrub disk no help
- Select English
- Select Gnu/Linux
- Select Fix boot of Gnu/Linux

If you see more than one menu item try to identify the one for your latest installation. Select it and Enter. 


Remove the CD before rebooting and you should be in business.

---

### Post by redbob on 2008-04-23
I must consider that Space is not problem when you install Ubuntu. My brother has a laptop with just 20GB of HD and 512Mb RAM, we just booted up live CD, resized HD with GParted for 10Gb ext3 bootable Partition and 512Mb swap partitions. Maybe the cause of this issue is when you make a manual partition, you must tell to gparted: "my partition has to be bootable". A couple of times I did a manual setup of Ubuntu I forgot to make this option, so I had to run Recov Mode and install grub.

---

### Post by redbob on 2008-04-23
Hey, I liked to know about SuperGrub! Where I found it?
:lolflag:

---

### Post by danishdart on 2008-04-23
Yes I downloaded super grub disk and used it. Ubuntu loaded for the first time :) 
I did not permanently fix the MBR only loaded Ubuntu will try that tomorrow.. its late here. 
Thank you all for your help... 	:-D
P.S The network card still doesn't work
Goodnight

---

### Post by RobHK on 2008-04-23
> **redbob said:**
> Hey, I liked to know about SuperGrub! Where I found it?
:lolflag:

Google? ;) or [www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by redbob on 2008-04-23
Ok, guy! Thanks...

---

