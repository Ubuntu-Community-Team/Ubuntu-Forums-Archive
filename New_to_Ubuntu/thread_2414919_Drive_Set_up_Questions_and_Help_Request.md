---
title: "Drive Set up Questions and Help Request"
date: 2019-03-17
forum: New to Ubuntu
---

### Post by Dave_Mann on 2019-03-17
/dev/sda is a 1.0 TB drive

/dev/sda1 is 576 MB Partition EFI (FAT-12/16/32) Bootable

That's where 18.10 was installed but with no swap partition

Disks shows the following info on same HD:

Partition 2 (/dev/sda2) "Partition type unknown" 0.0 KB

Partition 3 (/dev/sda) "Free Space 1000GB"

-----

/dev/sdb is 4TB drive {I noticed that there is no "1" after the sdb}

4.0 TB - 2.6 TB free

Contents Ext4 (ver 1.0) mounted at /mnt/bigstorage

Does not state "Linux Filesystem" on description of partition type

-----

/dev/sdc1 is 4TB drive


4.0TB 2.6TB free

Contents Ext4 (ver 1.0) mounted at /mnt/bigstorage#2

States "Linux Filesystem" on partition type

-----

Questions for the group:

1.  Should I do something with that 1TB empty area on /dev/sda ?  

2.  Can I use that empty area for a 500GB swap?

3.  Why does /dev/sdb not show a "1" after the "/dev/sdb"?

4.  Can I reformat /dev/sdc1 as a RAID and set my rsync to back up all of /dev/sda to it?

5.  /dev/sdc1 only allows me access as root -- how can I chown the entire drive as user?

6.  /dev/sdb only allows me access as root -- how can I chown the entire drive as user?

Any advice is appreciated.

---

### Post by TheFu on 2019-03-17
Please post the output from. 
* df -Th
* sudo fdisk -l
Much easier to read and understand than text description. Also, it provides facts. No worries about misinterpretations.

1. I don't know.
2. In general, more than 4.1G of swap is a waste. Is there a specific reason you want more?  Do you hate end-users and want to make things slow?
3. No idea what you are looking at.
4. Setting up RAID requires all disks be empty.  RAID solves 3 issues. You still need backups even with RAID. Sometimes the only fix for RAID issues is to destroy the RAID and start over, using backups.
5. Learn about file permissions.  If the disk is NTFS, only mount options can control permissions, ownership.
6. It is a terrible idea to work storage at the whole disk level (sda/sdb). Always create at least 1 partition (sda1/sdb1) and manage storage under it. This applies to RAID at well. Reasons.  Feel free to have more than 1 partition, if required.

For non-trivial storage setups, using LVM can bring great flexibility. LVM can be thought of as partitions, but with much more flexibility. Often, resizing a logical volume doesn't require taking storage offline. Cloning, migrating to other disks, snapshots for perfect backups, all those things are possible with LVM.  But LVM shouldn't be used by people new to storage management without a clear grasp of most concepts.

---

### Post by Dennis N on 2019-03-17
I suggest you post the output of **[FONT=Courier New]sudo fdisk -l[/FONT]** and **[FONT=Courier New]sudo parted -l[/FONT]** so that these disks and partitions can be analyzed.

In the meantime, a couple of remarks:
> 5. /dev/sdc1 only allows me access as root -- how can I chown the entire drive as user?
sdc1 is a partition. When formatted, it contains a file system. If formatted ext4, The ext4 filesystem has an owner and permissions. When created, it is owned by root. To change the owner, you use the chown command:

If you user name is dave, and the file system is mounted at /mnt/data, then
```
sudo chown -R dave:dave /mnt/data
```
will make you the owner, with all the necessary premissions to use it.

Without a number, sdb designates the disk. With a number, sdb1 designates a partition.

disk sdb should have a partition table created so you can create partitions and then file systems on them. It's not clear if it does. Maybe you can format an entire disk without a partition defined, but I've never done it since using floppy disks in the 90s, so I'm not sure how that will work out.

To make a partition table on a disk: In gparted, **Device > create partition table > gpt (suggested type)** This will destroy any existing data on the disk.

