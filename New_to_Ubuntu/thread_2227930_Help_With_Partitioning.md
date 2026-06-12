---
title: "Help With Partitioning"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by dbarnowski on 2014-06-04
I would like to try Ubuntu 14.04 LTS. When I try to install it along with windows 7 I cant select my internal hard drive. I have a 500 Gig drive and i'd like a partion with 100 gigs to start out with. I think the swap has to be something like twice the ram, my machine has 4 gigs. I'd like to dual boot either windows or Ubuntu. Can someone please provide me with screen shots to do this. 

Thank-You,
Doug

---

### Post by marbew on 2014-06-04
hei try with this [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

---

### Post by LastDino on 2014-06-05
You don't need swap that big, for you it is more than enough to keep in between 2 to 4 GB max.

Also, easiest way would be to create 100 (min of 30 GB) GB of free space from  your existing drive by windows partitioning tool. 

Then you can proceed with ''something else'' instead of install alongside.

---

### Post by fantab on 2014-06-05
> **dbarnowski said:**
> I would like to try Ubuntu 14.04 LTS. When I try to install it along with windows 7 I cant select my internal hard drive. I have a 500 Gig drive and i'd like a partion with 100 gigs to start out with. I think the swap has to be something like twice the ram, my machine has 4 gigs. I'd like to dual boot either windows or Ubuntu. Can someone please provide me with screen shots to do this. 


Post more details about your machine's hardware, CPU RAM and Graphics card, etc.
SWAP twice the size of RAM is an outdated concept. It is a hangover from the days when RAM used be quite less than what it is today.
2-4GB of swap is plenty. However if you like to hibernate your PC then you will need SWAP size equal to more than your RAM in Gib and not GB.

First of all boot Ubuntu DVD/USB Live and 'Try Ubuntu (without installing)". Open Terminal [ctrl+alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

Did you install Windows yourself or was it preinstalled?

---

### Post by dbarnowski on 2014-06-05
Win 7 Ultimate 64-bit
ASUS F1A75-M PRO R2.0
AMD A8 3850
4 Gigs G.Skill Ripjaws DDR3-1866

Installed myself

---

### Post by fantab on 2014-06-05
> **fantab said:**
> ...
First of all boot Ubuntu DVD/USB Live and 'Try Ubuntu (without installing)". Open Terminal [ctrl+alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```


Please post the HDD information by sharing the output asked earlier.

---

### Post by dbarnowski on 2014-06-06
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5003AZEX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   500GB  500GB  primary  ntfs


Model: Initio WD5000AAKB-00H8A (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005f7b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   976771071   488282112    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e8283e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976767686   488382819+   7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

---

### Post by fantab on 2014-06-06
You have not created a Linux partition. Ubuntu or Linux will not install to a NTFS partition.
Either create a Linux Partition and install ubuntu manually to it or make some 'unallocated space' for the Ubuntu installer to work with.

Use only Windows Disk management tools to manage NTFS partitions for best results and only Linux tools to manage linux partitions.

---

### Post by 3rdalbum on 2014-06-06
What are the options you are choosing in the installer? You don't need to create the partitions first, but you should try to use the "side-by-side" option in the installer, not the Something Else option, until you know what you are doing on Linux.

---

### Post by oldfred on 2014-06-06
Since you have two drives, there are some advantages to having Windows on one drive, and Ubuntu on the other drive. You still have the same total space either way.

But with two drives you have to either unplug the Windows drive to make sure parts of Ubuntu install are not on it, or use Something Else and manually format, mount and configure all your partitions. And then it is important to choose to install grub2's boot loader into the Ubuntu drive not the Windows drive, on the partitioning screen.
But as fantab suggests you do need to know or learn about partitions.

Default install is just / (root) formatted as ext4 of at least 10GB to 25GB if you have a separate /home or plan on storing most of your data in your NTFS data partitions for sharing with Windows. Default install does some strange things on sizing swap, but whatever it selects will work unless you give too little space for total install.
The advantage of Something Else or manual install is you get to choose sizes and can add additional partitions like /home if desired. 

If you shrink your NTFS data partition on your second drive and unplug Windows drive then you can just do the auto install. If if a NTFS data only partition best to use Windows to shrink it and run chkdsk on it immediately afterwards.

And if course good backups are essential. Any major system change can have unexpected things happen.

       Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by dbarnowski on 2014-06-06
I cant unplug a drive the windows one is internal, while the second is external.

---

### Post by oldfred on 2014-06-06
Install to internal will be faster, but many do install to an external drive. USB port is not as fast as SATA, but if you have a fair amount of RAM once an app is loaded it is just as fast.

---

### Post by pfeiffep on 2014-06-06
Consider using BIOS to disable the internal HDD which should produce similar peace of mind as disconnecting

---

### Post by dbarnowski on 2014-06-25
Thanks for the help guys I really appreciate it, reading this thread and the tutorial here multiple times I was able to make the four partions with ease, [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) . I have another question. Should I use the default settings for the software updates? I saw a thread but I can't find it so I don't know which ones to use or not for security purposes.

---

### Post by LastDino on 2014-06-25
You can make sure that pre-eleased/proposed and unsupported updates are turned off in ''updates'' in ''software and updates''. Check which server provides best speed to you as well (do that before running major update and once in a few days or so, it helps and is worth the time).

Other than that be careful with PPA's and direct sources you may download from, that's about it. 

Some say turn off the notification for new releases too but I don't do it.

---

