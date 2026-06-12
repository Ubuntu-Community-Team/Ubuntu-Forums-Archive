---
title: "Problem detecting second hard drive"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by samsaptak on 2012-01-16
Hi,
I am a new user in Ubuntu 10.04LTS. I have two hard drives in my computer. The first one is partitioned and contains triple boot system :Ubuntu, win7 64 bit and win7 32 bit. (I have two windows as some scientific softwares I use are specific to the OS.)
The second hard drive is formatted as NTFS. Everything is working fine except I cannot access the second hard drive from Ubuntu where as the same can be accessed from win7s. I tried to look at earlier posts but could not solve the problem.
here is the output from  sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x273a6f17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       62974   505731072    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           62974       94630   254276608    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           94631      121601   216644557+   5  Extended
/dev/sda5           94631      120502   207816808+  83  Linux
/dev/sda6          120503      121601     8827686   82  Linux swap / Solaris

However, when i boot with G-parted I can see the second hard drive.
I am very confused now. Please help.

---

### Post by drdos2006 on 2012-01-16
The drives are loaded when /etc/fstab is run at boot time.

Open two terminals, in one type : ls -l /dev/disk/by-uuid
In two type : sudo cp /etc/fstab  /etc/fstab.backup
and : 
sudo gedit /etc/fstab

For your second drive (/dev/sdb) highlight the UUID from terminal one, right click and copy to the clipboard.
In /etc/fstab add at the bottom of the file:
## /dev/sdb
UUID=<Edit Paste here>  /media/sdb1  ntfs  defaults  0 1
Save Close, run : 
sudo mkdir /media/sdb1
mount -a

UUID is the UUID of the drive, ntfs is how the drive is formatted
0 1 is check the drive for faults periodically at boot time
mkdir makes a directory to load the drive
Mount -a mounts all the drives.

regards

---

### Post by sandyd on 2012-01-16
> **samsaptak said:**
> Hi,
I am a new user in Ubuntu 10.04LTS. I have two hard drives in my computer. The first one is partitioned and contains triple boot system :Ubuntu, win7 64 bit and win7 32 bit. (I have two windows as some scientific softwares I use are specific to the OS.)
The second hard drive is formatted as NTFS. Everything is working fine except I cannot access the second hard drive from Ubuntu where as the same can be accessed from win7s. I tried to look at earlier posts but could not solve the problem.
here is the output from  sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x273a6f17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       62974   505731072    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           62974       94630   254276608    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           94631      121601   216644557+   5  Extended
/dev/sda5           94631      120502   207816808+  83  Linux
/dev/sda6          120503      121601     8827686   82  Linux swap / Solaris

However, when i boot with G-parted I can see the second hard drive.
I am very confused now. Please help.
Post the output of
```

ls -l /dev/sd*
```

---

### Post by samsaptak on 2012-01-16
Thanks Sandyd, Here is the output for ls -l /dev/sd*

brw-rw---- 1 root disk 8, 0 2012-01-16 12:41 /dev/sda
brw-rw---- 1 root disk 8, 1 2012-01-16 12:41 /dev/sda1
brw-rw---- 1 root disk 8, 2 2012-01-16 12:41 /dev/sda2
brw-rw---- 1 root disk 8, 3 2012-01-16 12:41 /dev/sda3
brw-rw---- 1 root disk 8, 4 2012-01-16 12:41 /dev/sda4
brw-rw---- 1 root disk 8, 5 2012-01-16 12:41 /dev/sda5
brw-rw---- 1 root disk 8, 6 2012-01-16 12:41 /dev/sda6

---

### Post by samsaptak on 2012-01-16
Thanks drdos,
No uiud for the second hard drive.
Heres the output:
ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2012-01-16 12:41 2C86427F86424992 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-01-16 12:41 867245CC7245C1A3 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-01-16 12:41 8d413197-c634-49de-89bc-6d600ee4a465 -> ../../sda5
lrwxrwxrwx 1 root root 10 2012-01-16 12:41 9641d4a8-0203-41b2-a5be-d59120c60fd8 -> ../../sda6
lrwxrwxrwx 1 root root 10 2012-01-16 12:41 E69E23829E2349FF -> ../../sda3

---

### Post by drdos2006 on 2012-01-16
Can you see the drive when you run the System -> Administration -> Disk Utility ? ( Ubuntu 10.4 )

regards

---

### Post by sudodus on 2012-01-16
> **samsaptak said:**
> Hi,
... However, when i boot with G-parted I can see the second hard drive ...
I guess that you mean that you run a live linux session with gparted. What system were you using?

Please run it again and give more details of the result, for example that you ***attach  a screen dump of gparted showing the drive that is not detected by Ubuntu***. Is it possible to run a terminal in that system and try with the same commands as you have tried with Ubuntu?
```
sudo fdisk -lu
```

---

### Post by samsaptak on 2012-01-16
> **drdos2006 said:**
> Can you see the drive when you run the System -> Administration -> Disk Utility ? ( Ubuntu 10.4 )

regards

No.

---

### Post by samsaptak on 2012-01-16
> **sudodus said:**
> I guess that you mean that you run a live linux session with gparted. What system were you using?

Please run it again and give more details of the result, for example that you ***attach  a screen dump of gparted showing the drive that is not detected by Ubuntu***. Is it possible to run a terminal in that system and try with the same commands as you have tried with Ubuntu?
```
sudo fdisk -lu
```

Hi when I start gparted live, I could see both hard drives. I tried to run a terminal and tried the same commands. I could see both hard drives. But I do not know how to get a screen shot of that. Screen-shot icon did not work.

---

### Post by sudodus on 2012-01-17
> **samsaptak said:**
> Hi when I start gparted live, I could see both hard drives. I tried to run a terminal and tried the same commands. I could see both hard drives. But I do not know how to get a screen shot of that. Screen-shot icon did not work.
Good enough! I guess it is a linux system that is running Gparted, so the problem should be very specific to your Ubuntu system, maybe that Ubuntu 10.04 is too old to recognize a new partition table. Maybe information about the partition table is displayed by Windows or Gparted.

**What size is the disk and what kind of partition table is it, DOS (MBR) or _[B]**_GUID Partition Table (GPT)?[/B] Would the new Ubuntu version (11.10) recognize the drive? You can try downloading an iso file and making a CD or USB boot drive.

---

### Post by samsaptak on 2012-01-20
> **sudodus said:**
> Good enough! I guess it is a linux system that is running Gparted, so the problem should be very specific to your Ubuntu system, maybe that Ubuntu 10.04 is too old to recognize a new partition table. Maybe information about the partition table is displayed by Windows or Gparted.

**What size is the disk and what kind of partition table is it, DOS (MBR) or _[B]**_GUID Partition Table (GPT)?[/B] Would the new Ubuntu version (11.10) recognize the drive? You can try downloading an iso file and making a CD or USB boot drive.

Thank you so much...I have upgraded to 11.10 and the second hard drive is there.. thanks again

---

### Post by sudodus on 2012-01-20
> **samsaptak said:**
> Thank you so much...I have upgraded to 11.10 and the second hard drive is there.. thanks again
I'm glad it works for you now :-)
Please mark the thread SOLVED

---

