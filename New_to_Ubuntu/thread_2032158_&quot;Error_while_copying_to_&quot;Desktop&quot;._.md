---
title: "&quot;Error while copying to &quot;Desktop&quot;. There is not enough space on the destination. Try"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Mark.arted on 2012-07-23
I just got a refurbished asus n53s. I used windows 7 to partition the hard drive so that I have 444 GB of space dedicated to ubuntu. I installed pangolin last night. This morning I tried to move my entire music collection (24.6 GB) and got the following message:
"Error while copying to "Desktop". There is not enough space on the destination. Try to remove files to make space." How can this happen when the music file is a small fraction of the allocated drive?

---

### Post by philinux on 2012-07-23
> **Mark.arted said:**
> I just got a refurbished asus n53s. I used windows 7 to partition the hard drive so that I have 444 GB of space dedicated to ubuntu. I installed pangolin last night. This morning I tried to move my entire music collection (24.6 GB) and got the following message:
"Error while copying to "Desktop". There is not enough space on the destination. Try to remove files to make space." How can this happen when the music file is a small fraction of the allocated drive?

Open a terminal and use this code

```
df -h
```

Post back the result.

---

### Post by TheFu on 2012-07-23
> **Mark.arted said:**
> I just got a refurbished asus n53s. I used windows 7 to partition the hard drive so that I have 444 GB of space dedicated to ubuntu. I installed pangolin last night. This morning I tried to move my entire music collection (24.6 GB) and got the following message:
"Error while copying to "Desktop". There is not enough space on the destination. Try to remove files to make space." How can this happen when the music file is a small fraction of the allocated drive?

The outputs from a 'df -k' and a 'sudo fdisk -l /dev/sda' would be helpful too.

Perhaps a different way to make your music available to both Windows AND Linux would be useful?  I'd suggest having 3 partitions.
1- NTFS-Windows7 boot and apps (60G or so) - Primary partition
 2- EXT4 with Ubuntu/Linux. Only 20GB is needed.  - logical partition
3- NTFS-Data make this big enough, but don't use ALL the remaining space until you need it; you can resize partitions to be larger after all - logical partition

