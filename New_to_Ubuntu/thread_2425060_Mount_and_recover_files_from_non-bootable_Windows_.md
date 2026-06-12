---
title: "Mount and recover files from non-bootable Windows SSD"
date: 2019-08-19
forum: New to Ubuntu
---

### Post by bpmccarthy on 2019-08-19
Hello all, first time poster and Ubuntu newbie here.

I'm attempting to recover the data from our Windows drive after (what I suspect) was an interrupted Windows update.  Windows laptop (Lenovo T460s) that crashed won't even boot to BIOS, so the SSD is connected to an older laptop running Ubuntu via a USB external drive.

Started by running Disks, which shows the 4 partitions, but partition 3 (/dev/sdb3, the partition I need files from) shows up as an unknown partition.

Then I ran ```
sudo lshw
```, which gives the following information about the drive:

```
                    *-disk
                         description: SCSI Disk
                         product: 2115
                         vendor: ASMT
                         physical id: 0.0.0
                         bus info: scsi@6:0.0.0
                         logical name: /dev/sdb
                         version: 0
                         serial: 00000000000000000000
                         size: 238GiB (256GB)
                         capabilities: gpt-1.00 partitioned partitioned:gpt
                         configuration: ansiversion=6 guid=c8ad4bab-b428-4c5f-bbb3-d096af4a67dc logicalsectorsize=512 sectorsize=512
                       *-volume:0
                            description: Windows FAT volume
                            vendor: MSDOS5.0
                            physical id: 1
                            bus info: scsi@6:0.0.0,1
                            logical name: /dev/sdb1
                            version: FAT32
                            serial: 1c1f-69b6
                            size: 255MiB
                            capacity: 259MiB
                            capabilities: boot precious readonly hidden nomount fat initialized
                            configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
                       *-volume:1
                            description: reserved partition
                            vendor: Windows
                            physical id: 2
                            bus info: scsi@6:0.0.0,2
                            logical name: /dev/sdb2
                            serial: 6cac19d2-6b53-4a9d-b0e9-ce94f9578585
                            capacity: 15MiB
                            capabilities: nofs precious readonly hidden nomount
                            configuration: name=Microsoft reserved partition
                       *-volume:2
                            description: Windows FAT volume
                            vendor: -FVE-FS-
                            physical id: 3
                            bus info: scsi@6:0.0.0,3
                            logical name: /dev/sdb3
                            version: FAT32
                            serial: 0000-0000
                            size: 15EiB
                            capabilities: fat initialized
                            configuration: FATs=0 filesystem=fat name=Basic data partition
                       *-volume:3
                            description: Windows NTFS volume
                            vendor: Windows
                            physical id: 4
                            bus info: scsi@6:0.0.0,4
                            logical name: /dev/sdb4
                            version: 3.1
                            serial: 86af5768-140d-7a46-ab6c-af126b90db1f
                            size: 969MiB
                            capacity: 999MiB
                            capabilities: boot precious readonly hidden nomount ntfs initialized
                            configuration: clustersize=4096 created=2017-09-27 22:23:20 filesystem=ntfs label=WinRE_DRV modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true

```

Attempting to mount the drive renders the following:

