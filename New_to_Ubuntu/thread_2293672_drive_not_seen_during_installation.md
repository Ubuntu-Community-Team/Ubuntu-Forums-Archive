---
title: "drive not seen during installation"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by houndhen on 2015-09-06
Multibooting Window 7 64 bit and Linux. Haven't had much success installing Ubuntu based OSes. I have tried several including Ubuntu Mate. The latest OS that I am trying is Linux Lite. When I get to the screen that I am supposed to choose where to install, there are no drives showing. My drive is already partitioned.

I did a search and tried the solution [here]("http://ubuntuforums.org/showthread.php?t=1694750&page=8"). I was not able to find a setting to put my drive to 'Large". 

My CPU is 'Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz'
My Motherboard is - Dell Inc.  model 0Y958C revision	A00
my hard drive is - 500 GB SATA

Has anyone that has had this problem found a solution that might work for me?

---

### Post by yancek on 2015-09-06
You indicate your drive is already partitioned but not how many partitions you have?
Are you using MBR to boot?  If so, you are allowed 4 partitions.  Do you have free or unallocated space on the drive outside your windows partitions?
Boot the Linux Lite medium and go to the Desktop.  Do not click the install icon but rather open a terminal from the Menu and run the two separate commands below:

```
sudo fdisk -l
sudo parted -l
```

It is a Lower Case Letter L in each command.  Each command should output some information which you can then post here.  If you are new to this, you might take a look at the very detailed tutorial below.  It is Ubuntu but the installer should be pretty much the same.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by houndhen on 2015-09-07
> **yancek said:**
> You indicate your drive is already partitioned but not how many partitions you have?
Are you using MBR to boot?  If so, you are allowed 4 partitions.  Do you have free or unallocated space on the drive outside your windows partitions?
Boot the Linux Lite medium and go to the Desktop.  Do not click the install icon but rather open a terminal from the Menu and run the two separate commands below:

```
sudo fdisk -l
sudo parted -l
```

It is a Lower Case Letter L in each command.  Each command should output some information which you can then post here.  If you are new to this, you might take a look at the very detailed tutorial below.  It is Ubuntu but the installer should be pretty much the same.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
```
sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb9715f43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   212082687   105937920    7  HPFS/NTFS/exFAT
/dev/sda3       212082688   339230719    63574016    7  HPFS/NTFS/exFAT
/dev/sda4       339230720   976773119   318771200    5  Extended
/dev/sda5       339232768   370690047    15728640   82  Linux swap / Solaris
/dev/sda6       370692096   395857919    12582912   83  Linux
/dev/sda7       395859968   421025791    12582912   83  Linux
/dev/sda8       421027840   446193663    12582912   83  Linux
/dev/sda9       446195712   471361535    12582912   83  Linux
/dev/sda10      471363584   597192703    62914560   83  Linux
/dev/sda11      597200373   622374164    12586896   83  Linux
/dev/sda12      622374228   647548019    12586896   83  Linux

Disk /dev/sdb: 15.5 GB, 15514730496 bytes
255 heads, 63 sectors/track, 1886 cylinders, total 30302208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026557

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    30302207    15150080    c  W95 FAT32 (LBA)
```
```

sudo parted -l
Model: ATA HDS725050KLA360 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   109GB  108GB   primary   ntfs
 3      109GB   174GB  65.1GB  primary   ntfs
 4      174GB   500GB  326GB   extended
 5      174GB   190GB  16.1GB  logical   linux-swap(v1)
 6      190GB   203GB  12.9GB  logical   ext4
 7      203GB   216GB  12.9GB  logical   ext4
 8      216GB   228GB  12.9GB  logical   ext4
 9      228GB   241GB  12.9GB  logical   ext4
10      241GB   306GB  64.4GB  logical   ext4
11      306GB   319GB  12.9GB  logical   ext4
12      319GB   332GB  12.9GB  logical


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.5GB  15.5GB  primary  fat32        boot, lba
```

---

### Post by yancek on 2015-09-07
Well, fdisk and parted obviously show all the partitions so I'm not sure what the problem is.  Are you using the manual install method?  It is usually referred to as 'Something Else' in most Ubuntus.  I've seen several posts here with a similar problem but not sure what the solution was.

---

### Post by houndhen on 2015-09-07
I have seen this problem with other people and have posted about it before but have not found a solution. I have found that some Linux distros will install but it seems that they are not Ubuntu related. I have PCLOS, Sparky, and Makulu installed on my system but occasionally check around to see of someone has discovered a fix.

---

### Post by LostFarmer on 2015-09-07
this is a old post but it may be your problem,  do you know if you ever had the hdd in a raid setup?  [http://ubuntuforums.org/showthread.php?t=1508867&highlight=remove+raid+info](http://ubuntuforums.org/showthread.php?t=1508867&highlight=remove+raid+info)

---

### Post by houndhen on 2015-09-08
I don't know enough or understand enough about raid to even try it that I know of. But I will try the solution referenced by your link. Thanks

---

