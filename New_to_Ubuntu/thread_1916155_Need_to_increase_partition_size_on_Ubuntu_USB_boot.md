---
title: "Need to increase partition size on Ubuntu USB boot stick"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by kn4hh on 2012-01-27
I am running Ubuntu on a bootable USB stick.  The system works fine.  However, I am getting messages saying that I do not have enough file space for additional apps.  I am using a 8gb stick and currently only 2gb are being used for the operating system.  I ran gparted and discovered that a significant amount of memory is still formatted as FAT32.  

I thought when I created the USB boot stick that the entire available memory would be dedicated to Linux.  Is it possible to make the rest of the USB stick available for Ubuntu file space for additional applications.

Many thanks for any assistance,
Bob Watson

---

### Post by Fernhill Linux Project on 2012-01-27
Gparted live will allow you to resize the partition.

---

### Post by sudodus on 2012-01-27
Are you running a persistent live system (with a casper-rw file for saving tweaks, applications and data files)? In that case, run Gparted from another drive (another CD or USB drive or from the internal HDD)! If you have FAT32, the maximum file size is 4GB, so you cannot really utilize more that approx. 5 GB for the 'boot partition'.

But there are better solutions. Have a look at the following recent thread

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1910412_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1910412")

---

### Post by mcduck on 2012-01-27
How did you create the stick? Is it an actual Ubuntu install, made to the USB drive, or is it a live system created using the Startup Disc Creator, Unetbootin or some similar tool?

If it's a normal install, then yu can simply resize the partitions as you wish using Gparted or some other partitioning tool. Keep in mind that you can't edit a partition youa re using, though, so you'll need to do it from another Ubuntu system or boot the machine with a live-CD or other live-USB.

...and if it's a live system created using Startup Disc Creator, then the whole stick is supposed to be still in FAT format, and the space where you can save your programs, settings and files is actually just a  single file on the stick ("casper-rw"). In this case the amount of available space for the persistence file would have been selected at the time you created the stick. This old thread might help you in resizing the file: [http://ubuntuforums.org/showthread.php?t=1147101]("http://ubuntuforums.org/showthread.php?t=1147101"). But keep in mind that FAT filesystem can't handle files larger than 4GB, so that's also the maximum size for the persistence file. If you need more space than that, you can create a new Ext2 partition on the drive and set it's label to "casper-rw" (you'll need to remove the casper-rw -file from the drive if you do this, and the space won't of course be usable from any Windows or Mac system any more)

---

### Post by C.S.Cameron on 2012-01-27
A casper-rw file in FAT32 has max size of 4GB.
A casper-rw partition formatted ext2 may have unlimited size.

Using gparted you can format the flash drive 1GB as FAT32 and 7GB as ext2, (or ext3 or ext4, as you wish). Name the ext partition casper-rw. The FAT partition must be first to be seen by Windows

Intall to the FAT partition using usb-creator.exe from the iso in Windows, (or Startup Disk Creator from the Live CD or ubuntu install).

Use minimum extra space, (128MB).
delete the casper-rw file, (NOT the casper folder).

If you want to use the flash drive to store or copy files from a Windows machine make the FAT partition larger.

If you want a seperate home partition make a third ext partition and name it home-rw.

---

