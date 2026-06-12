---
title: "Having Disk Partitioning Issues on Ubuntu 16.04.2"
date: 2017-07-10
forum: New to Ubuntu
---

### Post by hungrybrain727 on 2017-07-10
Hello all,

I was initially trying to create a disk partition to install Windows 8.1 and was unable to since the primary partition used practically all of the 1TB HDD I have. I resized it to 250GB and created a new partition for Windows 8.1 but when I boot the computer with the Windows 8.1 ISO USB (first priority in BIOS, HDD is second), I get the following:

error: attempt to read or write outside of partition.
Entering rescue mode...
grub rescue>

Any help is greatly appreciated. Thank you.

---

### Post by johndough2 on 2017-07-10
Hi

I am a little confused.

If you are booting USB instead of HDD to get Windows 8.1 then Grub need not be involved.

Is the USB containing W8.1 as an .iso or a fully expanded file system?

Then the type of partitions you have created, and their format and flags.

It is possible you have shrunk or deleted a partition that is listed as a specific size on the partition table and has not been updated with the reduced size.

So a little more on the partition table please, perhaps consider Gparted Live to try and help you.

[http://gparted.org/livecd.php](http://gparted.org/livecd.php)

---

### Post by hungrybrain727 on 2017-07-10
Yes, I was booting the USB because it contains the W8.1 .iso and before I tried to boot the USB, I created a partition for it and reduced the primary partition since it took practically a whole TB. I used GParted to do this as well.

---

### Post by oldfred on 2017-07-10
Again grub is not involved with booting Windows ISO on flash drive.
And then flash drive not a valid Windows bootable flash drive and it is reverting to your install on hard drive and that is now corrupted so grub is not booting your install.

Post screen shots from gparted as requested above.
Or:
sudo parted -l

Is your system UEFI or BIOS? Is Ubuntu installed in UEFI or BIOS boot mode?

---

### Post by yancek on 2017-07-10
Did you format the partition on which you want to install windows as ntfs?
Did you mark that partition as active in GParted?
How did you get the windows iso on the flash drive?  What software did you use to do this?  If you simply copied the windows iso to the flash I doubt very much that will work.

---

