---
title: "My disks not setup right"
date: 2017-06-07
forum: New to Ubuntu
---

### Post by schmitta on 2017-06-07
I have a dell computer 32 bit with 4 GB ram, a 300GB IDE drive for Ubuntu 16.04, and two 2TB drives one for backup of the other for a bitbox dropbox like application for my network . The desktop screen to the left has:

50 GB volume : Has Desktop, Downloads and documents (it should be 300gb)
4 GB volume : which should probably be /boot (has grub on it)
1.82 TB Bitbox empty
1.82 TB Backup with nothing on it

When I run gparted I get:

/dev/sda1 /media The bitbox disk -- should be boot (and 4 GB)
/dev/sda2 extended 13.04 GB
/dev/sda5/ is for / 13 GB 11.78 GB used (Is this big enough for UBUNTU 16.04)
/dev/sda3/ swap 11.18GB 7 GB used
/dev/sda4/ /media Backup 46.57GB 1.18 GB used
Unallocated 25.09 MB

I did not allocate the /media disks

/dev/sdb/ label Bitbox EXT$ (all that way) 1.82 TB
/dev/sdc/ Label Backup EXT4 1.82TB

I got a low disk space warning of 611 MB during update i guess on sda

I have 13 GB for / with UBUNTU 16.04  --  Is that enough?

What I want is to be able to have the system on the 300 GB IDE drive and the two 2 TB drives to be able to put files on them  for the dropbox and backup.  Should they appear in /media like that? Should I put mounting instructions someplace? 

This system is not in use yet so I can destroy all files with no problem. I usually set up a system with 4GB for /boot, 16GB for /swap, 20GB for / and the rest for /home all on the 300GB IDE drive.  I do not know how to setup the two 2TB disks for regular file system use. I am missing something here - probably mounting info. Thanks for your help.

---

### Post by oldfred on 2017-06-07
I always consider how you organize drives & partitions as personal preference. So you can do whatever you want.
And everyone that responds may have different suggestions, none probably are wrong.

Is your system really 32 bit? Almost everything in last 10 years has been 64 bit unless some of the very lightweight laptops.
If 32 bit, probably only using 3GB of RAM although now it swaps in/out the extra RAM. Just not optimal.
What cpu?
cat /proc/cpuinfo | head -10

I prefer not to have a separate /boot partition. And normally use 25GB or so for / (root) including /boot & /home, but have all data normally in /home in a separate /mnt/data partition usually on another drive. Current system has / on SSD & other partitions on HDD.
I then have /mnt/backup as another mount of a partition, but do not consider it a real backup as it is not versioned, just a copy. I save most important files separately to DVDs, flash drives and other systems for in effect my versioned backups.
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) 

Do not know how bitbox backups work.

Are the 2TB drives internal or external. If internal better to mount with fstab.
Did you partition external drives? If not partitioned you will have issues remounting.

I also now prefer gpt partitioning over the 35 year old MBR(msdos) partitioning. But to boot in BIOS mode you have to add another 1MB unformatted bios_grub partition for grub2's use. But no more primary, extended & logical partitions. Drives over 2TB must be gpt, others it is your choice. But Windows only boots from a gpt drive in UEFI mode, if every installing Windows. 
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Impavidus on 2017-06-07
I'm confused. And so are you, I think.

I don't think that the partitions that are automatically mounted during boot (or are otherwise mentioned in fstab) should be listed on the left of your desktop. So that includes /boot. 13GB is a bit small for a root partition. Your warning could be about the root partition or the /boot partition. 4GB /boot partition is very generous, but if you've got disk space to spare, no problem. Actually, if you don't use lvm or encryption there's little need for a /boot partition.

Let's see the details.```
df -h
sudo parted -l
```

---

### Post by schmitta on 2017-06-08
Thanks Guys for all the great help! for the processor; and disk system I have:
```

alvin@BITBOX:~$ cat /proc/cpuinfo | head -10
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping    : 9
microcode    : 0x2e
cpu MHz        : 2593.680
cache size    : 512 KB
physical id    : 0
```

```
alvin@BITBOX:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           385M  6.0M  379M   2% /run
/dev/sda5        13G   12G  894M  93% /
tmpfs           1.9G  224K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           385M   56K  385M   1% /run/user/1000
/dev/sda4        46G  337M   44G   1% /media/alvin/3ee65f9b-8a27-4ff8-aeb1-7f209238fdd2
/dev/sda1       3.7G  105M  3.3G   3% /media/alvin/8e65db2d-3cc4-41c4-9813-c2e23649d776
/dev/sdb        1.8T   68M  1.7T   1% /media/alvin/bitbox
/dev/sdc        1.8T   68M  1.7T   1% /media/alvin/Backup

```
```
alvin@BITBOX:~$ sudo parted -l
[sudo] password for alvin: 
Model: ATA WDC WD800BB-40JH (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  4000MB  3999MB  primary   ext4            boot
 2      4001MB  18.0GB  14.0GB  extended
 5      4001MB  18.0GB  14.0GB  logical   ext4
 3      18.0GB  30.0GB  12.0GB  primary   linux-swap(v1)
 4      30.0GB  80.0GB  50.0GB  primary   ext4


Model: ATA WDC WD20EFRX-68E (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4


Model: ATA WDC WD20EFRX-68E (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4

```

alvin@BITBOX:~$ 

Any further help you can glean from this would be greatly appreciated!

---

### Post by yancek on 2017-06-08
Your root filesystem partition (sda5) is 93% full so it won't work much longer if you install more software or add files/directories.  Your boot partition is much larger than necessary as they are rarely over 500MB.  You might be able to take space away from boot to add to / as well as using other options.  Posting they output of sudo fdisk -l would be a starting point for into to help.

---

### Post by oldfred on 2017-06-08
Partition Table: loop

I think that means you did not partition drives.
And I have seen others have issues mounting unpartitioned drives. Just about everything expects a partition table and you may have random data where it expects partition table data.

---

### Post by Impavidus on 2017-06-09
Also, you have no /boot partition. Your entire system is on that small 13GB sda5. But you don't really need a /boot partition (unless using lvm or encryption). Your swap is a bit large, but nothing wrong with that, and everything else is just storage space. Best to automate mounting of the other partitions in fstab. Put your /home with Desktop, Documents and Downloads there or use symlinks.

As you haven't done anything yet with your computer, a fresh start may be best.

---

### Post by schmitta on 2017-06-12
Thanks guys for all your help - It is great to have friends on this!

---

