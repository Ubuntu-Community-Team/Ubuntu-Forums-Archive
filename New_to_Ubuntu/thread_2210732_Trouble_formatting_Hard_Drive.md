---
title: "Trouble formatting Hard Drive"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by Dave.B on 2014-03-12
Running from a USB as a live ( i donno if this is an issue)

I have a working Hard drive that i am having trouble formatting.
I am not sure what kind of machine that the HD came out of.
I have used fdisk to delete the Partitions that were on the HD
I then created a sincle partition on the HD making it the primary ( in fdisk)
i then wrote the changes and exited fdisk
I then tried to format the HD using "sudo mkfs -t ext3 /dev/sda1

I get the responce "/dev/sda1 is apparently in use by the system; will not make filesystem here!

im stuck please help

thank you

---

### Post by oldfred on 2014-03-12
Post this:
sudo fdisk -lu

Some systems promote flash drive to sda, others do not. So not sure which drive is hard drive?
I have not used command line for ages. 
What does gparted show?

Most use ext4 now, why ext3?

---

### Post by Dave.B on 2014-03-12
i did a sudo fdisk -lu 

this is what i got back

Disk /dev/sda: 251.0 GB, 251000193024 bytes
179 heads, 63 sectors/track, 43472 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47474747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   490234751   245116352   83  Linux

Disk /dev/mapper/.asr_092904         _74beb715_donotuse: 251.0 GB, 250999734272 bytes
179 heads, 63 sectors/track, 43472 cylinders, total 490233856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47474747

                                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/.asr_092904         _74beb715_donotuse1            2048   490234751   245116352   83  Linux

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    62530623    31265296    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

/dev/sda is the hard drive

---

### Post by Mark Phelps on 2014-03-12
I would suggest instead of using fdisk that you reboot from the USB stick and use GParted.  Looks like the disk may have previously contained some form of RAID.

If it were me, I would blank the disk using dban and then use gparted to do the repartitioning.

---

### Post by oldfred on 2014-03-12
A device mapper is either RAID or LVM.
You cannot use fdisk with either.

You must use RAID tools for RAID or LVM tools for LVM. I know neither.

---

### Post by sandyd on 2014-03-12
> **Dave.B said:**
> i did a sudo fdisk -lu 

this is what i got back

Disk /dev/sda: 251.0 GB, 251000193024 bytes
179 heads, 63 sectors/track, 43472 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47474747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   490234751   245116352   83  Linux

Disk /dev/mapper/.asr_092904         _74beb715_donotuse: 251.0 GB, 250999734272 bytes
179 heads, 63 sectors/track, 43472 cylinders, total 490233856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47474747

                                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/.asr_092904         _74beb715_donotuse1            2048   490234751   245116352   83  Linux

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    62530623    31265296    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

/dev/sda is the hard drive

Have you tried
a) Creating a new partition table (Gparted is nice for this and is installed by default on a LiveCD!)
b) Some Mobos have 'fakeraid' on it - if the drive has been configured with fakeraid, it will have to be removed
c) Rebooting - and checking fdisk again, ioctl may have not updated the partitions

---

