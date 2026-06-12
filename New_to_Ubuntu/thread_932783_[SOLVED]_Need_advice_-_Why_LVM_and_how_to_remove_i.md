---
title: "[SOLVED] Need advice - Why LVM and how to remove it?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by TeknoPhil on 2008-09-28
Hi,
Do I need LVM? I'm not sure why it's on my system (8.04 server).

While getting info on LVM, I need some advice:

I want to create another partition to install another distro (on my first hdd, sda) and I'm not sure if LVM will cause any problem...

here's my output of fdisk -l

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078723

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       38913   312319665    5  Extended
/dev/sda5              32       38913   312319633+  8e  Linux LVM

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
```

Thanks for your input...

---

### Post by Paqman on 2008-10-01
Normally LVM is used to create one big virtual volume out of several physical drives. It's not the default setup at all, but is an option during the install process (on the alternate CD I think?)

I've not got any experience with using it, so consider this a bump to get the attention of someone who has.

---

### Post by nhasian on 2008-10-01
dont you need LVM to encrypt the drive?

---

### Post by bodhi.zazen on 2008-10-01
LVM is quite powerful, but it is not necessary.

LVM is the default with some OS including Fedora and Centos/RHEL.

If you wish to install another OS it may be easier to simply partition your hard drive and then re-install both OS.

Assuming you have the space, It can be done with LVM, but this involves resizing your LVM partition which must be don manually and may not be easy.

The biggest issue is that LVM takes a physical partition (or physical volume) and divides them in "logical volumes". But there is often fragmentation of the LV across the PV, so before you can resize the physical volume you may need to move the logical volumes manually.

The easiest solution (with LVM) is to resize your ubutu LV and in the free space make a new LV to install into. The distro you will install will have to allow installation into a LVM (should be no problem with Fedora) and you will need to manually assign the partitions.

To give you an idea how to do this see :

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641") 

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

Live CD : [http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

    General Info :
        Setup : [http://www.netadmintools.com/art365.html](http://www.netadmintools.com/art365.html)
        Extend: [http://www.netadmintools.com/art366.html](http://www.netadmintools.com/art366.html)
        Shrink: [http://www.netadmintools.com/art367.html](http://www.netadmintools.com/art367.html)

---

### Post by TeknoPhil on 2008-10-04
Thanks a lot for your help!

---

