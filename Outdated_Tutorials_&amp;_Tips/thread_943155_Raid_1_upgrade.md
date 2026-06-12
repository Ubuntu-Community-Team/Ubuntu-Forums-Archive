---
title: "Raid 1 upgrade"
date: 2008-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by phillik747 on 2008-10-09
I have a server at home running Ubuntu server 8.04 and it is just a simple samba server.  I wanted to have the disks setup in a raid 1 format.  I just couldn't get my wife to approve the cost of a new hard drive at the time. The down side is I had a lot of data that I needed to get on the server and I wouldn't have to room at a later time to copy the data off of the server to setup raid 1.  I got to thinking about “pre” setting up  raid 1 so later when I purchased the new drive the raid would sync to it.  This is what I have discovered and I hope it will help you.

Note...You are dealing with changing your partition tables and file system.  Don't complain if you lose your data. I strongly suggest you test this out with some old small hard drives first before you put all your family photos on the line.  I tested it again and again to make sure I have the process down right.  Your mileage my very. 
Also this tutorial assumes you understand how to use fdisk, fstab, chmod, mkfs.* and what raid1 is.

_FDISK SETUP:_
First, start out with a blank HDD (sdb).  Then go into fdisk and create a partition and the partition type:

```
fdisk /dev/sdb
#new partition
n
#primary
p
#first partition
1
#the rest are defaults or whatever size you want
<enter>
<enter>
#change the partition type
t
fd
#write to disk
w
```

_MDADM SETUP:_

Now setup raid 1 setup with mdadm
```
mdadm --create /dev/md0 --level=1 --force --raid-devices=2 /dev/sdb1
```
Note the --force is to tell mdadm to make a raid out of one device (stupid huh, but there is an obvious reason)
Now we need to give /dev/md0 a file system.
```
mkfd.ext3 /dev/md0
```
Now you can mount /dev/md0 and copy what you want to it.  You can, at this point, put this in your fstab and use the file system until you obtain the second drive.  
```
mount /dev/md0 /media/storage
```
Don’t forget to chmod  your mount point. I also recommend creating a mdadm.conf file by doing the following:
```
$ cd /usr/share/mdadm
$ sudo ./mkconf force-generate
```



_VERIFICATION_

Below is some verification that raid 1 is setup and working.
```

$ sudo mdadm -Q -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Oct  5 15:47:18 2008
     Raid Level : raid1
     Array Size : 78148096 (74.53 GiB 80.02 GB)
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
   Raid Devices : 1
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Oct  5 15:50:39 2008
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 3381e0c3:2a31ad3d:1b037c4b:b4cc5ad2
         Events : 0.2

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0]
      78148096 blocks [1/1] [U]
      
unused devices: <none>
```

[U]ADDING THE SECOND DRIVE
[/U]
Now if you’re testing this out or when the time comes to put in that new drive shutdown the computer and install the new drive. Then when the pc comes back up you will have to give the new drive a partition like sdb.  

```
fdisk /dev/sdc
#new partition
n
#primary
p
#first partition
1
#the rest are defaults or whatever size you want
<enter>
<enter>
#change the partition type
t
fd
#write to disk
w
```

Now if you mounted your /dev/md0 or have it in your fstab you will want to umount it and stop mdadm
```
umount /dev/md0
mdadm --stop /dev/md0

```
Now we will add sdc (the new drive) to the raid set
```
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

***The  order is important here! Make sure you list the disk with the data on it first or  you will lose it all****

Now get some coffee or help answer some questions in the forum because the system is going to sync the drives and if you have a large drive (750GB) it could take 7+ hours. I had two 80Gb drives for testing and it took 40 mins at 27 MB/sec. Another trick is to make the partitions about 1GB for testing so you don't have to wait forever.

 You can watch the process with this command.
```
watch cat /proc/mdstat
```
<Ctrl c> to get out.

Now write a mdadm.conf file to /ect/mdadm/
```
cd /usr/share/mdadm
$ sudo ./mkconf force-generate

```
Once the drives are done syncing it's ready to be used. Just mount /dev/md0 or put it in fstab. 

_VERIFICATION_

Below are some results from MDADM.

```
$ sudo mdadm -Q -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Oct  8 11:56:15 2008
     Raid Level : raid1
     Array Size : 78148096 (74.53 GiB 80.02 GB)
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Oct  8 14:47:29 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 112d3440:8c99d678:333fcf05:95963365 
         Events : 0.1000

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1




$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc1[1] sdb1[0]
      78148096 blocks [2/2] [UU]
      
unused devices: <none>



$ sudo fdisk -l
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e840d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   fd  Linux raid autodetect

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc898c898

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   fd  Linux raid autodetect

Disk /dev/md0: 80.0 GB, 80023650304 bytes
2 heads, 4 sectors/track, 19537024 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


```

If you see any errors in this tutorial, please let me know. Thank you for taking the time to read my post!:guitar:

---