Logical partitions are great. There is no practical limit for how many you can have (I've seen over 40) and Linux can be booted fine from a logical partition. I like to have room for a few extra 10G partitions to try out new versions of Linux in a quad-boot setup for fun. On a 1TB disk, what harm does 20GB unused really cause?

Put all your non-program data on the Data partition and keep any large media like music or videos there.  Both Windows and Linux can mount NTFS partitions, but only Linux can mount EXT4 partitions, so Windows won't be able to access your music if you put it there - at least not without some pain.

Keeping large files under your "Desktop" is crazy to me.  If you want those files to appear like they are on your desktop, use a softlink.

FYI, my main desktop is only 13GB in size and I've been using it for about 5 yrs, so don't worry that 20G for Linux isn't enough ... unless you are an Android developer and need 15G just for Eclipse and all the Android SDK files.

---

### Post by Mark.arted on 2012-07-23
Hi Philinux.

Thanks for the interest. In looking a bit deeper I see that both operating systems are located on the C drive. I guess pangolin defaulted to that location somehow.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        20G   17G  1.7G  92% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  852K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  140K  2.9G   1% /run/shm

---

### Post by Mark.arted on 2012-07-23
Thanks to you as well TheFu. I need to think about your comments a bit. I hadn't considered what you describe and I don't know a lot about all this. I really like Ubuntu and only really want windows to open programs that the open source community has not gotten around to practical workarounds for.

---

### Post by TheFu on 2012-07-23
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        20G   17G  1.7G  92% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  852K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  140K  2.9G   1% /run/shm
```This tells us that you only have a 20G partition for the OS and it is 92% full already with "stuff".  You don't have room to copy over more.

To find where all the data eating your storage is located, try this:
```
cd /
sudo du -s *
```

The output from those commands that I asked for earlier would help "find" where the available space is on your HDD, not just what the OS sees too.

To clarify, I'm completely addicted to Linux (and versions of Ubuntu) myself. Of the 20 or so machines running here, only 2 have Windows. My daily driver desktop is Ubuntu-based, but there is a practical need to access some data, especially video and music from MS-Windows still. NTFS is the best way that I know to share data on a dual-boot system between Widnows and Linux that doesn't compromise too much for either OS.

---

### Post by philinux on 2012-07-23
> **Mark.arted said:**
> Hi Philinux.

Thanks for the interest. In looking a bit deeper I see that both operating systems are located on the C drive. I guess pangolin defaulted to that location somehow.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        20G   17G  1.7G  92% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  852K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  140K  2.9G   1% /run/shm

Is this a Wubi install?

---

### Post by madjr on 2012-07-23
you can also check your free space visually:

[http://askubuntu.com/questions/73160/how-do-i-find-the-amount-of-free-space-on-my-hard-drive](http://askubuntu.com/questions/73160/how-do-i-find-the-amount-of-free-space-on-my-hard-drive)

[https://help.ubuntu.com/11.04/ubuntu-help/disk-capacity.html](https://help.ubuntu.com/11.04/ubuntu-help/disk-capacity.html)

---

### Post by Mark.arted on 2012-07-23
Sorry, I didn't understand what you were asking for before.

Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda5       19954564  17261312   1692244  92% /
udev             2999160         4   2999156   1% /dev
tmpfs            1203184       864   1202320   1% /run
none                5120         0      5120   0% /run/lock
none             3007960       664   3007296   1% /run/shm
/dev/sdb1      976760000 208303884 768456116  22% /media/SimpleDrive

and
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x343771f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    52430848   317552639   132560896    7  HPFS/NTFS/exFAT
/dev/sda2       317552640  1250258943   466353152    7  HPFS/NTFS/exFAT
/dev/sda3            2046    52430847    26214401    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5            2048    40042495    20020224   83  Linux
/dev/sda6        40044544    52430847     6193152   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by TheFu on 2012-07-23
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x343771f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    52430848   317552639   132560896    7  HPFS/NTFS/exFAT
/dev/sda2       317552640  1250258943   466353152    7  HPFS/NTFS/exFAT
/dev/sda3            2046    52430847    26214401    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5            2048    40042495    20020224   83  Linux
/dev/sda6        40044544    52430847     6193152   82  Linux swap / Solaris

```Shows that your attempt to allocate 444GB for Linux failed. It appears you got 20G allocated for the sda5 partition.  Did you go into the advanced disk partitioning menu and remember to save your changes?  No matter now.

The best GUI tool that I know to handle partitions is **gparted**.  Highly recommended, however you can't be using the partition you are changing so a boot CDROM with gparted is usually the best answer.  Windows7 might have an issue with some changes due to gparted, but it will tell you about them and offer to correct. That has always worked for me.

BTW, when posting the output from CLI command that look nice in a terminal, please use a monospaced font or put them inside -code- blocks to make reading easier for helpers. If this solves your issue, please mark the subject as "SOLVED" too.

---

### Post by Mark.arted on 2012-07-24
> **TheFu said:**
> ```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x343771f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    52430848   317552639   132560896    7  HPFS/NTFS/exFAT
/dev/sda2       317552640  1250258943   466353152    7  HPFS/NTFS/exFAT
/dev/sda3            2046    52430847    26214401    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5            2048    40042495    20020224   83  Linux
/dev/sda6        40044544    52430847     6193152   82  Linux swap / Solaris

```Shows that your attempt to allocate 444GB for Linux failed. It appears you got 20G allocated for the sda5 partition.  Did you go into the advanced disk partitioning menu and remember to save your changes?  No matter now.

The best GUI tool that I know to handle partitions is **gparted**.  Highly recommended, however you can't be using the partition you are changing so a boot CDROM with gparted is usually the best answer.  Windows7 might have an issue with some changes due to gparted, but it will tell you about them and offer to correct. That has always worked for me.

BTW, when posting the output from CLI command that look nice in a terminal, please use a monospaced font or put them inside -code- blocks to make reading easier for helpers. If this solves your issue, please mark the subject as "SOLVED" too.
Thanks for the information. 
I will make a gparted disk. 
I think I'd like to leave Windows with 100 GB, and use the rest for Ubuntu. Can I simply use gparted to shrink the Windows portion, then consolidate all others with the 20 GB where Ubuntu is living? Again, my only use for Windows is when there is no open source alternative to a program.
 -is this an example of code block?- I've been using Ubuntu for a while but the jargon is always tricky for me.

---

### Post by TheFu on 2012-07-26
> **Mark.arted said:**
> Thanks for the information. 
I will make a gparted disk. 
I think I'd like to leave Windows with 100 GB, and use the rest for Ubuntu. Can I simply use gparted to shrink the Windows portion, then consolidate all others with the 20 GB where Ubuntu is living? Again, my only use for Windows is when there is no open source alternative to a program.
 -is this an example of code block?- I've been using Ubuntu for a while but the jargon is always tricky for me.

100G seems like a reasonable size for Windows.  FYI, my minimal Win7-Ultimate install is 60G with 15G empty. My Win7-Home laptop is 60G with 18G free, so 100G is more than enough if Ubuntu will be your main OS.  The smaller the OS partition is, the better. It makes restores and backups easier when you need it later.

Whether gparted can _simply_ shrink the Win7 partition or not, is unknown. Sometimes Windows puts non-moveable blocks of stuff at the far end of a partition.  Best to follow this order:
* delete the swap drive used by Windows
* defrag the windows partition
* attempt to shrink it inside Windows, then
* boot a gparted disk and shrink it, then
* boot Windows again and let the OS fix any issues.

Yes, that is a "code" block, but it has nothing to do with Ubuntu. It is just an ubuntuforums technique.

BTW, it sounds like you are going to dual-boot for some time. If you are in "the IT business" it is nearly impossible to be 100% Ubuntu/Linux no matter how much you love Linux. For me, this partitioning scheme works:
1) primary - NTFS Windows OS and Apps - 60G
2) logical - Ubuntu LTS  OS and Apps - 13G
3) logical - Ubuntu swap 1G (all Linux installs share this swap)
4) logical - HOME - 5G
5) logical - NTFS DATA - 200G or more. This is where all those large files are placed that I'd like access to between both OSes
6) logical - Spare partition for test driving other OSes - 10G
7) logical - Spare partition for test driving other OSes - 10G

