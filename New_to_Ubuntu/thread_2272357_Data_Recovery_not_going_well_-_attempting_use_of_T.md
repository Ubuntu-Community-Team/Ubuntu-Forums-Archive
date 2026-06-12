---
title: "Data Recovery not going well - attempting use of TestDisk"
date: 2015-04-06
forum: New to Ubuntu
---

### Post by Mark_Hagan on 2015-04-06
Hello all, first a bit of background.

I am new to Ubuntu but not new to Linux (although I wouldn't call myself an expert but I work on Java software development on Linux platform).

I have been meaning to convert to Linux for personal use for some time now and chose the event of finding my Netgear ReadyNAS Duo v2 2TB disk being corrupted as motivation to make the leap! I researched the forum and tools available and decided, rightly or wrongly, following the Linux (and in particular, Ubuntu) platform approach was my best option. Netgear were pretty useless and just wanted me to pay them for help because my warranty had expired. Hence I want to try myself.

I have installed Ubuntu 14.04 LTS in dual boot with my Windows 8 preinstalled Dell Inspiron 660 with approx 0.5TB given to each OS.

IIRC there was only about 300-400GB space used on the disk (WD Red SATA) before it failed so its nowhere near capacity. Having said that I've ordered another one anyway (due in the next day or so) to be used as the destination for anything I can recover.

So, on to the hairy details. I spent the day going through TestDisk - Analysis, Deeper Search - but all it did was come back and say the 'Linux' partition couldn't be recovered. Not what I wanted to hear but also not one of the scenarios described in the TestDisk wiki. It also said the size of the disk was wrong which seemed odd.

I am fairly certain I have not written to, or performed any admin on, the disk since discovering the failure. I also used a trial version of a Windows tool to see what could be recovered and it seemed to find plenty of files. 

Basically, despite that worrying first attempt I am optimistic that my data is still there some where. I just might need to learn a bit more about blocks and sectors to find it!

I also reviewed gddrescue but that seems like I might need to be in a better place before proceeding to that and also need to have my replacement disk available. I only have about 450GB of free disk space available on my Ubuntu FS but I was not sure if the recovery tool needed up to 2TB as it would not necessarily know how much data to recover until it scanned the whole disk.

I'd love to hear if any one recognises the TestDisk phrase "The following partition can't be recovered" and can give me some hope!

Cheers,
Mark

I tried attaching the log file but maybe as I'm new it didn't let me. Here it is:--

p.s. I also posted this log file on the TestDisk forum so a) I hope this type of cross-post is OK and b) I'll make sure any info or progress is synch'd.