```
brad@brad-ThinkPad-Edge:~$ sudo mount /dev/sdb3 /mnt/storage
NTFS signature is missing.
Failed to mount '/dev/sdb3': Invalid argument
The device '/dev/sdb3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

I was able to use TestDisk to create an image of the disk (albeit with an "Image created successfully but read errors have occured." result).

TestDisk shows 

```
Bad sector count.
No partition is bootable.
```

I have a warranty to get the computer fixed, but I suspect it will come with a reformatted drive and the loss of all data onboard, which I do not have a recent backup of.

Two things I'm trying to do:

1. Can the files be recovered from an image.dd file?

2. Can the partitions be repaired to render the disk bootable/mountable?

Thanks in advance!

---

### Post by yancek on 2019-08-20
Your lshw output shows /dev/sdb3 as a FAT32 partition and the mount error says it doesn't seem to have a valid ntfs.  Have you tried mounting with the filesystem type included?

> sudo mount -t vfat /dev/sdb3 /mnt/storage

If you still get an error you might try some windows tool.  Also, which version of windows is it?

---

### Post by Autodave on 2019-08-20
If it will not boot to the BIOS, that has nothing to do with Windows: sounds like a failure to the motherboard. 

That machine evidently came with Win7 on it.  That may or may not have have had UEFI.  If you updated it to Win10, then it would have had UEFI and *secure boot*/ *fast boot* enabled.

I would try hooking it up to a Windows machine and running the diagnostics from that machine.  IF you can get it working there, then either from there or your Linux machine you should be able to get the files copied.  While on Win10, you need to to make sure that you unmount the drive properly.  You may even have to disable *fast boot *that machine to properly release the drive in order to mount it in Linux.

---

### Post by TheFu on 2019-08-20
> **bpmccarthy said:**
>  
Two things I'm trying to do:

1. Can the files be recovered from an image.dd file?

2. Can the partitions be repaired to render the disk bootable/mountable?


1) perhaps.  perhaps not.  I never work from the original disk when trying to recover data.  Always make an image using **ddrescue** first and work from that.  Google "ubuntu data recovery" for a how-to guide around data recovery.

2) perhaps. perhaps not.  mounting is easier than booting. sda3 is reported as NTFS, not FAT.
```
sudo mkdir /mnt/recover
sudo mount  -o ro   -t ntfs    /dev/sda3     /mnt/recover
# do all your data copies ... then either reboot or remember to umount
sudo umount  /mnt/recover

```
Might need to install the ntfs fuse driver. I don't remember if it is included or not.  **sudo apt install ntfs-3g** is the command.

If Windows didn't properly close the partition, Linux won't mount it read-write.  Try the read-only option as I've shown above.  And you should be working on a cloned drive, never the original.   To clone, use an identical sized (or larger) disk of the same sector size.  512b or 4k sectors.  **sudo ddrescue   /dev/sda   /dev/sdX  /tmp/loggging**  Replace the X with the correct letter for the target disk.  If you get it wrong, everything on that disk will be overwritten.  If you get the order of the options wrong, the original disk will be wiped.

Having automatic, daily, versioned, backups, makes all these problems go away.  Much easier to restore from backups and being able to sleep at night is good too.

---

### Post by bpmccarthy on 2019-08-21
Attempted to mount as both FAT and NTFS:

```
brad@brad-ThinkPad-Edge:/$ sudo mount  -o ro   -t ntfs    /dev/sdb3     /mnt/storage
[sudo] password for brad: 
NTFS signature is missing.
Failed to mount '/dev/sdb3': Invalid argument
The device '/dev/sdb3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
brad@brad-ThinkPad-Edge:/$ sudo mount -t vfat /dev/sdb3 /mnt/storage
mount: /mnt/storage: wrong fs type, bad option, bad superblock on /dev/sdb3, missing codepage or helper program, or other error.
```

I do have a copy of the disk as an image.dd that I can work from as well.

I am running TestDisk to attempt to analyze the disk.  Quick Search results are here:

```
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /media/brad/Sarah's External/BackupDir/image.dd - 256 GB / 238 GiB - CHS 31
131 255 63
     Partition                  Start        End    Size in sectors

   P FAT32                    0  32 32    33  69 35     532480 [SYSTEM]
   P NTFS                 30875 232 14 31003 100  9    2048000
   P NTFS                 31003 100  9 31130 223  4    2048000
```


I'm running the Deeper Search option now.  Will probably take a day or so.  Initial screen gives the following warnings:

```
  FAT32                               0  32 32      33  69 35     532480 [SYSTEM]
  FAT32                               0  32 38      33  69 41     532480 [NO NAME]
Warning: number of heads/cylinder mismatches 16 (NTFS) != 255 (HD)
Warning: number of sectors per track mismatches 2 (NTFS) != 63 (HD)
  NTFS                                3 116 60       3 214 59           6174
