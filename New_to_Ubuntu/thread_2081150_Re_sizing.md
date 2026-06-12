---
title: "Re sizing?"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by Yezinki on 2012-11-06
Hi there,

Can drive partitions be re sized on a Live/running Ubuntu......if yes how?

Thanks.

---

### Post by The Cog on 2012-11-06
Most types of filesystem cannot be re-sized while it is mounted. This rules out re-sizing the root partition, and re-sizing other (normally used) partitions can be inconvenient. 

However, btrfs and LVM can be re-sized online. I found a couple of links:
[http://www.funtoo.org/wiki/BTRFS_Fun](http://www.funtoo.org/wiki/BTRFS_Fun)
[http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/all-pages.html](http://www.tcpdump.com/kb/os/linux/lvm-resizing-guide/all-pages.html)

Edit: Oops, that refers to re-sizing the filesystem. That is different to re-sizing the partition, and I'm not sure if Linux will re-read the partition table without reboot.

---

### Post by zombifier25 on 2012-11-06
Only non-system partitions (e.g., not / or /home) can be resized on a running system. If you want to resize / or any system partitions, you need to do so on a live CD/USB. Grab a [GParted LiveCD](http://gparted.sourceforge.net/), burn it to a CD or install unetbootin and write it to a USB, boot from the CD/USB and you will be able to resize them.

Note that resizing partitions is a risky task, so make sure you're not interrupted during the process or there will be data loss.

---

### Post by westie457 on 2012-11-06
Hi. Ideally all drive partitioning is done in a Live Desktop using Gparted running from a CD or USB drive.
To resize a partition it must not be mounted ie. not being used by any programs.

To resize a partition select it then click 'Resize/Move'.

In the pop up window drag from the right hand end to the left. This is to keep the UUID so Grub and FSTAB can use it on the next reboot. Dragging from left to right will cause all sorts of problems.

To delete a partition select it and click on delete.

Any operation you choose will not complete until you click on 'Apply', also as a tip do not set multiple operations to run. In other words  work on one partition at a time. When one operation has finished go on to the next.

Any further questions just ask.

Thank you

---

### Post by Yezinki on 2012-11-06
Thanks The Cog, zombifier25, & westie457 for the very detailed explanation how to resize using GParted CD.

---

### Post by Bartender on 2012-11-06
One little thing to add.

I just repartitioned a drive a few minutes ago with a GParted LiveCD.  It's not the latest version, but pretty new.  

You can Create, Delete, Resize/Move, etc. most partitions by right-clicking on the "map" along the upper part of a GParted screen.  However, if you want to mess with an Extended partition you have to right-click on the line of text describing that partition below the map.  It's been this way forever.

Right-click on the text describing the extended partition and you get the window listing your options.

Right-click on the 'picture' of the extended partition and you get nothing.

Kinda weird but that's just the way it is.  Not a big deal once you know about it.

---

### Post by Yezinki on 2012-11-06
Thanks Bartender for your expert reply.

Another question related to this, can one create a Extended> Logical FAT32/NTFS partition on a Live Ubuntu running system using the GParted CD?

FAT32 or NTFS file system & not ext4 cause to create, store & restore backups.

---

