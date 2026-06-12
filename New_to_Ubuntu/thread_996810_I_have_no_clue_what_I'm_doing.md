---
title: "I have no clue what I'm doing"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by heymynameiseric on 2008-11-29
As the title says:

I have no idea what I'm doing.
I'm not necessarily compu-illiterate, just completely unfamiliar with linux as a whole.

Here is what I'm trying to do:
dual boot Windows Vista (pre-installed) and Ubuntu 8.10 and maybe, once all the drivers are available, OSX Leopard - but thats a different story entirely.

Here is my current setup:
Dell Studio 1735
Windows Vista Ultimate SP1
3gigs Ram
2.10Ghz
ATI mobility Radeon HD 3650
287GB HDD w/ 161 Gigs Available

My question is, how do I achieve my objective, and what if any drivers will I need to have everything function as it should...


Thanks again :-)

~Eric

---

### Post by PmDematagoda on 2008-11-29
From your hardware, you won't need to download and install drivers of your own. But for your ATi card, you can install them by going to System>Administration>Hardware Drivers.

---

### Post by lukjad on 2008-11-29
This [link]("http://www.psychocats.net/ubuntu/") contains a **very** good  site that should guide you through the downloading of the CD and the installation. configuration, etc. It sure helped me through a few jams.

---

### Post by MasterSander on 2008-11-29
Good luck with installing mac os x86 btw, I managed to do it before on mine because my hardware matches a lot of macs. It didn't work perfectly but I was able to boot.

---

### Post by heymynameiseric on 2008-11-29
Werd! thanks for your quick responses!!

hopefully, the next message from me will be "Got linux working!!"

---

### Post by mkvnmtr on 2008-11-29
Installing Ubuntu is a snap but the Mac os might be a problem. I would think that a virtual install would be easier. Probably in a virtual install you can get everything to work.

---

### Post by heymynameiseric on 2008-11-29
> **lukjad007 said:**
> This [link]("http://www.psychocats.net/ubuntu/") contains a **very** good  site that should guide you through the downloading of the CD and the installation. configuration, etc. It sure helped me through a few jams.
I'm reading the Tutorial right now, only problem is, the partitioner in 8.10 DOES NOT give me the option to do a guided partition without erasing my vista partition BOOOOOOOOOOO!!!!

Any advise?

---

### Post by lukjad on 2008-11-29
Have you tried using Gparted on the Live CD (System->Administration->Gparted) to resize the drive and then using the guided partitioning to choose the space you carved out? Also, before resizing the partition, make sure to defrag your drive in Vista, twice if you can.

---

### Post by heymynameiseric on 2008-11-29
Ok I see it, but I have no idea what to do with it.

It Shows several partitions:
10Gb Recovery (thanks dell)
298 gb NTFS partition (I'm thinking thats where Vista Lives)
149.01 MB FAT16 (no idea)

What should I change/chop up in order to have enough space for Ubuntu and Vista to cohabitate? I was thinking I could format the NTFS partition to FAT32, then allocate 12 gigs for the linux system and boot files to live in...

does this sound like a good idea?

---

### Post by Lupusceleri on 2008-11-29
From what I understood in other threads, I doubt that making your **whole** HD FAT32 is a good idea (or will work at all).

You're probably best off making partitions.

So, because messing around with partitions potentially has a chance to kill all data on your harddrive, make sure you backed up stuff you don't want to lose.

As lukjad007 said, use GParted from the Ubuntu LiveCD (which is by the way also the installation CD, just pick the "try ubuntu without changes to your system" option rather than "install ubuntu"). Defragmenting your Vista harddrive a few times before you start sounds like a great idea as well.

I'd say: leave the 10GB Recovery alone (after all, who knows, you might want to recover later on! :P ). Also you never know what vital stuff is on the FAT16 partition, so leave that alone too. The 298 GB NTFS partition is indeed very likely where Vista lives.

Use the Resize/Move button in GParted to shrink your Vista partition.. to be safe on diskspace I'd say make sure to shrink the Vista partition by at least 40 GB (40960 MB). More never hurts, but keep in mind Vista needs space too. Personally I'd go for at least 60 GB, but that's your choice. I would keep the Vista partition on the beginning, and start the unallocated space right behind the Vista partition. **Click on apply now, or no change will be made at all!!**

Reboot the computer from the CD, this time hit install ubuntu, when it asks where to install ubuntu, tell the installer to **put ubuntu in the largest free space**. Clickity click through the questions and wait a bit, and everything should be alright. GRUB should be configured to see your other OS, so you can select Vista (or Ubuntu) on bootup. It's also possible for Vista to be the default boot-after-x-seconds OS, but for that you'll have to change some more advanced stuff.

Hope this helped.

---

### Post by caljohnsmith on 2008-11-29
Just a word of warning: if you use Ubuntu's gparted partition editor to resize Vista, it usually temporarily breaks Vista until you use a Vista Install/Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table, but gparted knows nothing about updating Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Install/Recovery CD.

So the bottom line is try to use Vista's "Disk Management" tool to resize the Vista partition to make room for your Ubuntu partitions. If you right-click "my computer" in Windows explorer, I think you can find the disk management tool there. I would recommend trying that first, and only if that doesn't work to shrink Vista's partition (which sometimes can happen), then you don't have much choice but to use gparted and then fix Vista afterwards. Let me know how it goes. :)

---

### Post by Lupusceleri on 2008-11-30
Yep Disk Management can be found by R-clicking on "My Computer" and then selecting Manage. From there, there's the Disk Management menu (in the left bar).

---

