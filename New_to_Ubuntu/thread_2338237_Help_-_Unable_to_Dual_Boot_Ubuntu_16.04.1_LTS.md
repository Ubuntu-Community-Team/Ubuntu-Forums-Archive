---
title: "Help - Unable to Dual Boot Ubuntu 16.04.1 LTS"
date: 2016-09-26
forum: New to Ubuntu
---

### Post by stylishdoggy on 2016-09-26
Hi Bros,

 I am trying to dual boot Ubuntu 16.04.1 LTS on a HP AMD Laptop with Windows 10 and facing troubles while attempting to install on hard disk from USB boot disk. I followed below mentioned steps. Please ignore all stupid mistakes i made and help me to install ubuntu.

1. Downloaded and verified md5 checksum of **ubuntu-16.04.1-desktop-amd64.iso** 
2. Prepared USB Boot drive on 16GB Usb drive using Universal USB Installer 1.9.6.6  
3. Booted into livecd and While attempted to install Ubuntu, Installer working fine and shows me all options 1. Install alongside windows 2. Erase disk 3. LVM 4. Something else. 
4. Then i thought why not create a seperate partition in windows for ubunutu and comeback to live cd then proceed with ubuntu. So booted into windows 10 and created 25 GB unformatted partition
5. Booted in livecd again and but then installer didn't detect windows. 
6. As i thought that the 200 MB- old OEM recovery partition may interrupt detection of windows in ubuntu, and changing type from Primary to Logical drive for 200 MB SYSTEM Partition will allow ubuntu to detect windows boot files (Stupid Mistake). Proceeded to boot into windows and changed Primary to Logical. 
7. Booted back with ubuntu livecd, Ubuntu installer still didn't detect windows. So i tried to go back to windows to see what is wrong but windows didn't boot saying no boot partition
8. Tried to repair windows boot drive using a LILO bootloader by writing it on /dev/sda didn't work and /dev/sda1 didn't work
9. Tried again to repair with a software called boot repair download from ubuntu software utiltiy, Tried setting boot flags to various partitions such as sda2 where that 200MB recovery was and sda5 where Windows C Drive was but in vain
10. Then loaded windows 10 iso in usb using another pc booted into windows installer and repaired startup and succeeded11. Having repaired windows booted again with livecd, so i can install ubuntu. Now installer crashes while pressing install button.
12. Went through online to find the issue of crash, and found that insufficient space is the cause
13. Tried opening Gparted in livecd to see partitions, Gparted crashes and got LIbparted bug. Tried many times rebooting, didn't work
14. Ubuntu still mounts all windows partition and i can right click on disks to see properties. Still have more than 70GB free space

Additinal details : Later tried with Linux mint KDE 18 but same issue persists

Really appreciate help guys

---

### Post by mastablasta on 2016-09-26
> **stylishdoggy said:**
> 
4. Then i thought why not create a seperate partition in windows for ubunutu and comeback to live cd then proceed with ubuntu. So booted into windows 10 and created 30 GB unformatted partition


what is your current partition layout? can you post a screenshot from windows disk manager?

is hibernation off in windows 10?

---

### Post by stylishdoggy on 2016-09-26
> **mastablasta said:**
> what is your current partition layout? can you post a screenshot from windows disk manager?

is hibernation off in windows 10?

[ATTACH=CONFIG]271359[/ATTACH]

Thanks a lot, really appreciate your help. Yes, hibernation is in off

---

### Post by mastablasta on 2016-09-27
primary to extended, not to logical. these should be extended. not sure what implications logical partitions have. is this MBR partition format or GPT. since you are after extended, i would guess it is MBR.
[SIZE=2]https://www.partitionwizard.com/convertpartition/primary-partition-vs-logical-drive.html
[/SIZE]
the issue you were dealing with bootloader is your change of system boot partition into logical one. has nothing to do with ubuntu.

the issue to do with ubuntu is it not seing the windows disk partitions and that is likely because disk is full. still i think it should be able to see the partitions. make sure they are not dynamic. i also do not udnerstand why gparted would crash. might be good to check the image and verify it is a good one.: [SIZE=2]https://help.ubuntu.com/community/HowToMD5SUM
[/SIZE]

i would have to look at this at home, but i had 4 MBR primary partitions and all i needed to do is change one of them into extended, resize it and all was easy after that. that was in Windows 7. installer still didnt' see the Windows disk to offer side-by-side install, however gparted acted normally.

---

### Post by stylishdoggy on 2016-09-27
> **mastablasta said:**
> primary to extended, not to logical. these should be extended. not sure what implications logical partitions have. is this MBR partition format or GPT. since you are after extended, i would guess it is MBR.
[SIZE=2]https://www.partitionwizard.com/convertpartition/primary-partition-vs-logical-drive.html
[/SIZE]
the issue you were dealing with bootloader is your change of system boot partition into logical one. has nothing to do with ubuntu.

the issue to do with ubuntu is it not seing the windows disk partitions and that is likely because disk is full. still i think it should be able to see the partitions. make sure they are not dynamic. i also do not udnerstand why gparted would crash. might be good to check the image and verify it is a good one.: [SIZE=2]https://help.ubuntu.com/community/HowToMD5SUM
[/SIZE]

i would have to look at this at home, but i had 4 MBR primary partitions and all i needed to do is change one of them into extended, resize it and all was easy after that. that was in Windows 7. installer still didnt' see the Windows disk to offer side-by-side install, however gparted acted normally.