Warning: number of heads/cylinder mismatches 16 (NTFS) != 255 (HD)
Warning: number of sectors per track mismatches 2 (NTFS) != 63 (HD)
  NTFS                                3 214 59       4  57 58           6174


```

---

### Post by TheFu on 2019-08-21
Sorry, I can't help.  I have daily, versioned, backups, so never need to deal with data recovery.

---

### Post by bpmccarthy on 2019-08-21
I'm definitely convinced after this experience. If you have a particular solution you prefer (cloud service vs local NAS, etc.), I'd be glad to hear it.  Thanks for the help.

---

### Post by The Cog on 2019-08-24
Has anyone noticed the size on volume 2 in the lshw output? 
```
size: 15EiB
```
I think the partition table may be corrupt.
If you have the space, work on a copy of your ddrescue image, so you can make multiple attempts to fix it without further damaging the original.

---

### Post by Autodave on 2019-08-24
> **bpmccarthy said:**
> I'm definitely convinced after this experience. If you have a particular solution you prefer (cloud service vs local NAS, etc.), I'd be glad to hear it.  Thanks for the help.

I use an external HD to keep a backup out of all machines.  I have a backup HD in each machine.  I also have an external HD backup that resides at my mom's house.  If this house burns down, I still have a copy.

---

### Post by TheFu on 2019-08-24
> **bpmccarthy said:**
> I'm definitely convinced after this experience. If you have a particular solution you prefer (cloud service vs local NAS, etc.), I'd be glad to hear it.  Thanks for the help.

I'm backing up about 15-20 systems, so what I do might not be good for a 1-computer setup.  I'm fairly skilled, so some of my methods wouldn't be useful to someone without at least intermediate Unix skills and understanding.

I have a backup server.  It "pulls" backups using a tool called rdiff-backup.  There are pre-backup and post-backup scripts that get run remotely over ssh.  Those scripts generate information about each system and place that data into a place that gets included in the daily backups.  I use a root-equiv backup userid to make the rdiff-backup connections. It can only run 1 command, limited by the ssh authorized_hosts settings.  That is the local backup.  Each of the details I mention above are important parts of the solution to address risks.
I do not backup everything on the system, just what is needed to restore everything so it works the same.  That means I don't backup /lib/ or /bin/ or /usr/ (except /usr/local/). I create a list of manually installed package and use that list to feed back during the restore.

Media files are mirrored using rsync. No versioning. No offsite copies.  

Daily, I **rsync** the backup areas offsite.  With rsync, I can control the bandwidth used, so other WAN users don't notice it. Daily change data is fairly small, so that usually finishes in less than 2 hrs.  This my my 3-2-1 backup solution.
3 copies, 2 locations, 1 on different media.

The local, daily, versioned, backups for each system take between 30 seconds and 25 minutes according to the summary report I get daily.

Restoring each system takes about 30-45 minutes.  It took about 5 times to get everything correct to ensure I had enough, but didn't waste too much storage with totally unnecessary files.  After those first efforts, I use the backups to get a single file from 3 months ago or a directory from yesterday or to restore a complete system after a do-release-upgrade fails.  When I got a new laptop last spring, I used my restore process to load everything onto the new box. Basically, 45 minutes later and it was "my laptop" with all my data, settings, programs.

I've had a few disk failures over the decades too.  The 1 that got me *backup religion* saw 80% data loss. This was when HDDs were $300+, so having a spare was an expensive problem.  

Today, $50 can get us a 2TB USB3 HDD, so there really isn't any excuse for not having versioned backups.  Let me check that price ...  Fry's has a bare drive for $49.  Buy a USB3 "dock" for $22 and you can swap out HDDs as needed.  This can work to rotate 2 HDDs between home and work for your "offsite" backup. Do that every week.  If the storage is portable, be certain to LUKS encrypt it.  Encryption will make the automatic part of backups a little harder. In a home, perhaps weekly backups are sufficient?  That's up to you.  I started by doing weekly backups and it saved me once from a hacker actively going after that machine. If you have multiple machines, doing "pull" backups will add some protection against malware that having storage directly connected will not.

But that is a different story.

---