```

==========


Sun Apr  5 09:19:46 2015
Command line: TestDisk

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 3.13.0-48-generic (#80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015) x86_64
Compiler: GCC 4.8
Compilation date: 2013-10-29T01:29:29
ext2fs lib: 1.42.9, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       1953525168 sectors
/dev/sda: user_max   1953525168 sectors
/dev/sda: native_max 1953525168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 1 sectors, sector size=512
Hard disk list
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - ST31000524AS, S/N:5VPD82CS, FW:JC4A
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 30400 255 63, sector size=4096 - WDC WD20 EFRX-68AX9N0

Partition table type (auto): Intel
Disk /dev/sdb - 2000 GB / 1863 GiB - WDC WD20 EFRX-68AX9N0
Partition table type: Intel

Analyse Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 30400 255 63
Geometry from i386 MBR: head=256 sector=63
check_part_i386 1 type EE: no test
Current partition structure:
 1 P EFI GPT                  0   0  2 243201  80 63 3907029167

Warning: Bad ending head (CHS and LBA don't match)
No partition is bootable

search_part()
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 30400 255 63

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   28 170 15    93 235 11    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/14788, s_mnt_count=16/4294967295, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 484573184
recover_EXT2: part_size 484573184
     Linux                15154  74 25 45317 147 14  484573184
     ext4 blocksize=4096 Large file Sparse superblock Recover, 1984 GB / 1848 GiB
This partition ends after the disk limits. (start=243453696, size=484573184, end=728026879, disk end=488378646)
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 30400 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (2000 GB / 1863 GiB) seems too small! (< 2981 GB / 2777 GiB)
The following partition can't be recovered:
     Linux                15154  74 25 45317 147 14  484573184
     ext4 blocksize=4096 Large file Sparse superblock Recover, 1984 GB / 1848 GiB

Results
   * Linux                   28 170 15    93 235 14    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB


dir_partition inode=2
   * Linux                   28 170 15    93 235 14    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
ext2fs_dir_iterate failed with error 1.
Directory /

interface_write()
 1 * Linux                   28 170 15    93 235 14    1048320

search_part()
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 30400 255 63
file_pread(5,3,buffer,8(0/0/9)) read err: Partial read
file_pread(5,2,buffer,8(0/0/9)) read err: Partial read

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   28 170 15    93 235 11    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   28 182 27    93 247 23    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   28 247 28    94  57 24    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   29   0  1    94  64 60    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   29  33  5    94  98  1    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/31, s_mnt_count=1/38, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1048317
recover_EXT2: part_size 1048317
     Linux                   29  73 45    94 138 41    1048317
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4094 MiB

recover_EXT2: s_block_group_nr=0/14788, s_mnt_count=16/4294967295, s_blocks_per_group=32768, s_inodes_per_group=2048
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 484573184
recover_EXT2: part_size 484573184
     Linux                15154  74 25 45317 147 14  484573184
     ext4 blocksize=4096 Large file Sparse superblock Recover, 1984 GB / 1848 GiB
This partition ends after the disk limits. (start=243453696, size=484573184, end=728026879, disk end=488378646)
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 30400 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (2000 GB / 1863 GiB) seems too small! (< 2981 GB / 2777 GiB)
The following partition can't be recovered:
     Linux                15154  74 25 45317 147 14  484573184
     ext4 blocksize=4096 Large file Sparse superblock Recover, 1984 GB / 1848 GiB
get_geometry_from_list_part_aux head=255 nbr=1
get_geometry_from_list_part_aux head=255 nbr=1

Results
     Linux                   28 170 15    93 235 14    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
     Linux                   28 182 27    93 247 26    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
     Linux                   28 247 28    94  57 27    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
     Linux                   29   0  1    94 254 63    1060290
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4342 MB / 4141 MiB
     Linux                   29  33  5    94  98  4    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
     Linux                   29  73 45    94 138 44    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB


dir_partition inode=2
     Linux                   28 170 15    93 235 14    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                   28 182 27    93 247 26    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                   28 247 28    94  57 27    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                   29   0  1    94 254 63    1060290
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4342 MB / 4141 MiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                   29  33  5    94  98  4    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                   29  73 45    94 138 44    1048320
     ext3 blocksize=4096 Large file Sparse superblock Recover, 4293 MB / 4095 MiB
ext2fs_dir_iterate failed with error 1.
Directory /

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
```

---

### Post by TheFu on 2015-04-06
Doesn't readyNAS use a proprietary format for storage?  I think you need to determine that and solve how to get the data out of that into something useful - ext2/3/4 - something like that.

The first thing you should do when the new disk arrives is make a bit-for-bit copy from the old Red onto the new Red using **ddrescue**. Then only do work on the new disk.  Make the copy at the whole-disk device level.

[http://forum.r-tt.com/readynas-nv-v2-xraid-2-recovery-t8719.html](http://forum.r-tt.com/readynas-nv-v2-xraid-2-recovery-t8719.html) has some cautionary tails of people attempting data recovery on the same platform - be very careful.

Going forward, hopefully you've learned that RAID doesn't replace the need for backups.

---

### Post by Mark_Hagan on 2015-04-06
Thanks for the response. Regarding "Doesn't readyNAS use a proprietary format for storage?". I certainly hope not! I had a ticket open with Netgear so I've posed that to them now to see what they say.

I think I might have difficulty with the disk to disk copy as I'm not sure I see how I'm going to mount both simultaneously as I only have one USB bridge. I don't fancy fitting it internally but that might be my only option. I'm assuming I wouldn't be able to access it while its in the ReadyNAS cabinet.

And finally, in response to the need for backups, I have only just recently stopped beating myself up about this...although backing up a 2TB disk is a bit of a chore but its one I'll get sorted for next time.

---

### Post by TheFu on 2015-04-06
a) We've all been there. The way I learned about backups - had a failure and lost 80% of my data which was spread across 3 drives. Only 1 disk failed, but I had used LVM to merge the 3 disks into a single volume. No backup.  **That got me backup religion.**

b) Do not mount the storage. USB connections suck. They don't provide the entire SATA command set. SATA or eSATA are necessary.  Most normal desktop PCs have 4-6 SATA connectors. Use that.  Boot off a liveCD, install **ddrescue** into the live-environment, then do **sudo ddrescue /dev/sda /dev/sdb /tmp/logfile**  Of course, you need to be extremely, extremely, extremely careful to get the device names correct and accurate. Or you will loose everything.  **Triple check** which drive has which device name. Sure, you can use USB for this ... it won't be as quick and you have to mirror the entire disk bit-for-bit, not just the data.

