---
title: "Trouble formatting flash drive"
date: 2016-07-23
forum: New to Ubuntu
---

### Post by melissaanne on 2016-07-23
Hi!  Earlier today I formatted a flash drive and put Kubuntu 16.10 daily build on it without any issues.  Later I decided I wanted to install Kubuntu 16.04, so I downloaded an ISO and when I went to format my flash drive, I got an error saying "Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)"  I did some research and saw that using gparted solved their issues.  Formatting with GParted is successful, or so I thought... Ubuntu is detecting the file system on the flash drive as msdos now, when I formatted it to FAT32.  If I go back in to gparted, now I have flags on the partition saying filesystem doesn't exist. I error check the drive and it finds none. I'm kind of at a loss on where to go from here.  Any advice would be appreciated. Thanks! 

Currently running Ubuntu 16.04.01

---

### Post by ptn107 on 2016-07-23
You don't need to mess with filesystem types and formatting if you just write the image directly to the drive.

Install ddrescue:
```
apt install gddrescue
```

Plug in your usb drive.

Write the image to the drive:
```
ddrescue -d -D --force isofilename devicetarget
```

for example (since my usb is /dev/sdb)
```
ddrescue -d -D --force ubuntu-16.04.1-desktop-amd64.iso /dev/sdb
```

When it's done it will contain the right data on the right filesystem.

---

### Post by melissaanne on 2016-07-23
I think you are misunderstanding me.  I didn't mess with filesystem types or anything really.  I used start up disk creator and put Kubuntu 16.10 on my flash drive, just to see what it was about.  After testing it out, I logged back into Ubuntu and I needed to move a ton of files via my flash drive to a different computer, so I just did the right click - format and used the default settings to erase the Kubuntu stuff.  The formatting failed and I got the "Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0" error. I looked on other forums and it said that to fix this, just format using gparted.  I did use gparted, and it said it was successful, but when it refreshes the devices, it shows error flags. I didn't mess with anything, except hit format and left default settings everywhere. Then I decided I wanted to install Kubuntu 16.04 so I tried make a bootable flash drive.  Both unetbootin and start up disk creator failed because it couldn't format the drive. I appreciate the steps, I'll give it a shot. Thanks

---

### Post by melissaanne on 2016-07-23
I followed the steps above, and while it did force the ISO onto the flash drive. It is not bootable, nor is it being identified on anything like unetbootin or start up disk creator.  Gparted is still seeing the filesystem as unknown and when I click information it says 

Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sdb1 is missing

---

### Post by SeijiSensei on 2016-07-23
If you're comfortable at the command prompt, you might try using fdisk and mkfs.  Let's suppose the USB device appears as /dev/sdc.  First, run fdisk and see what it finds with "sudo fdisk /dev/sdc".  The program uses single-letter commands.  Start with "p" to "print" the partition table.  Is there a partition?  If so, try deleting it with "d".  (If there are multiple partitions, you need to use a number like "d 2", but on a USB drive there will probably be only one.)  Once you have no partitions on the device create a new one with "n" and follow the prompts to make one partition that spans the entire device.  Use "p" at the end to check your work, then "w" to write the new partition table to the device.

Now try writing a FAT32 filesystem into the partition with the command
```
sudo mkfs -t vfat /dev/sdc1
```

Any better?

---

### Post by sudodus on 2016-07-23
Welcome to the Ubuntu Forums :-)

I suggest that you use mkusb to wipe the ISO 9660 file system and create a partition table and file system on the pendrive. See these links (install mkusb and use the wipe menu),

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by The Cog on 2016-07-23
I find cfdisk easier to use than fdisk. You have to give it the device name, e.g.:
```
sudo cfdisk /dev/sdf
```

---

### Post by melissaanne on 2016-07-26
> **SeijiSensei said:**
> If you're comfortable at the command prompt, you might try using fdisk and mkfs.  Let's suppose the USB device appears as /dev/sdc.  First, run fdisk and see what it finds with "sudo fdisk /dev/sdc".  The program uses single-letter commands.  Start with "p" to "print" the partition table.  Is there a partition?  If so, try deleting it with "d".  (If there are multiple partitions, you need to use a number like "d 2", but on a USB drive there will probably be only one.)  Once you have no partitions on the device create a new one with "n" and follow the prompts to make one partition that spans the entire device.  Use "p" at the end to check your work, then "w" to write the new partition table to the device.

Now try writing a FAT32 filesystem into the partition with the command
```
sudo mkfs -t vfat /dev/sdc1
```

Any better?


Hi! Thanks for the reply.  I've been away due to a family emergency so sorry for the late response.  I did all this and it seems to have went fine.  I had no errors but my flash drive is still not mounting, and gparted is still saying the same thing 

Unable to detect file system! Possible reasons are:- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sdb1 is missing

Though now it is showing the right size and it has says sdb1 under partition instead of unknown.  Here is my results from what you told me to type in terminal: 
Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.




Command (m for help): p
Disk /dev/sdb: 7.6 GiB, 8103395328 bytes, 15826944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x151c43d8


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        2048 15826943 15824896  7.6G  7 HPFS/NTFS/exFAT


Command (m for help): d
Selected partition 1
Partition 1 has been deleted.


Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-15826943, default 2048): 2084
Last sector, +sectors or +size{K,M,G,T,P} (2084-15826943, default 15826943): 15826943


Created a new partition 1 of type 'Linux' and of size 7.6 GiB.


Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.


m@m-Satellite-L655:~$ sudo mkfs -t vfat /dev/sdb1
mkfs.fat 3.0.28 (2015-05-16)

---

### Post by melissaanne on 2016-07-26
> **The Cog said:**
> I find cfdisk easier to use than fdisk. You have to give it the device name, e.g.:
```
sudo cfdisk /dev/sdf
```


I did this, and got the same results as using fdisk above.  Everything seems to go fine, but it doesn't show up in fstab when I try to use terminal to mount it and gparted says file system unknown.   This is so random because it was working perfectly before I tried to format the flash drive using the right click method after having put Kubuntu on and booting into it.

---

### Post by sudodus on 2016-07-26
Sometimes you need to *reboot* for the kernel to recognize the change in the partition table.

There could also be some data left from before, and these data be be confusing for the tools that manage the drive. Such problems are often fixed by wiping the first megabyte (overwriting with zeros) before creating a new partition table and file system. (This is done automatically via the wipe menu of mkusb. See post #6.)

---

