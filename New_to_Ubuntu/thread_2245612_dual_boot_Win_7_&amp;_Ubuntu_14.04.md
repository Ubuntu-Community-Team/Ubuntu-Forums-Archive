---
title: "dual boot Win 7 &amp; Ubuntu 14.04"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by odatkid on 2014-09-24
Hi All,
 I'm a newbie and I purchased an 8GB flash drive with Ubuntu 14.04 LTS Desktop (64bit) from OSDisc.com and I'm trying to install it to dual boot with my existing windows 7 Pro 64bit. I created a partition of 20GB on windows and left it unallocated but when I get to installing Ubuntu it's not at all clear to me how to find that space. The installer sees my drive (a 240GB SSD) but I don't see that partition I created and am afraid of destroying my data on the drive. If someone can point me to SIMPLE instructions that I can understand it would be appreciated.

Thanks for help

---

### Post by sandyd on 2014-09-24
> **odatkid said:**
> Hi All,
 I'm a newbie and I purchased an 8GB flash drive with Ubuntu 14.04 LTS Desktop (64bit) from OSDisc.com and I'm trying to install it to dual boot with my existing windows 7 Pro 64bit. I created a partition of 20GB on windows and left it unallocated but when I get to installing Ubuntu it's not at all clear to me how to find that space. The installer sees my drive (a 240GB SSD) but I don't see that partition I created and am afraid of destroying my data on the drive. If someone can point me to SIMPLE instructions that I can understand it would be appreciated.

Thanks for help

Hi, can you do the following.
1. Go to the Unity Dash (Ubuntu Icon in the top-left corner), and type in 'Gparted'. Open the first entry that appears, and attach the screenshot.
2. Open a terminal (Unity Dash -> Terminal).
Run the following commands and paste the output here.
```

sudo fdisk -l
sudo parted -l
```

The commands will allow us to have a view of your current partitioning setup, and see why Ubuntu may have issues detecting the partition.

Thanks!

---

### Post by odatkid on 2014-09-25
Sandy....Thank you for your reply. When I said newbie I meant it. It was a challenge to get what you suggested.
 Here is the result:

ubuntu@ubuntu:~$ sudo fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 


Disk /dev/sda: 240.1 GB, 240057409536 bytes 
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0xfe660ada 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT 
/dev/sda2          206848   426913791   213353472    7  HPFS/NTFS/exFAT 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0xe421e421 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        2048   976769023   488383488    7  HPFS/NTFS/exFAT 

Disk /dev/sdc: 7756 MB, 7756087296 bytes 
32 heads, 63 sectors/track, 7514 cylinders, total 15148608 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x432e19d0 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *          63    15148223     7574080+   c  W95 FAT32 (LBA) 
ubuntu@ubuntu:~$ sudo fdisk parted -l 
 It appears to me that it's seeing all 3 of the drives the SSD 240GB and my second drive 500GB for storage and of course it sees the 8GB USB drive with Ubuntu on it. Don't understand the initial "Warning" at all

---

### Post by stalkingwolf on 2014-09-25
when the installer gets to the HDD selection type of install window select something else.  this will bring up a window with a list of partitions.  you will want the 20 gb unallocated one.
Click that and it will bring up another box to set it up  i use ext4 for the file format type,    for mount point /  then check the box that asks if you want to format.  then click ok.

---

### Post by oldfred on 2014-09-25
If drive was gpt partitioned and you install Windows in BIOS mode it converts to MBR(msdos) partitioning. But it does it incorrectly and leaves the backup gpt partition table. Then Linux tools see both MBR and gpt and assume you want to erase disk or totally start over.

You can use fixparts to remove the extra gpt data.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

    
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

But Windows only boots from gpt with UEFI or only from MBR with BIOS. Windows (except XP) will read another drive that is gpt partitioned if a Windows formatted partition.

---

### Post by odatkid on 2014-09-25
> **stalkingwolf said:**
> when the installer gets to the HDD selection type of install window select something else.  this will bring up a window with a list of partitions.  you will want the 20 gb unallocated one.
Click that and it will bring up another box to set it up  i use ext4 for the file format type,    for mount point /  then check the box that asks if you want to format.  then click ok.
 
Thank you for the reply. I have clicked "something else" and it doesn't see the 20GB umallocated partition for some reason. I can only see the the full SSD and the 500GB second drive. That's where I'm at.