---

### Post by Dave_Mann on 2019-03-17
[B]Thank you for your concise and timely responses.

Output for fdisk -l[/B]

```
dave@TheMightyWurlitzer:~$ **sudo fdisk -l**
[sudo] password for dave: 
Disk /dev/loop0: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1d32d1e4

Device     Boot      Start        End    Sectors  Size Id Type
/dev/sda1  *          2048    1050623    1048576  512M ef EFI (FAT-12/16/32)
/dev/sda2          1052670 1953523711 1952471042  931G  5 Extended
/dev/sda5       1936822272 1953523711   16701440    8G 82 Linux swap / Solaris
/dev/sda6          1052672 1936822271 1935769600  923G 83 Linux

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.




Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytesOutput for parted -l
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2568777B-CC07-427E-8947-E0111FE71A29

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux filesystem


**Output for parted -l**

[code]dave@TheMightyWurlitzer:~$ **sudo parted -l**
[sudo] password for dave: 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  538MB   537MB   primary   fat32           boot, esp
 2      539MB   1000GB  1000GB  extended
 6      539MB   992GB   991GB   logical   ext4
 5      992GB   1000GB  8551MB  logical   linux-swap(v1)


Model: ATA WDC WD40EZRX-00S (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ext4


Model: ATA WDC WD40EZRX-00S (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name          Flags
 1      1049kB  4001GB  4001GB  ext4         BigStorage#2
```

---

### Post by TheFu on 2019-03-17
Please edit the fdisk and wrap in "code tags" so it is readable.
Also, please edit/remove all the "loop" devices. Those have nothing to do with storage and just muddy up the output.

Took a quick look. sda2 is an extended partition. This holds all the logical partitions numbered 5+.  It is NOT unused.  Check out the wikipedia article on extended and logical partitions to understand this.

If you used GPT for the partitioning, then there isn't any need for extended or logical partitions, which are a work-around due to partition design choiced made in the 1980s with MBR/MSDOS partitioning.

---

