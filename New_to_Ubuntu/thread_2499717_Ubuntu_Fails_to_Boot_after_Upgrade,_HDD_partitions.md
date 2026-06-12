---
title: "Ubuntu Fails to Boot after Upgrade, HDD partitions unknown"
date: 2024-08-07
forum: New to Ubuntu
---

### Post by chriskv on 2024-08-07
I upgraded my Ubuntu 22.04 server a few days ago (using sudo apt-get upgrade). The update completed successfully, I think - I don't recall seeing any error messages. When I rebooted the device today, it failed to even load grub, displaying "error 1962: no operating system found".
I attempted to toggle on CSM in the bios and prefer legacy boot over UEFI, both to no avail. Ubuntu 22.04 was the only OS on the HDD.

I've now booted into a live trial of Ubuntu 22.04 via a USB stick, and was able to gather this from the boot repair tool: 
[https://pastebin.ubuntu.com/p/6pBkkFGpKf/](https://pastebin.ubuntu.com/p/6pBkkFGpKf/)
My primary HDD is sda there, and evidently it can't even detect MBR or partitions on the drive. The Disks utility says the drive is ok, but with 22 bad sectors.

I'm fine to reinstall, most of the things I cared about are backed up, but I'd prefer to repair the install if possible. If that's not possible/practical, I'd hope to recover a few more recent files, if I can at least discover and mount the drive's partition.

I'd also like to determine, before doing a clean install, if the drive really is "ok" or I should replace it. I'd really appreciate any help/advice you all can give!

---

### Post by tea for one on 2024-08-08
[COLOR="#0000FF"]Line 18[/COLOR] - 0 (zero) OS detected
Boot-repair cannot find the operating system.

Can you access your UEFI firmware and see if the disk is visible?
Perhaps, also check that the disk is securely connected to the motherboard?

---

### Post by chriskv on 2024-08-08
Hi, thanks for the response. I checked and UEFI does register the drive (it's available in the boot order). It did so after I opened the box and reseated the connection as well. Unfortunately, I still get error 1962, no OS found.
Is there something I should check next?

---

### Post by tea for one on 2024-08-08
As the drive is recognised by your UEFI, It would be useful to boot into a "Try Ubuntu" live session and see if the partitions are now visible?
```
sudo parted -l
```
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

---

### Post by yancek on 2024-08-08
If you see a message indicating bad blocks you should try running fsck but only if you get positive output from the commands in the post above.  If the drive is not recognized, you obvioulsy won't won't be able to run a filesystem check.

---

### Post by chriskv on 2024-08-08
No such luck, the partitions are still missing...
```
$ sudo parted -l
Error: /dev/sda: unrecognized disk label
Model: ATA Patriot Burst El (scsi)
Disk /dev/sda: 240 GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

# ... correct details on my flash drive

$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
NAME      SIZE  TYPE FSTYPE   FSUSE% FSAVAIL MOUNTPOINT
sda      223.6G  disk
sdb        29.2G  disk iso9660
# .. correct partition details on sdb

$ sudo fsck -n /dev/sda
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
e2fsck_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem. If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else) then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
or
    e2fsck -b 32768 <device>

```
I tried running those alternate e2fsck commands and both returned
```
Bad magic number in super-block while trying to open /dev/sda
```
I'm starting to guess I might be hosed, at this point. Can I try something like testdisk, or is all it going to do is look at those alternate superblock locations? Thanks for the help, all.

---

### Post by oldfred on 2024-08-08
[https://ubuntuforums.org/showthread.php?t=2243715](https://ubuntuforums.org/showthread.php?t=2243715)
Error 1962 us from UEFI not finding a "Windows Boot Entry".
Are you only booting Ubuntu?

Your sda partition label type should be either old MBR or newer gpt, not unknown,

I might try gdisk as if gpt it has a backup partition table that gdisk might find.
sudo gdisk -a /dev/sdb

Or try testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by TheFu on 2024-08-09
Definitely see if **gdisk** will see the partition table on sda.  

You cannot run fsck on the whole disk.  **fsck** should only be run on file systems. Often, those are tied to partitions, but they could be tied to more advanced volume manager objects - like if LVM is used, then the file systems would be in logical volumes - LVs.  Not in PVs or VGs, but in LVs.

BTW, if the system was installed in UEFI mode, you cannot boot using legacy boot methods. You have to use UEFI.

If the partition table isn't restored then I'd use **smartctl** to check the disk for errors found any reported by SMART.  SMART needs to be enabled in the BIOS, then a test needs to be run - taking from 2 minutes to 24+ hours, depending on the disk hardware and type of test requested.  When the test finishes, a report can be requested using **smartctl**.

It should go without saying that if you hope to get any data off sda, then you shouldn't write anything to it.  Do all this from a Try Ubuntu flash drive. Install any missing programs that are needed into the temporary environment.

Data recovery methods generally suck. They suck more if the partition has lots of files and hasn't been zeroed.  Restoring 50 files on a zeroed partition with just those 50 files isn't too hard.  OTOH, if it isn't zeroed (before issues) then all the storage will have remnants of files to be restored and if there is a full OS there, hundreds of thousands of files will be found and randomly named at recovery time.  testdisk can look at file headers for specific types of files - mpeg2, avi, mp4 files, for example, and ignore others.  They will still be randomly named at restore and there might be 10 versions of the same file, so you'll manually need to compare all 10 versions to decide which is to be retained.  For small files, like documents and configs, there can be many more versions found and each will get a unique, random, name.  Directories are lost too, so imagine 10,000+ random filenames in a single directory, with 2-10 versions of each file.

It's a big problem to be manually solved.  After trying to restore once, you'll likely decide that spending $40 on a 2TB USB HDD and doing weekly, versioned, backups is much easier for your most important things.  

Not showing the whole output from lsblk leaves us guessing. Please don't make us guess.

---

### Post by chriskv on 2024-08-10
Hi all, thanks for the advice here. Testdisk was able to show me that, much to my surprise, there were old Windows partitions still around - I thought I'd removed them when I set up the server, but I guess not. I was also able to use testdisk to recover the most recent data that hadn't been backed up yet (though it was unable to fix the partition table). 

I used smartctl as recommended to check that the disk was still healthy (it reported that it was). So I ended up just erasing the disk and reinstalling Ubuntu. Then I restored my data from various backups, and everything seems to be running smoothly again. I'll boot back into the Trial Ubuntu and run fsck on (the new, main partition) /dev/sda2 tomorrow, just to double-check that the device is now in good shape. Thanks again!

---

### Post by TheFu on 2024-08-10
You probably did remove them.  Testdisk is showing old partitions.
Did testdisk recover the filenames and directories?  I've never seen that myself.

BTW, SMART data isn't 100% accurate.  Drives fail without any negative SMART data about 22% of the time. Beware.  You still need backups. All that SMART data really can do is say that the 5 or 10 parameters normally related to a failing disk are not failing today.  I've seen perfectly find SMART data change to a dead HDD in less than 2 weeks.  

Also, SMART data is less useful for NVMe devices.

---

