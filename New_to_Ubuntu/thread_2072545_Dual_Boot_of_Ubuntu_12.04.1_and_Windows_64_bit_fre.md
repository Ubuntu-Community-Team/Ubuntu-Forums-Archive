---
title: "Dual Boot of Ubuntu 12.04.1 and Windows 64 bit freezing"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by teekash on 2012-10-18
Goodmorning All, this is my first post ever on ubuntu forums:guitar: I am relatively new to Ubuntu, and still getting to know about it, i have a group called Ubuntu Gurus on Facebook.

Anyway i am struggling to dual boot a version of Ubuntu 12.04.1 64 bit, with my Windows 7 Ultimate 64 bit,wit a disc i got from a PC Format magazine. It just stalls in the middle of the install and i do not what to do:(

---

### Post by shreepads on 2012-10-18
Hmmmm try the original install ISO downloaded from ubuntu.com... You can also boot it via a USB pen drive (if your system supports boot from USB) instead of a CD...

If the regular download is a problem, try the torrents, they are a better option if your internet connectivity is not that great...

If your only option is that CD you got from the magazine (not a good idea IMHO) then on boot hit any key to enter the boot menu and choose the option to verify the install media. This will check if there are any errors in the boot CD provided by the magazine...

---

### Post by NikTh on 2012-10-18
> **shreepads said:**
> try the original install ISO downloaded from ubuntu.com... You can also boot it via a USB pen drive (if your system supports boot from USB) instead of a CD...

+1 

Download Ubuntu 12.04 from here: [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Unetbootin can be downloaded from here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You will need an empty USB-Flash 2GB. 

"Marry" all these together and try to install again.

Thanks

---

### Post by Mark Phelps on 2012-10-18
It may be stalling because, if your PC came with Win7 preinstalled, it might already have the maximum of 4 primary partitions assigned -- preventing the installer from creating any more.

BEFORE you press ahead with the dual-boot install, you should read the material below:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Cavsfan on 2012-10-18
+^^ good advice!

When you get your Ubuntu installed along side Windows and it's looking good you might want to check out my How to.

It has been converted into a wiki but, it just hasn't been linked to the How to yet.

Here is a direct link to the wiki:

[[COLOR=blue]_https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen_[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

You will want to start at 1.4 in the table of contents and it has some good examples of what the screen will look like.
It never needs modification even when a new kernel is installed.

Unless you want to change the font colors, background picture or add/delete an operating system.

---

