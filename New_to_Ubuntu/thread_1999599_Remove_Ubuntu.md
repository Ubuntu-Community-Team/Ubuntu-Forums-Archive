---
title: "Remove Ubuntu"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by Simpleasy on 2012-06-08
Hi everyone, 

I want to install ubuntu, but I have a few questions to ask before I do so. 
I have already booted from USB to test Ubuntu out. But before I really want to install it, I want to be sure I can delete it, in case I like windows 7 more. After all, I can't really know what ubuntu is like if I only booted from usb. I want to use it for a few days, and then decide whether or not I want to keep using it.

And on top of that, I also have another question: 
When I booted from usb, I couldn't disable the touchpad of my laptop anymore. Normally I can disable it by pressing Fn + F1, but that didn't seem to work anymore... other shortcuts like Fn + F3 did work (volume) 
In case this information is relevant, I have a Sony Vaio VPCF22M1E.

---

### Post by wilee-nilee on 2012-06-08
> **Simpleasy said:**
> Hi everyone, 

I want to install ubuntu, but I have a few questions to ask before I do so. 
I have already booted from USB to test Ubuntu out. But before I really want to install it, I want to be sure I can delete it, in case I like windows 7 more. After all, I can't really know what ubuntu is like if I only booted from usb. I want to use it for a few days, and then decide whether or not I want to keep using it.

And on top of that, I also have another question: 
When I booted from usb, I couldn't disable the touchpad of my laptop anymore. Normally I can disable it by pressing Fn + F1, but that didn't seem to work anymore... other shortcuts like Fn + F3 did work (volume) 
In case this information is relevant, I have a Sony Vaio VPCF22M1E.

Make sure you make a recovery disc for windows for reloading its bootloader upon removing Ubuntu if you do, and do a full backup an image/clone of the windows as well, before installing Ubuntu.

These two things will save you from a whole lot of trouble.

---

### Post by NikTh on 2012-06-08
Hi , 

> **Simpleasy said:**
> Hi everyone, 

I want to install ubuntu, but I have a few questions to ask before I do so. 
I have already booted from USB to test Ubuntu out. But before I really want to install it, I want to be sure I can delete it, in case I like windows 7 more. After all, I can't really know what ubuntu is like if I only booted from usb. I want to use it for a few days, and then decide whether or not I want to keep using it. 
You can delete Ubuntu anytime you want. You have a lot of options to try it , but the best (IMO) its dual boot(regular installation) with windows. 
If you decide to delete it just boot from windows and from disk manager delete the partitions of Ubuntu. You must have a windows dvd cause will need to boot from there to repair your mbr (with windows bootloader) 
Don't forget to make a disk defrag before install Ubuntu alongside windows. 


> **Simpleasy said:**
> And on top of that, I also have another question: 
When I booted from usb, I couldn't disable the touchpad of my laptop anymore. Normally I can disable it by pressing Fn + F1, but that didn't seem to work anymore... other shortcuts like Fn + F3 did work (volume) 
In case this information is relevant, I have a Sony Vaio VPCF22M1E.
This problem can be fixed either with a parameter in grub , like noapic , nolapic , acpi_osi=Linux  or 
by runing the** syclient** command or something else. 
This problem its to small (IMO) to gets you back from install Ubuntu.

---

### Post by Mark Phelps on 2012-06-08
The "safest" way to try out Ubuntu is to do a Wubi installation.  That will NOT require you to mess with partitioning in any way and does not risk any damage to your Win7 install.  IF that works out such that all your hardware is detected and all your devices work, you can easily remove that just like any other Win7 app.

Once you decide that you DO want to have a dual-boot setup with Win7 and Ubuntu in separate partitions, read through the details below BEFORE you do that:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

