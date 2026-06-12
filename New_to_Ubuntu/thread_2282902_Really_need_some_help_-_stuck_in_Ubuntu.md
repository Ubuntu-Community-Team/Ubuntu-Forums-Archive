---
title: "Really need some help - stuck in Ubuntu"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by oli8 on 2015-06-17
Hi guys

So I built a PC and my copy of Windows 7 hadn't arrived, so I downloaded and installed Ubuntu as the full OS from a dvd. Just so I had a way of using it.

I now have my copy of Windows 7 and when I try to install and get to "Set up is copying temporary files", I get the following message: "Windows cannot find a location to store temporary installation files. To install Windows, make sure that a partition on your boot disk has at least 890 megabytes (MB) of free space."

If someone could put me in the right direction I'd really appreciate it.

I'm not great with this kinda stuff so any help is good help.

Thanks

---

### Post by Duck_Dude on 2015-06-17
The problem with windows is that it likes to wipe entire drives and create partitions when doing a new installation.  It's highly recommended that you install windows before any linux distro.  There is more technical reasons behind it trying to install files in specific places (places that are currently occupied by your Ubuntu install) but regardless, Windows is a hog during the installation process.

If at all possible, I would highly recommend wiping the drive, installing Windows and then reinstalling Ubuntu (if you plan to keep it - which it sounds like you do).

The other option would be to use the Windows CD as a coaster.

---

### Post by cariboo on 2015-06-18
Windows needs a partition at the start of the first hard drive, plus space to install it. I'd suggest you install gparted, and use it to create the empty space you need to install windows at the start of the first hard drive.

---

### Post by mastablasta on 2015-06-18
or if you plan to remove Ubuntu - boot from live disk and use gparted to erase Ubuntu and format the disk (will erase all data) as NTFS. windows installer will handle the rest.

---

### Post by stalkingwolf on 2015-06-18
If memory serves me windows cannot read a linux partition.  So if you just create an ntfs partition at the beginning of your drive  you are likely to have windows tell you that your drive is bad (because it cant read part of the drive) and refuse to install.  Easiest is to wipe the drive and format it to ntfs.  then after install resize it.  One of the tricks windows used to use was to put a single file at the end of the drive to prevent resizing.  if theis is the case it must be moved before resizing.

---

### Post by cooleryawner on 2015-06-19
Use Gparted and split your Ubuntu partition into one for Ubuntu, one for windows, the windows partition must be in NTFS.

---

### Post by oldrocker99 on 2015-06-19
There is a Windows program called ext2fsd, which does allow Windows to read ext2 (and, I have discovered, ext4 as well) partitions.

For what that's worth.

---

### Post by buzzingrobot on 2015-06-21
> **oli8 said:**
> Hi guys

So I built a PC and my copy of Windows 7 hadn't arrived, so I downloaded and installed Ubuntu as the full OS from a dvd. Just so I had a way of using it.

I now have my copy of Windows 7 and when I try to install and get to "Set up is copying temporary files", I get the following message: "Windows cannot find a location to store temporary installation files. To install Windows, make sure that a partition on your boot disk has at least 890 megabytes (MB) of free space."

If someone could put me in the right direction I'd really appreciate it.

I'm not great with this kinda stuff so any help is good help.

Thanks

Windows can't find any empty partitions to use to install itself on, because there are none. Very likely because Ubuntu is using the entire disk.

The Windows installer enables you to delete partitions and then select one (which is typically a single partition encompassing the entire drive) as the 'New' partition on which to install it. 

If you want to retain Ubuntu and install Windows, then you will need to shrink the Ubuntu partitions to create room for a new Windows partition and then research how to successfully install and use Windows in dualboot mode.

---