I don't know anything about ReadyNAS myself - had two friends with those devices. It didn't turn out well for them or their data. Don't know the details - both are IT experts. They've both switched - one chose Thecus and the other built his own NAS with the newer versions of FreeNAS - he wanted ZFS RAIDz2. I built a DAS array using [addonics equipment]("http://www.addonics.com/") - Infiniband connected.

I think you need another new HDD. You will need to make backups somewhere, right? Optical media is what I used for about a decade, but large HDDs have gotten so cheap that the hassle of optical backups just isn't worth it to me anymore. I know some people use 25-50G Bluray for this. This was media backups - for OS and non-media file backups, I use rdiff-backup, automatic, nightly, versioned, and keep 60-120 days depending on the system risk of issues. The best how-to for rdiff-backup is: [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)  Much better than the 5 articles I've written about it. ;(

Get backup religion now so any disk failure in the future is an inconvenience, not data loss.

Sorry I'm not much help with the ReadyNAS part.

---

### Post by Mark_Hagan on 2015-04-06
Hello again. So Netgear support came back and said the following:-

"There is no proprietary ReadyNAS technology that we use for the file  system. Normally the ReadyNAS uses Linux Ext3/Ext4 file system. A  typical Linux distribution can mount and access the data from the disks.  For more information for PC data recovery, see this forum thread.."

The link is here:- [http://www.readynas.com/forum/viewtopic.php?f=11&t=35153](http://www.readynas.com/forum/viewtopic.php?f=11&t=35153)

They want me to use VMWare with an image supplied by them. New ground for me...

---

### Post by Mark_Hagan on 2015-04-13
Some updates, but more questions!!

So I did what you (TheFu) suggested and installed the disks (the original corrupt and the new WD Red) internally with SATA cables.

I then copied the original disk (/dev/sdc) to the new one (/dev/sdb) using ddrescue but only after several dozen checks that I had the device names the right way round.

Running TestDisk on the new imaged device then gave more interesting results. It recognised it as EFI GPT and also that it had Linux RAID partitions (despite Netgear telling me you can't have raid with one disk and it would be JBOD format - just a bunch of disks).

I then ran PhotoRec and got hold of a lot of files from the disk but as you'll know, you lose file names and directory structure so it's not really that usable although not disappointed that I have most of the files in one state or other.

The main issue appeared to be 'Invalid RAID superblock' and so after a bit of searching I found a few things to try. 

One of them was to try to mount the partition that looked like it might have the majority of the data on it (it was 1.8TB):-

```

mark@mark-Inspiron-660:/$ sudo mount /dev/sdb3 /mnt/sdb-backup/
mount: unknown filesystem type 'linux_raid_member'

```

So then more research yielded mdadm as the right RAID tool

```

mark@mark-Inspiron-660:/$ sudo mdadm --assemble --scan
mdadm: /dev/md/1 has been started with 1 drive.
mdadm: /dev/md/2 has been started with 1 drive (out of 2).

```

Now this is starting to look hopeful as this appears (according to another search) that this means the RAID array is 'active':-

```

mark@mark-Inspiron-660:/$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=698e599e:fbcbf591:c936431c:cedde9e8 name=2CB05DBEC8B5:1
ARRAY /dev/md/2 metadata=1.2 UUID=63ba3665:cfcd3ef9:81bb9131:9e0a4197 name=2CB05DBEC8B5:2

# This file was auto-generated on Mon, 13 Apr 2015 16:00:51 +0100
# by mkconf $Id$

```

But trying to mount them didn't work:-

```

mark@mark-Inspiron-660:/$ sudo mount /dev/md/1 /mnt/sdb-backup/
/dev/md1 looks like swapspace - not mounted
mount: you must specify the filesystem type
mark@mark-Inspiron-660:/$ sudo mount /dev/md/2 /mnt/sdb-backup/
mount: unknown filesystem type 'LVM2_member'

```

So, the searching at the moment is all about 'logical volume' but I have absolutely no idea what I'm doing....

Can anyone suggest where I can go from here? There is probably still something wrong with one or both of these /dev/md/n devices but I don't know enough to work out what.

Thanks for any help.

Mark

---

### Post by TheFu on 2015-04-13
It is definitely possible to have LVM2 on-top-of mdadm-RAID disks.  TLDP has an extensive LVM2 guide.  vgdisplay, lvdisplay are the main commands I recall off the top of my head.  I use LVM, but it isn't something I touch daily ... or even yearly. Always have to look up the commands for what I need.

Do you recall what RAID level your disks were in?  RAID0, RAID1, something else?  There is a command to ask for "details" or "examine" the RAID disk. Read the manpage to ensure those can safely be run on your copy disk.

Here's 1 of my arrays (no LVM):
```
$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Fri Sep 14 14:06:57 2012
     Raid Level : raid1
     Array Size : 1943010816 (1853.00 GiB 1989.64 GB)
  Used Dev Size : 1943010816 (1853.00 GiB 1989.64 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Apr 13 13:05:35 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:1
           UUID : ac416c61:885ec692:5dc9a72b:2a70a601
         Events : 5281

    Number   Major   Minor   RaidDevice State
       0       8       35        0      active sync   /dev/sdc3
       2       8       51        1      active sync   /dev/sdd3
```

How it appears when mounted:
```

$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/md1        1.8T  817G  915G  48% /raid
```

---

### Post by Mark_Hagan on 2015-04-13
Yup! I did it!!!  I installed Logical Volume Management from the Ubuntu Software Centre  I ran :-  

```
 
mark@mark-Inspiron-660:~$ sudo pvs 
[sudo] password for mark:    
/dev/sdc1: read failed after 0 of 4096 at 4096: Input/output error   
PV         VG   Fmt  Attr PSize PFree    
/dev/md2   c    lvm2 a--  1.81t 10.00g 

mark@mark-Inspiron-660:~$ sudo lvdisplay   
/dev/sdc1: read failed after 0 of 4096 at 4096: Input/output error   
--- Logical volume ---   
LV Path                /dev/c/c   
LV Name                c   
VG Name                c   
LV UUID                v3f2ty-50Ig-4rDe-57De-dlJD-8Sx5-mKJc32   
LV Write Access        read/write   
LV Creation host, time ,    
LV Status              NOT available   
LV Size                1.81 TiB   
Current LE             29576   
Segments               1   
Allocation             inherit   
Read ahead sectors     auto 


```  

FYI the /dev/sdc1/ is the original drive still in a bad state...  So then I tried to mount the /dev/c/c/   

```
 mark@mark-Inspiron-660:~$ sudo mount /dev/c/c /mnt/sdb-backup/ 
mount: special device /dev/c/c does not exist 

```  

Another quick search and this was because it wasn't active...so 

```
 mark@mark-Inspiron-660:~$ sudo vgchange -ay c   
1 logical volume(s) in volume group "c" now active 

mark@mark-Inspiron-660:~$ sudo mount /dev/c/c /mnt/sdb-backup/ 
mark@mark-Inspiron-660:~$ ls -l /mnt/sdb-backup/ 
total 48 
-rw------- 1 root   root     7168 Jan 30 23:17 aquota.group 
-rw------- 1 root   root     8192 Jan 30 23:17 aquota.user 
drwxrwxrwt 4 nobody nogroup  4096 Jan 30  2014 backup 
drwxrwxrwx 6 nobody nogroup  4096 Mar 26  2013 Documents 
drwxr-xr-x 3     98      98  4096 Feb 14  2013 home 
drwx------ 2 root   root    16384 Feb 14  2013 lost+found 
drwxrwxrwt 5 nobody nogroup  4096 Feb 14  2013 media 

``` 

My data!!!  Busily copying and backing it up now!!  Thank you so much for all your help (and to all those others who put various updates all over the place for me to find!)  Happy days..

---

### Post by TheFu on 2015-04-13
Might be helpful if you used code-tags so that last paragraph lines up - it is unreadable now.

I'm not used to seeing /dev/c/c stuff ... usually see /dev/sdc1 or similar.  Or if mounting by-id, by-label, by-uuid, by-path ... those are buried in /dev/disk/by-* directories. Is that something new?

---

### Post by Mark_Hagan on 2015-04-13
Not sure what happened on that posting. It all went on one line...edited now.

I assumed the weird path was because it was a Logical volume as opposed to a physical volume and maybe the name format would have been decided by the Logical Volume Management software I downloaded from the Software Centre?

---

### Post by Mark_Hagan on 2015-04-13
Also, I found this link very helpful:- [https://blmath.wordpress.com/2010/04/01/how-to-mount-a-logical-volume/](https://blmath.wordpress.com/2010/04/01/how-to-mount-a-logical-volume/)

---

### Post by TheFu on 2015-04-13
My LVM mounts have always been something like this ... 
/dev/mapper/vg--hadar-lv--hadar
/dev/mapper/vg--hadar-lv--backups
/dev/mapper/qbe-root
/dev/mapper/qbe-export
/dev/mapper/qbe-backups
You get the idea.  None of my systems are newer than 14.04. Perhaps some things have changed?

---

