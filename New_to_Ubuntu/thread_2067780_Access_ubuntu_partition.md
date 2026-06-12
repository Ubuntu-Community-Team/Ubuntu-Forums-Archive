---
title: "Access ubuntu partition"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by ARDV on 2012-10-07
hello
i have 3 partitions on my drive: C-D-E
i've installed ubuntu on D/ubuntu
but now i can't access D files
is there any way to access them from ubuntu?
or i have to install ubuntu lonely in a partition

thanks in advance

---

### Post by raja.genupula on 2012-10-07
Hi

you have to tell us that how you have installed Ubuntu .

have you formatted your select drive >

what type of Ubuntu installation done , General or WUBI type ?

---

### Post by ARDV on 2012-10-07
> **raja.genupula said:**
> Hi

you have to tell us that how you have installed Ubuntu .

have you formatted your select drive >

what type of Ubuntu installation done , General or WUBI type ?

no, i didn't format it
i still can access my files from Windows7
i done a normal installation (booted from cd, then rebooted to win7 and installed ubuntu on: D/ubuntu)
now i have the choice between win7 and ubuntu in the booting

---

### Post by dodo3773 on 2012-10-07
If I understand this question correctly you want to be able to see files from your windows partition from inside ubuntu. In order to do that just make sure you have the correct drivers installed on the ubuntu side. Look in your software center for something called ntfs-3g or similar. The other way (accessing your ubuntu files from windows) is not really possible last time I checked because there are no ext4 drivers for windows.

---

### Post by NikTh on 2012-10-07
Hi , 

boot in Ubuntu and open a terminal with [Ctrl]+[Alt]+[t] keys combo . 

Then copy-paste from here to the terminal bellow commands , one at time and post back here the results* 

```
sudo fdisk -l 
sudo parted -l
``` 

*put the results between the brackets **[noparse]```
Here
```[/noparse]** , so can be readable. 

Thanks

---

### Post by Mark Phelps on 2012-10-07
> **ARDV said:**
> hello
i have 3 partitions on my drive: C-D-E
i've installed ubuntu on D/ubuntu
but now i can't access D files
is there any way to access them from ubuntu?
or i have to install ubuntu lonely in a partition

thanks in advance

This implies you installed from INSIDE Windows -- using something called Wubi.

The files on the "D" partition will be part of the Windows filesystem -- which you access from inside Ubuntu in the "/host" folder.

---

### Post by ARDV on 2012-10-08
> **NikTh said:**
> Hi , 

boot in Ubuntu and open a terminal with [Ctrl]+[Alt]+[t] keys combo . 

Then copy-paste from here to the terminal bellow commands , one at time and post back here the results* 

```
sudo fdisk -l 
sudo parted -l
``` 

*put the results between the brackets **[noparse]```
Here
```[/noparse]** , so can be readable. 

Thanks


the problem is that when i enter ubuntu, i can't see D partition, so i can't access files in it
and also i can't access ubuntu files from Windows


fdisk -l

```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   215867391   107830272    7  HPFS/NTFS/exFAT
/dev/sda3       215867392   850745343   317438976    7  HPFS/NTFS/exFAT
/dev/sda4       850745344  1465145343   307200000    7  HPFS/NTFS/exFAT

```


sudo parted -l
```
Model: ATA Hitachi HDT72107 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   111GB  110GB  primary  ntfs
 3      111GB   436GB  325GB  primary  ntfs
 4      436GB   750GB  315GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label          
```

---

### Post by NikTh on 2012-10-08
> **ARDV said:**
> the problem is that when i enter ubuntu, i can't see D partition, so i can't access files in it
and also i can't access ubuntu files from Windows
sudo parted -l
```
Model: ATA Hitachi HDT72107 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   111GB  110GB  primary  ntfs
 3      111GB   436GB  325GB  primary  ntfs
 4      436GB   750GB  315GB  primary  ntfs
```

From the results of above command 

**Mark Phelps** has right. You installed Ubuntu via Wubi (from inside Windows). Be aware that this is  a Virtual Installation (only for testing proposes). 

Follow this 
> **Mark Phelps said:**
> 
The files on the "D" partition will be part of the Windows filesystem --  which you access from inside Ubuntu in the "/host" folder.

Thanks

---

### Post by DuckHook on 2012-10-08
> the problem is that when i enter ubuntu, i can't see D partitionNaming a partition after a letter is a Microsoft DOS/Windows convention that does not exist in Linux. In Linux, everything is either a file or a directory. When the OS identifies a readable partition, it mounts it and creates a directory for it. I am not familiar with WUBI installs so I am out of my league here. However, other responders have pointed to a "/host" directory. You can find the path to this directory with the following command in a console:

```
find host -type d
```The list will likely be long and scroll for a long time. Cut off the list generation with ^C if desired.

---

### Post by newb85 on 2012-10-08
> **ARDV said:**
> no, i didn't format it
i still can access my files from Windows7
i done a normal installation (booted from cd, then rebooted to win7 and installed ubuntu on: D/ubuntu)
now i have the choice between win7 and ubuntu in the booting