Every HDD can only have 4 primary partitions, but basically an unlimited number of logical partitions.  Since logical partitions aren't really limited, why not make use of them? Leaving 50GB left over on a 1TB HDD unused will provide options for other needs later too.

I've found that Linux loaded with lots of apps doesn't need more than 13G of storage. Any larger allocation is a waste to me.  Keeping HOME and Data separate from the OS/Apps has been learned.  If my HOME is more than 5G, I need to do some clean up and consider making project specific file areas.  

To me a partition is the same as a backup-need. If I can't backup a partition, then I don't need to have it.  None of my partitions on any machines are larger than 1TB. Why?  If I can't easily backup the data, then I don't want to have it. 1TB HDDs were the sweet spot for cheap HDDs for a few years and 1TB is lots and lots of data.

Anyway, I hope these ideas help someone.

---

### Post by Mark.arted on 2012-07-26
Hi TheFu.

A lot for me to digest, but on the face of it your suggestion sounds good. I hadn't thought of using a partition available to both OS's.

I very much appreciate the input.

---

### Post by TheFu on 2012-07-26
NTFS isn't the fastest file system for Linux to access, so you really want only media files there.   To me, the ability and convenience to access certain files from any of the OSes trumps raw performance for those files. 

OTOH, if you are doing HD video editing, then having your "working files" on a quicker file system under Linux would make sense.

---