Thank you again

---

### Post by odatkid on 2014-09-26
> **oldfred said:**
> If drive was gpt partitioned and you install Windows in BIOS mode it converts to MBR(msdos) partitioning. But it does it incorrectly and leaves the backup gpt partition table. Then Linux tools see both MBR and gpt and assume you want to erase disk or totally start over.

You can use fixparts to remove the extra gpt data.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

    
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

But Windows only boots from gpt with UEFI or only from MBR with BIOS. Windows (except XP) will read another drive that is gpt partitioned if a Windows formatted partition.

Thank you so much for your reply. 
 I downloaded "Fixparts" and didn't understand what to do with it. All I'm sure of is that I'm not using UEFI boot. Other than that I'm totally lost. I get the sense that this may be impossible for me to get the assistance I need having no Linux experience. I'm a reasonably smart guy but totally ignorant as how to do this. My hope was that things might have gotten a bit easier with Ubuntu 14.04 LTS Desktop (64bit). Initially I created the 20GB partition as NTFS and then reclaimed the partition and repartitioned it as unallocated. Is this where  I'm going wrong? Can I or should I try to create the partition with Linux installation? Still not sure why I couldn't see the partition.  Any other help is greatly appreciated.

Cheers

---

### Post by oldfred on 2014-09-26
If you download the Debian package, you should just be able to double click install it. 
The linked site has the details on running it which really is just telling it which drive you want to fix.

---

### Post by yancek on 2014-09-26
> Thank you for the reply. I have clicked "something else" and it doesn't see the 20GB umallocated partition 

Just for your information, you are using terms incorrectly.  A partition can basically include the entire drive or partitions can be pretty much any size and there are some limitations on the number of partitions you can have depending upon several factors.  You can't have an "unallocated partition", if space is unallocated then it is not on a partition.  A partition needs to have a filesystem on it to be usable.  You seem to have free space at the end of your 240GB partition but it is unallocated space.  That is how Ubuntu should see it and I'm not sure why it does not.

Your fdisk output does show the 240GB drive has GPT partitioning.  I don't use GPT so can't really help but others here should be able to advise.

---

### Post by odatkid on 2014-09-26
> **oldfred said:**
> If you download the Debian package, you should just be able to double click install it. 
The linked site has the details on running it which really is just telling it which drive you want to fix.

Olfred, Thank you for the reply. My confusion continues as I disabled UFEI in the BIOS before installing Windows 7 Pro and have already purchased Ubuntu on  a USB flash drive. Have no idea about Debian package.
 When I said newbie I meant newbie. Is there a better forum than "New to Ubuntu" for morons like me?

Thank you again

---

### Post by odatkid on 2014-09-26
> **yancek said:**
> Just for your information, you are using terms incorrectly.  A partition can basically include the entire drive or partitions can be pretty much any size and there are some limitations on the number of partitions you can have depending upon several factors.  You can't have an "unallocated partition", if space is unallocated then it is not on a partition.  A partition needs to have a filesystem on it to be usable.  You seem to have free space at the end of your 240GB partition but it is unallocated space.  That is how Ubuntu should see it and I'm not sure why it does not.

Your fdisk output does show the 240GB drive has GPT partitioning.  I don't use GPT so can't really help but others here should be able to advise.

Yancek, 
 Thank you for reply and clearing up the partition terminology which now makes perfect sense to me. You said you don't use GPT(whatever that means); what do you use and would it work for my setup? Do think I have any options with this project, without harming my windows installation? 

Thank you again...

---

### Post by odatkid on 2014-09-29
Can Anybody help?

---

### Post by yancek on 2014-09-29
> You said you don't use GPT(whatever that means); what do you use and would it work for my setup? 

A brief explanation of GPT (GUID Partition Table) and UEFI (Unified Extensible Firmware Interface) at the site below.  Just google either term and you will find all kinds of detailed info.   
[http://www.computerhope.com/jargon/g/gpt.htm](http://www.computerhope.com/jargon/g/gpt.htm)

I use the standard MBR which has been in use on computers for 30+ years.  The suggestions by oldfred above might be able to resolve the issue but not having used GPT/UEFI or having any familiarity with "fixparts" I can't offer any more details.  Good luck with it.

---

