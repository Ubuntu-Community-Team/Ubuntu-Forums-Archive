---
title: "Request for advice on reading fdisk output"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by timmy_1891 on 2011-11-06
Hi Guys and Gals,

Total Windows fanboy taking first steps with Ubuntu! I'm building a NAS server with hardware raid 1. 

I've got a 250gb boot drive partitioned and setup with installer - OK.
Also 2x 2TB drives configured as RAID 1 in BIOS - ?

I know that I have to create a partition and filesystem before mounting it, just a little confused by the fdisk output and what exactly I should be partitioning.

Here is the output 

```
timmy@ubuntu:~$ sudo fdisk -l
[sudo] password for timmy:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d3d8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 243.5 GB, 243500318720 bytes
255 heads, 63 sectors/track, 29603 cylinders, total 475586560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/pdc_djgcaeihhd: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906249984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_djgcaeihhd doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 6299 MB, 6299844608 bytes
255 heads, 63 sectors/track, 765 cylinders, total 12304384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
```By process of elimination I'm guessing that **/dev/mapper/pdc_djgcaeihhd** is what I need to partition and mount. Is that correct?

Also, I plan on using ext4 fs, but looking into xfs (not installed). I have a large number of video (~600GB) and audio content which made me think of it, but also millions of smaller files < 100kb. Sharing through samba, is it worth installing xfs or will using ext4 be ok?

Thanks for the advice

Timmy

---

### Post by apollothethird on 2011-11-06
> **timmy_1891 said:**
> Hi Guys and Gals,

Total Windows fanboy taking first steps with Ubuntu! I'm building a NAS server with hardware raid 1. 

I've got a 250gb boot drive partitioned and setup with installer - OK.
Also 2x 2TB drives configured as RAID 1 in BIOS - ?

I know that I have to create a partition and filesystem before mounting it, just a little confused by the fdisk output and what exactly I should be partitioning.

Here is the output 

```
timmy@ubuntu:~$ sudo fdisk -l
[sudo] password for timmy:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d3d8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 243.5 GB, 243500318720 bytes
255 heads, 63 sectors/track, 29603 cylinders, total 475586560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/pdc_djgcaeihhd: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders, total 3906249984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_djgcaeihhd doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 6299 MB, 6299844608 bytes
255 heads, 63 sectors/track, 765 cylinders, total 12304384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
```By process of elimination I'm guessing that **/dev/mapper/pdc_djgcaeihhd** is what I need to partition and mount. Is that correct?

Also, I plan on using ext4 fs, but looking into xfs (not installed). I have a large number of video (~600GB) and audio content which made me think of it, but also millions of smaller files < 100kb. Sharing through samba, is it worth installing xfs or will using ext4 be ok?

Thanks for the advice

Timmy

Someone will probably help you with the fdisk CLI which is most likely easy to use.  But in the meantime take a look at gparted.  If it's not installed you can install it with "sudo apt-get install gparted" or just type gparted in synaptic.

This gui partition manager might be easier to use.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by timmy_1891 on 2011-11-06
Hi thanks for the reply. I should have mentioned that I'm running Ubuntu 11.10 (GNU/Linux 3.0.0-12-server x86_64) without any GUI installed.

---

### Post by apollothethird on 2011-11-06
> **timmy_1891 said:**
> Hi thanks for the reply. I should have mentioned that I'm running Ubuntu 11.10 (GNU/Linux 3.0.0-12-server x86_64) without any GUI installed.

You're welcome, Timmy.  You might have already read the resources I'm going to link for you, but if you haven't this will be a good start.  Also once you test some of the commands and options provided it might have you to better verbalise more specifically where you're having problems.

InstallingANewHardDrive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

InstallationRAID1+LVM:
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by timmy_1891 on 2011-11-06
Thanks for the links, between those two and [http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System](http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System) I *think* I have it working! Now to setup all my shares and services!

Thanks for the help, I'm sure there will be a lot more questions to come ;)

---

