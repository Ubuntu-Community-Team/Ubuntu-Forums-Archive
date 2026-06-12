---
title: "Server hardware upgrade &amp; HD consolidation."
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Craig71 on 2013-06-16
Hi guys, thanks to some very helpful people on here, an idiot like me managed to install a home media server, and stream it around the house flawlessly. 

The time has come to upgrade the server though, mainly so I can get a smaller board & more discreet case.

My current setup has 2 hard drives - 1 80gb IDE with Ubuntu Server 12.04 on, and the other is a 2TB SATA drive with all my media on.

Would it be possible to install the server software on the SATA drive, just so I can have 1 drive to do everything?

I'm a little concerned that in attempting this, I'll mess up a system that is working fine, but I really would like to move to a smaller/quieter/less power hungry server.

Thanks for any input.

---

### Post by MidnightGrey on 2013-06-16
Yes you can install ubuntu server on the 2TB SATA, you will have to first create a seperate partition on the HD to place the new install on.
You can do this using the program gparted (which comes pre-installed in ubuntu). 
Please carefully read instructions on partitioning your HDs before proceding as mistakes could irreversably corrupt any data on said HD.

---

### Post by Craig71 on 2013-06-17
Cheers dude, I'll do a bit of googling. 

Unless, that is, someone can provide an idiot-proof guide to this?:o 
*EDIt*

I should add, that I am running this 'headless' and just access it through Putty on my Windows pc.

---

### Post by Cheesemill on 2013-06-17
First of all make sure you have a full backup of your system as any operation involving moving/resizing/creating partitions has an element of risk involved (you should always have a full back up anyway for when your hard drive fails).

You'll need to connect a monitor, keyboard and mouse to your server to edit your partitions as this can't be done from a running system via ssh, you'll need these connected to use the Live CD.

Boot from a Ubuntu Live CD and launch gparted, you can use this to shrink your current data partition to leave room for the new server installation. Ideally you would want to end up with the free space at the beginning of your drive as some motherboards have issues with booting an OS that lives on a partition at the end of the drive, however be prepared for shrinking a partition and moving it to the right can take a ***very*** long time. You can then use gparted to copy the existing root and swap partitions from the IDE drive to the newly created empty space. You *may* need to make edits to grub and fstab to allow the system to boot from the new drive, although this shouldn't be necessary.

If you need any help then post a screenshot of gparted so we can see exactly how your partitions are set up.

---

### Post by Craig71 on 2013-06-17
Thanks man, I'll give that a go & have a look.

Would it be possible to copy the settings for permissions onto the new server installation? As I did have a few teething problems setting these up!

---

### Post by Cheesemill on 2013-06-17
You should be able to get away with not having to reinstall at all and just copying your existing root and swap partitions onto the space you create on the data drive.

If for some reason this doesn't work and you do need to reinstall then you should be able to copy your settings over from the old IDE drive after installation.

---

### Post by Craig71 on 2013-06-17
Nice one, I'll dig the old monitor out of the loft & give it a go.:D

---

### Post by Craig71 on 2013-06-18
Hi guys, these are the screenshots from gparted. I'm guessing I resize the partition on dev/sdb, move it over to the right, and create a new one - big enough to copy everything over from dev/sda5?

[[IMG]http://img.photobucket.com/albums/v115/seymour71/20130618_195609_zps963cff9e.jpg[/IMG]]("http://smg.photobucket.com/user/seymour71/media/20130618_195609_zps963cff9e.jpg.html")
[[IMG]http://img.photobucket.com/albums/v115/seymour71/20130618_195617_zps5445312b.jpg[/IMG]](http://smg.photobucket.com/user/seymour71/media/20130618_195617_zps5445312b.jpg.html)

---

### Post by Craig71 on 2013-06-21
Wow, I'm really lost now. I've created some space on the 2tb drive, then I thought it's just be a case of copying & pasting the 80gb drive.
No. that won't work. It'll let me copy dev/sda/1, to the 2tb drive, but when i try to copy dev/sda2 & dev/sda5, the copy option is greyed out.
Please help me guys, I'm at a loss here!

---