FYI, What you described is not a "normal installation".  Normal installation is not done from within Windows.  What you described is a Wubi installation.

Edit: Oops! Overlooked Mark Phelps' post.

---

### Post by ARDV on 2012-10-08
so i just done a 'Wubi' installation :(
didn't know that.
now how can i go to normal installation? is there any way to 'transform it'?
or i have to install again?

---

### Post by NikTh on 2012-10-08
> **ARDV said:**
> now how can i go to normal installation? is there any way to 'transform it'?
or i have to install again?

Here is a way to transform it (migrate) : [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

I never used it , never tested it. 

Thanks

---

### Post by ARDV on 2012-10-08
> **NikTh said:**
> Here is a way to transform it (migrate) : [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

I never used it , never tested it. 

Thanks

do i have to put ubuntu in a pration 'alone' or i can put it in a folder inside a partition? (like: D:\ubuntu)

---

### Post by audiomick on 2012-10-08
> **ARDV said:**
> do i have to put ubuntu in a pration 'alone' or i can put it in a folder inside a partition? (like: D:\ubuntu)

Ubuntu has to have it's own partition. When you do a full install (as opposed to a Wubi install), you wont see letters as partition names. That is a windows naming practice. Linux systems use sda, sdb and so on for the drives, and the partitions on the drive are numbered. Your first partition on the first drive will be sda1. Existing windows partitions are also referred to by the Linux OS in the same way, so your sda1 may well be the existing windows partition.

Partitions sda1 to sda4 (or sdb, sdc and so on) are either Primary or extended partitions. A logical partition inside an extended partition will be sda5 and upwards if there are more than one.

You can put the entire Linux install on one partition. The directory system starts at / . Further down the tree (or up, if you prefer...) you will have things like /boot , /etc and a number of others. Particularly relevant is the /home folder. That is where your /home/user folder is created (where "user" is the name of the user(s) ). It is in fact possible to put every single folder on it's own partition, but not necessary. It is, however, worth thinking about putting your /home on a separate partition. If you do this, in the event of a re-install you can simply re-mount the old /home partition, thereby retaining your data and config files.

Unlike Windows, which can only be installed to a primary partition, Linux can also be installed on a logical partition.

---

### Post by ARDV on 2012-10-08
> **audiomick said:**
> Ubuntu has to have it's own partition. When you do a full install (as opposed to a Wubi install), you wont see letters as partition names. That is a windows naming practice. Linux systems use sda, sdb and so on for the drives, and the partitions on the drive are numbered. Your first partition on the first drive will be sda1. Existing windows partitions are also referred to by the Linux OS in the same way, so your sda1 may well be the existing windows partition.

Partitions sda1 to sda4 (or sdb, sdc and so on) are either Primary or extended partitions. A logical partition inside an extended partition will be sda5 and upwards if there are more than one.

You can put the entire Linux install on one partition. The directory system starts at / . Further down the tree (or up, if you prefer...) you will have things like /boot , /etc and a number of others. Particularly relevant is the /home folder. That is where your /home/user folder is created (where "user" is the name of the user(s) ). It is in fact possible to put every single folder on it's own partition, but not necessary. It is, however, worth thinking about putting your /home on a separate partition. If you do this, in the event of a re-install you can simply re-mount the old /home partition, thereby retaining your data and config files.

Unlike Windows, which can only be installed to a primary partition, Linux can also be installed on a logical partition.

Very helpful reply! thanks a lot!
so i'll download ubuntu 10.12 and install it permanently after making a new partition for it

---

### Post by will1982 on 2012-10-08
Ubuntu 10.12?

Hopefully you meant 12.10, or 10.10, as 10.12 doesn't exist :P

---

### Post by ARDV on 2012-10-08
> **will1982 said:**
> Ubuntu 10.12?

Hopefully you meant 12.10, or 10.10, as 10.12 doesn't exist :P

12.10 of course :)
cuz i download 12.04 the last time
and i prefer always using the last versions in everything, even they are beta :)

Edit: is this community better or askubuntu.com?
or there is some differences between theme?

---

### Post by newb85 on 2012-10-08
> **ARDV said:**
> Edit: is this community better or askubuntu.com?
or there is some differences between theme?

That's probably a subjective question, but I would say it depends on the topic.  The format of askubuntu.com seems (to me) to lend itself more to questions on casual use--questions that you would expect just one simple answer to address completely.

If you want more in-depth information, come here.

---

### Post by audiomick on 2012-10-08
> **ARDV said:**
> 12.10 of course :)
 is this community better or askubuntu.com?
or there is some differences between theme?

I don't know that it would be completely fair to say one or the other is better. That is probably a matter of personal taste as much as anything else. This forum has been around longer, as far as I know. There is a wealth of information here, and some really knowledgeable members. I would suggest keeping an eye on both and seeing which suits you better.

---

