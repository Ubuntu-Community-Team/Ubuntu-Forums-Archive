---
title: "Lost all my partition after installing Ubuntu 14.4 LTS"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by tarun3 on 2014-05-21
I am a complete newbie in linux.Yesterday i Installed Ubuntu 14.4 LTS with a bootable pendrive.Before that i had 3 partitions on my windows system.(C:),(D:) and (E:).During the Installation process i thought it would be same like windows where it formats the C drive and the linux gets installed in C.So i choosed the second option where it said erase disk and install ubuntu.Now i cannot find any of my drives.I have read hundreds of threads in this forum  and tons of youtube tutorial to retrieve it by testdisk but couldnot get a clue.When i use it with liveUSB it shows two storage systems.When i run (disks) from the application the result shows:

    Disk Drives:
    500gb Hard disk
    Hitachi HTS727550A9E364
    Size:500gb 
    Partitioning : Master Boot record
    Device: /dev/sda1
    Partition Type : Linux Bootable
    Contents : Ext2(version 1.0) not mounted

And below Disk Drives section there is Other Devices which has:

    491GB block device
    8.5gb block device
    967mb loop device

And when i run fdisk -l it shows:

    Disk /dev/sda: 500.1 GB, 500107862016 bytes
    255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00045999
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *        2048      499711      248832   83  Linux
    /dev/sda2          501758   976771071   488134657    5  Extended
    Partition 2 does not start on physical sector boundary.
    /dev/sda5          501760   976771071   488134656   8e  Linux LVM
    
    Disk /dev/mapper/ubuntu--vg-root: 491.3 GB, 491333353472 bytes
    255 heads, 63 sectors/track, 59734 cylinders, total 959635456 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
    
    Disk /dev/mapper/ubuntu--vg-swap_1: 8464 MB, 8464105472 bytes
    255 heads, 63 sectors/track, 1029 cylinders, total 16531456 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
    
    Disk /dev/sdb: 15.9 GB, 15925772288 bytes
    64 heads, 32 sectors/track, 15188 cylinders, total 31105024 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x20ac7dda
    
    This doesn't look like a partition table
    Probably you selected the wrong device.
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
    /dev/sdb2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
    /dev/sdb3   ?           0           0           0   6f  Unknown
    /dev/sdb4        50200576   974536369   462167897    0  Empty
    
    Partition table entries are not in disk order

How do i do it? My question might sound naive/stupid/duplicate (Please forgive me),but i have been trying this last 48 hours but couldnt get a clue how to do it.

Edit : I did a deeper search in testdisk and was able to see my lost partitions.But on changing the partition structure one partition shows structure bad.

---

### Post by tarun3 on 2014-05-21
I am here now..[http://imgur.com/vpa5ibD](http://imgur.com/vpa5ibD)

---

### Post by oldfred on 2014-05-21
You need to in testdisk see if you can restore the NTFS partitions. You will not get all data back. 
And if new Linux data overwrote too much then you may not get partition back and then have to use photorec. Photorec just scans drive for anything that looks like a file by extension. It cannot restore full file name and takes a very long time. Then you have a long time trying to determine file names. ( have used it to restore just a few files where backup was old). 

I know horse has left the barn, but better to have full backups before any major change. You should have full backups anyway as hard drives do totally fail usually at inconvenient times.

And drive means an entire hard drive. Only Windows interchanges partitions with drives. Your d: drive could be another hard drive or another partition on the same drive. In Linux it is sda, sdb are drives and sda1, sda2 or sdb1 are partitions on the drive.

---

### Post by tarun3 on 2014-05-21
Thanks for the advice sir..after the deep search two of the drives are shown..one partition structure was good other says bad structure..HERE>[http://imgur.com/k9NUfbe](http://imgur.com/k9NUfbe)
Help Please.And sorry i didnt had a backup and i hope a bit of horse gets back to the barn :).Thank you.

---

### Post by oldfred on 2014-05-21
Best to just copy files using testdisk for the one you see. 

Does it give errors since it is keeping the Linux partitions? At this point I would not restore any Linux partitions as you can easily re-install.

This has been suggested and in many threads they have confirmed it worked better for NTFS partitions.

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by tarun3 on 2014-05-21
If i would've got any clue to do what i want to by looking at hundreds of threads here..i wouldnt have posted a question in here sir..Anyway thanks for your time.

---