### Post by Dennis N on 2019-03-17
sdc has a partition table and a partition, so all you need to do is change owner on sdc1 mount point to have full access. (directions in post #3)

sdb doesn't have a partition table at all. This is not recommended. You should make a gpt type partition table (directions in post #3) and partition(s); then change owner on the partition(s) you create. Caution: doing this will destroy any existing data on the disk.

I don't use raid, so can't comment on that question.

---

### Post by TheFu on 2019-03-17
BTW, the setup being shown might have LVM.  Just check that with **sudo lsv**.  This will clearly show a hierarchy of how the storage is setup.  

And using LVM doesn't prevent using and managing RAID with LVM.

---

### Post by oldfred on 2019-03-17
Added code tags, easy to add with Forum's advanced editor and # icon.

You have UEFI install on sda, but the now 35 year old MBR partitioning. Ubuntu can be forced to install to MBR with UEFI, but UEFI strongly suggests using gpt and Windows only installs in UEFI boot mode to gpt partitioned drives. If little or no data in new install on sda, better to re-install using UEFI and gpt partitioning.

Did you use sdb as installer? Normally installer is a small flash drive, but many of the tools to create installer to flash drive use dd which makes a hybrid DVD/flash drive configuration that may look like a loop device.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

If you partition in advance gparted will default to MBR(msdos) on smaller drives,  unless you first change to gpt.
       
 Select gpt under device, advanced over msdos(MBR) default partitioning before starting. 
    
If you use Ubuntu installer, it will always use gpt for UEFI installs.
And new versions of Ubuntu use a swap file, so swap partition is not required
Or default UEFI install is just an ESP - efi system partition (FAT32) and / (root as ext4) on a gpt partitioned drive.

---

### Post by Dave_Mann on 2019-03-17
> **TheFu said:**
> Please edit the fdisk and wrap in "code tags" so it is readable.
Also, please edit/remove all the "loop" devices. Those have nothing to do with storage and just muddy up the output.

Took a quick look. sda2 is an extended partition. This holds all the logical partitions numbered 5+.  It is NOT unused.  Check out the wikipedia article on extended and logical partitions to understand this.

If you used GPT for the partitioning, then there isn't any need for extended or logical partitions, which are a work-around due to partition design choices made in the 1980s with MBR/MSDOS partitioning.

OK, I removed the "loop" devices; I didn't know not to include them.

I'm not sure how to do the "wrap in code tags" for the fdisk output, sorry.

I'll read up on the sda2 conundrum and educate myself on that issue.

If GPT isn't needed, what then?  Oh, but wait, I may find answer on researching it.

Thanks for help, so far!

---

### Post by Dave_Mann on 2019-03-17
> **oldfred said:**
> Added code tags, easy to add with Forum's advanced editor and # icon.

You have UEFI install on sda, but the now 35 year old MBR partitioning. Ubuntu can be forced to install to MBR with UEFI, but UEFI strongly suggests using gpt and Windows only installs in UEFI boot mode to gpt partitioned drives. If little or no data in new install on sda, better to re-install using UEFI and gpt partitioning.

Did you use sdb as installer? Normally installer is a small flash drive, but many of the tools to create installer to flash drive use dd which makes a hybrid DVD/flash drive configuration that may look like a loop device.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

If you partition in advance gparted will default to MBR(msdos) on smaller drives,  unless you first change to gpt.
       
 Select gpt under device, advanced over msdos(MBR) default partitioning before starting. 
    
If you use Ubuntu installer, it will always use gpt for UEFI installs.
And new versions of Ubuntu use a swap file, so swap partition is not required
Or default UEFI install is just an ESP - efi system partition (FAT32) and / (root as ext4) on a gpt partitioned drive.

I'm trying to figure this out.  When I installed 18.10, I remember reading that I would need to select "efi" when the installer began running during the formatting process.  It looks like I must have missed selecting the option to make a swap file.  I have 8GB of RAM and very rarely use even 75% of it, so maybe I thought there was no need for swap.  Then again, I might have been thinking that I could put swap onto a 254GB SSD.  IDK.

I get the impression that my system is badly assembled and I want to fix it.  I can completely reload, reformat, etc. since all of my data and /home is secured on an external HD which I could rsync back to the new  system.

So far, I'm researching the various posts and article everyone has recommended.

I don't use Window$ at all on this workstation.

Thanks again,

Dave

---

### Post by oldfred on 2019-03-17
It is not an option to make a swap file, it just defaults to using that if no swap partition is found.

See links in my signature for links to examples of partitioning, older links will still show creating swap partition and that can be ignored now.

---

### Post by Dave_Mann on 2019-03-17
> **oldfred said:**
> It is not an option to make a swap file, it just defaults to using that if no swap partition is found.

See links in my signature for links to examples of partitioning, older links will still show creating swap partition and that can be ignored now.

OK, but what I see in the links you provided are about going from a Window$ system to Ubuntu somehow co-existing with Window$.

Right now I am thinking -- after researching all of the advice given here -- is to simple do a complete reinstall of Ubuntu 18.10 onto one of the 4TB drives and let the installer do its "default" install.  If I redo /dev/sda1 I won't have enough room for my /home partition.

I should add, that the axiom "if it an't broke don't fix it" _should_ have been applied when I went directly from Ubuntu 16 to 18.10 ... I've have no end of problems trying to get the work station back to its previously very high speed and ease of accessing files.

Thanks again for your reply

Dave

---

### Post by oldfred on 2019-03-17
I do not think a default install to a 4TiB drive is a good idea, only because then you have a 4TiB / (root) partition. The default installer was from back when 200GB was a large drive and most installs were dual boots so / was not that large.

I use 25GB for / as I have multiple installs and keep all my data in a separate data partition. I boot using / on SSD and data partition on HDD but have multiple other partitions, some more data, some other installs and some still unallocated after a couple of years for future partitions.
I like to keep a LTS  version as main working install, so I do have to totally redo every 9 months, but still do installs to experiment.

Now older. I would not use /boot nor swap.
[https://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](https://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
       Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

You just need to do a little planning on what you want on what drive.
I do like to have a full install, even smaller emergency install on every drive. I put a full install on every flash drive now that is 32GB or more, but in a smaller / partition.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.

---

### Post by TheFu on 2019-03-23
My advice today is different from this thread: [https://ubuntuforums.org/showthread.php?t=2170308](https://ubuntuforums.org/showthread.php?t=2170308)
In there I suggest leaving 10G of empty space between the different partitions.  Today, I'd use LVM to get the desired flexibility.  Also, a quality SSD make a lot of sense.  I've had cheap SSDs fail within 2-3 yrs. Just bought a Samsung EVO 860 2 weeks ago. I need a 9[67]0 EVO for another system soon, but don't like the current prices.  860 is $78 and the 960 is $120+ both 500G in size.  I'd rather not waste a SATA port when there are 2 NVMe slots on that system.

As for sizes of different storage areas (either partitons or LVs), On laptops (anything portable), I use whole disk encryption which uses LVM + a separate /boot/. For non-portable computers, I use LVM, but not encryption for the whole OS.  Maybe I should encrypt everything, if only to make storage warranty support easier on my mind.

/boot - 1GB.  Reasons. In theory 500MB should be enough ... but in the past it hasn't been.
/ - 15 to 25GB.  Depends on the system. As small as practical.
/home - 10-25GB.  Don't keep media or project files (programming) in there. As small as practical.
/Data/video - whatever you need, but I keep media and other things separate.
/Data/projects - 25-100G. I suppose a Java or Node.js dev could need more.

Partitioning is all about backup and backup designs.  My backups go to spinning disks 4TB or larger in size.  That means no partition/LV can be larger than 4TB, just to keep restoring data easier.

Data that is large and seldom changes - like media, photos, audio, videos, can't have versioned backups due to practical constraints.  However, EVERYTHING ELSE can and should.  The OS, settings, documents that I create, things I'm editing (programming stuff), all change over time and need daily, automatic, versioned, "pulled" backups from another machine on the network.  "pulled" is very important, to prevent the cyrpto-locker viruses from having any access.

I don't have small, emergency, installs on any of my systems.  When I need that, I'll boot from a USB flash drive - usually an Ubuntu-Mate 16.04 stick then go into and fix whatever the problem is.  20 yrs ago, that wasn't an option and my knowledge of how all the system files/directories and booting (at least for my systems), was much less than it is today.  A non-booting system is a minor thing for me these days.  Critical systems all run inside virtual machines, which can be restored from backups and running on other VM host hardware in 15-45 minutes to exactly the state it was sometime early this morning.  I have an unplugged core i7 from 2009 laying around which could easily run 10 VMs, if necessary.  Heck, my new $305 laptop could too.

Don't worry about allocated all the storage. LVM allows us to expand an LV while the system is running with 1 command, lvextend or lvresize.  We don't need to know which LV will need the storage in advance.  From a high level, an LV, logical volume, can be thought of as a partition.  We mount LVs. We put file systems onto LVs.  We can move LVs from 1 disk to another easily. The cost of using LVM is some added complexity.  There are 3 abstract layers to LVM, which provides nearly unlimited flexibility.  Also, LVM let's us make "snapshots" to ensure 100% consistent backups on a running system.  The trick is that there must be empty space on the same storage for the snapshot as long as it is needed.   I'm a big believer in LVM.

If you want to jump to the next level in storage management, you can use ZFS for non-OS areas.  ZFS merges LVM and highly advanced, validated, file systems together.  Want to make a remote backup of a zfs partition safely?  It is 1 command. ZFS validates that what gets written to disk is what was sent there. No other file system does that. The others trust that CRCs and other hardware will catch and fix any errors. With current kernels, the core kernel guys have been giving the ZFS team hassles about some issues.

Regardless of what you select, you'll make the right choice for YOUR needs. It is your box. You get to live with those choices. Most of my systems aren't in their "ideal" state for storage either. 2 have storage designs from 2010, when I new a little less and the options weren't as solid as they are today.  We do the best we can, with the knowledge and equipment we have, at the time. Nothing is perfect.

---

