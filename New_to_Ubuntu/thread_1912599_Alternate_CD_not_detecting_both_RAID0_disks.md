---
title: "Alternate CD not detecting both RAID0 disks"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Ali1331 on 2012-01-20
So I'm currently running Windows 7 on a RAID 0 array comprising 2x Samsung 1TB F3s. Array is built using Intel Matrix Storage Controller and it works fine. 

(Motherboard is Asus P5B-E)

Now I've tried several ways of installing ubuntu:


[LIST]
[*]Wubi:
[LIST]
[*]Windows Installer ran fine, however when it came to rebooting I received a "gave up waiting for root device" error and when I checked which device it was waiting for it had one stored in "dev/disks/by-uuid/" which didn't exist at all according to the shell it drops you to.
[*]I tried changing the root device from within Windows (editing the config file) but I either received the same error or a "disk not found" one
[/LIST]
 
[*]Bootable USB (Created using LinuxLive USB Creator)
[LIST]
[*]Simple problem here, although the USB is listed in the BIOS it didn't boot from the drive at all and simply passed to Windows.
[/LIST]
 
[*]And finally disk (this time using Alternate CD download as I think it has built-in raid drivers?)
[LIST]
[*]The disk loads up (yay!) and I manage to get through the early menus about keyboards and languages and when it detects the disks it says its found "One or more drives configured for Serial ATA raid" or something similar so that seems alright. The issue comes on the next screen when it asks if I want to create a partition (which I do, I freed up ~40gb of space from within Windows and left it as unassigned), however **it only shows one of the disks that comprise the RAID array**. It lists it as a single 1TB drive and there's no other drives at all.
[*]Ignoring ^ that, I tried to create a partition on the disk thinking it was just misreporting it and it only gives me the option to create an entire disk partition, which is obviously useless as I want to dual boot.
[*](Side note, when I stick in the USB from before it is listed on the drive menu, also I get additional menu options asking if I wish to set up a software RAID. Moving into the menu for softRAID it **asks which disks I want to put in it, and only lists the USB drive** (?!)
[/LIST]
 
[/LIST]
So I need to find a way to dual boot Ubuntu onto an already set up RAID 0 array with Windows 7 by creating a partition using the free space without compromising my Windows partition. 



**TL:DR**

[LIST]
[*]Dual boot Windows+Ubuntu, RAID 0 array
[*]Only half of array detected in Ubuntu installer, no option to set up softRAID
[*]Partition choices seem to only let me create an entire disk partition, removing my Windows install entirely.
[/LIST]
Any help is much appreciated!


Thanks for reading

---

### Post by bcbc on 2012-01-21
Maybe this will help:
[http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

---

