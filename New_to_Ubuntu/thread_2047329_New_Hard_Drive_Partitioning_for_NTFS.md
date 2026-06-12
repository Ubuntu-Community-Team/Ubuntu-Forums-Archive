---
title: "New Hard Drive Partitioning for NTFS"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by Slownis on 2012-08-24
I recently bought a 2 TB drive, a western digital caviar green WD20EARX.  I'm replacing a dieing smaller drive on an older system.

I would like to have 1 large partition formatted as NTFS, like the old one. I've read around that people have had trouble properly formatting partitions on these newer drives.  Is there a resource that would be helpful for me here?

---

### Post by BDNiner on 2012-08-24
I haven't heard of issues formatting large drives with NTFS. You should be able to format it as one whole partition if you wanted. NTFS partitions can be up to 16TB in size.

---

### Post by mikewhatever on 2012-08-24
Have you tried contacting WD? What does it have to do with Ubuntu.

---

### Post by Slownis on 2012-08-24
> **mikewhatever said:**
> Have you tried contacting WD? What does it have to do with Ubuntu.

I'm using Ubuntu to format it and I've read in these forums where other users have had issues formatting WD20EARS drives with disk utility.

---

### Post by Easy Limits on 2012-08-24
Are you trying to format the drive while you are booted up in to Ubuntu?

---

### Post by Slownis on 2012-08-24
> **Easy Limits said:**
> Are you trying to format the drive while you are booted up in to Ubuntu?

Yes.  The drive is a secondary drive, Ubuntu resides on another disk.

This is what I'm talking about.  I went ahead and tried to format with Disk Utility, as GUID and a single large NTFS partition.  Here is the result:

  WARNING: The partition is misaligned by 3072 bytes.  This may result in poor performance.  Repartitioning is suggested.

---

### Post by oldfred on 2012-08-24
Both gparted & gdisk automatically align partitions. What mode is BIOS/UEFI set to LBA and AHCI?

What is reporting error?

Post this. If not sdb change to new drive.

sudo parted /dev/sdb unit s print
or
sudo gdisk -l /dev/sdb

If you do not have gdisk

sudo apt-get install gdisk

Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by Slownis on 2012-08-24
> **oldfred said:**
> Both gparted & gdisk automatically align partitions. What mode is BIOS/UEFI set to LBA and AHCI?

No idea. Its an old PC, so I doubt its AHCI.
 
> **oldfred said:**
>  
What is reporting error?

Disk Utility
 
> **oldfred said:**
>  
Post this. If not sdb change to new drive.
 
sudo parted /dev/sdb unit s print
or
sudo gdisk -l /dev/sdb
 
GPT fdisk (gdisk) version 0.6.14
Partition table scan:
MBR: protective
BSD: not present
APM: not present
GPT: present
Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 32F96D62-3DA1-4DDF-9E4C-D5C8CB3DDDEF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3907029101 sectors (1.8 TiB)
Number Start (sector) End (sector) Size Code Name
 
By the way, before I did this I deleted the bad partition.

---

### Post by oldfred on 2012-08-25
It looks like you have a drive set up to use gpt partitioning but no partitions. I have used gparted to create my gpt partitioned drives without any issue.

If just having one large NTFS you do not have to add any other partitions, but I like to have a bootable system on every drive. 

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

I use this logic but put a full 25GB Linux partition for Ubuntu.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Slownis on 2012-08-26
Yeah, this didn't really address the issue I was having, which was when you use gparted or disk utility to format these 'advanced format' drives, the cylinders are not aligned correctly.  What I ended up doing was moving the new drive to my win7 machine, formatting it there, then moving it back.  Cheating, I know, but at least now it works.

---

### Post by jibawakee on 2012-08-26
Use a Live Gparted Disk

---