I have found the reason behind crash of Installer, please refer below link where someone is facing exactly the same issue which i am facing.
1. [http://askubuntu.com/questions/771740/ubiquity-crashed-with-indexerror-in-free-space-list-out-of-range-when-insta](http://askubuntu.com/questions/771740/ubiquity-crashed-with-indexerror-in-free-space-list-out-of-range-when-insta)

[ATTACH=CONFIG]271369[/ATTACH]

2. [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1543704https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1543704](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1543704https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1543704)

I have managed to get tesk disk installed but as it works inside console, do not have any idea how to repair partition tables. So am trying to find how to do this. 

Below is my fdisk output, I hope you can figureout something this. (I tried but can't understand what is wrong)
```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1459982336 bytes, 2851528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdec3fed2

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            1985 415422463 415420479 198.1G  f W95 Ext'd (LBA)
/dev/sda2  *    415424512 573120511 157696000  75.2G  7 HPFS/NTFS/exFAT
/dev/sda5            2048    409599    407552   199M  7 HPFS/NTFS/exFAT
/dev/sda6          409600 158932991 158523392  75.6G  7 HPFS/NTFS/exFAT
/dev/sda7       158935040 210135039  51200000  24.4G  7 HPFS/NTFS/exFAT
/dev/sda8       210135104 415422463 205287360  97.9G  7 HPFS/NTFS/exFAT

Partition table entries are not in disk order.
ubuntu@ubuntu:~$
```

Also i have verified checksum, it is fine and matches. Let me try changing one of a primary partition to extended as per your method, to see what happens.

---

### Post by mastablasta on 2016-09-27
make sure you backup first before any partition work. 
after that :
1. do a chkdsk (disk --> properties --> under tools tab). in windows console it is porbably still chkdsk -r
2. defragment the drive

only then start with partition movements/changes/whatever.
i think partition tool wizzard should also be able to repair partition table (if they are indeed damaged).

---

### Post by oldfred on 2016-09-27
As mastablasta mentions above, you converted your Windows system boot partition to logical.
Or you converted sda1 as first partition to logical and made a new extended partition as sda1.
Either move boot partition back to primary or move boot files.

But Windows only boots from primary partitions formatted NTFS with the boot flag. Boot-Repair will often copy boot files from Windows boot partition to main or c: drive partition as so many users erase system boot partition not knowing it is essential.
You may be able to move bootmgr & /boot/BCD to c: partition and move boot flag to that partition as it still is primary. But then you would not need Windows boot partition. But make Windows repair flash drive as you then may not be able to use f8 to get into repairs as that also is in boot partition.

       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)

Do not create partitions with Windows, it cannot create anything useful for Linux. And it may convert from basic to dynamic which does not work at all.

Y

---

### Post by stylishdoggy on 2016-09-29
> **mastablasta said:**
> make sure you backup first before any partition work. 
after that :
1. do a chkdsk (disk --> properties --> under tools tab). in windows console it is porbably still chkdsk -r
2. defragment the drive

only then start with partition movements/changes/whatever.
i think partition tool wizzard should also be able to repair partition table (if they are indeed damaged).

I have completed disk check and defragmentation and repaired everything with mini tool partition wizard. But i still cant install ubuntu as a dual boot, So i am thinking of copying all of my to data to external hdd and doing a fresh install of Windows and Ubuntu

---

### Post by mastablasta on 2016-09-29
> **stylishdoggy said:**
> I have completed disk check and defragmentation and repaired everything with mini tool partition wizard. But i still cant install ubuntu as a dual boot, So i am thinking of copying all of my to data to external hdd and doing a fresh install of Windows and Ubuntu

that is the easiet option if you have the possibility to do it. you likely just have too many partitions occupied. boot, system and data should be enough for Windows. or boot and sytem.

i am not sure how you do this with GPT partition format but it should be possible to have more partitions with that. 
read more here of advantages and disadvantages as noted by users.: [SIZE=2]http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr
[/SIZE]

---

### Post by colmax on 2016-09-29
try burning your install onto dvd
worked with mine but my optical drive is internal - no usb used
good luck

---

### Post by stylishdoggy on 2016-09-29
> **mastablasta said:**
> that is the easiet option if you have the possibility to do it. you likely just have too many partitions occupied. boot, system and data should be enough for Windows. or boot and sytem.

i am not sure how you do this with GPT partition format but it should be possible to have more partitions with that. 
read more here of advantages and disadvantages as noted by users.: [SIZE=2]http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr
[/SIZE]

> **oldfred said:**
> As mastablasta mentions above, you converted your Windows system boot partition to logical.
Or you converted sda1 as first partition to logical and made a new extended partition as sda1.
Either move boot partition back to primary or move boot files.

But Windows only boots from primary partitions formatted NTFS with the  boot flag. Boot-Repair will often copy boot files from Windows boot  partition to main or c: drive partition as so many users erase system  boot partition not knowing it is essential.
You may be able to move bootmgr & /boot/BCD to c: partition and move  boot flag to that partition as it still is primary. But then you would  not need Windows boot partition. But make Windows repair flash drive as  you then may not be able to use f8 to get into repairs as that also is  in boot partition.

Y

  
Finally got installer to work. I just made sure that  windows boots from C; drive and boot flag is on C: using Test Disk and formatted 200 MB OEM  recovery partition and merged it to a another partition. Now i am able  to run ubuntu installer and it detects windows too. So, Now i am going through forum to find out proper installation method for dual booting.

Thanks a million guys and thank you for helping me get this working!!

---

### Post by stylishdoggy on 2016-09-29
> **colmax said:**
> try burning your install onto dvd
worked with mine but my optical drive is internal - no usb used
good luck

Thanks man but i dont have a built in optical drive. Actually have managed to get installer running succesfully by just playing around with partitions!

---

