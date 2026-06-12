---
title: "Ubuntu seeing HD as empty 500GB drive, even though Win7 is there and booting"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by diablo75 on 2012-11-18
I have a computer I just finished reformatting and re-installing Windows 7 on and during the install I left a good chunk of space unallocated with the intent of later installing Ubuntu into it via manual partitioning.  But when I boot into the live installer from a thumb drive it sees the hard drive as not having any partitions on it.

Any ideas why this might be happening and how I can get it to see the existing partitions?

---

### Post by oldfred on 2012-11-18
Was drive ever RAID? Or was it gpt?

Even after recent install sometimes a chkdsk may be required and that can make gparted or installer not show NTFS partition. It is not hibernated is it?

Post this from terminal in liveCd:

sudo fdisk -lu
       sudo parted /dev/sda unit s print

---

### Post by coffeecat on 2012-11-18
> **diablo75 said:**
> But when I boot into the live installer from a thumb drive it sees the hard drive as not having any partitions on it.

Is this in Gparted or Ubiquity, the installer application?

Two possibilities. If Gparted is showing the whole drive as unallocated when it obviously isn't, then this would be due to a partition table illegality. If this is the case, open a terminal in the live Ubuntu session and post the output of this command:

```
sudo fdisk -lu
```

If the Ubiquity installer is showing no partitions, then this could be due to residual RAID metadata on the drive if it was once used in a RAID array. Was it? If it was, the command in this post should clean it up for you:

[http://ubuntuforums.org/showpost.php?p=9447593&postcount=3](http://ubuntuforums.org/showpost.php?p=9447593&postcount=3)

**EDIT**: ninja'd by oldfred! :)

---

### Post by diablo75 on 2012-11-18
Here is the output for fdisk -lu:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a31bde5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048      206847      102400   42  SFS
/dev/sda3          206848   901122047   450457600   42  SFS
/dev/sda4       901122048   976771119    37824536   42  SFS

Disk /dev/sdb: 8004 MB, 8004304896 bytes
19 heads, 5 sectors/track, 164562 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000afeaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15632383     7815168    b  W95 FAT32
ubuntu@ubuntu:~$ 

```

This drive is the only one that's ever been in this system.  I didn't build it but I doubt it was ever paired up with another.  However I did notice the bios had a RAID controller enabled but set to IDE mode.  I've diabled it and Windows still boots up with it off.

Should I run the command in this thread:

[http://ubuntuforums.org/showpost.php...93&postcount=3](http://ubuntuforums.org/showpost.php...93&postcount=3)

?

Thanks for your help!

---

### Post by diablo75 on 2012-11-18
Forgot to add this output for the second command mentioned in the first reply above:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh
table, and using Parted's rescue feature to recover partitions.

```

---

### Post by oldfred on 2012-11-18
Two issues. Left over gpt data and SFS or dynamic partitions.

Absolutely need good backups before any of these major partition changes.

Windows only boots from gpt drives with UEFI. So if it sees a gpt partitioned drive it converts it to MBR. But gpt has a backup partition table that Windows does not delete. Linux tools see both MBR(msdos) partitioning and gpt partitioning and do not know what to do.

Best to remove backup gpt partition data. But I do not know if this will work before the SFS is fixed or vice-versa.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


At some point you used Windows to create more than 4 partitions. It does not use an extended & logical partitions. Windows official policy is to totally backup drive, erase drive and reformat back to basic partitions. 



       
 Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion but they are changing to only the paid version. You may want to search other download sites for the older version.
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)


       
 Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

### Post by diablo75 on 2012-11-18
I decided to start from scratch, beginning with using diskpart from a DOS terminal on the the windows 7 disk, using the clean all option.  That should fix it.  Already had a backup so... figured this would be the quickest solution.  Thanks everybody!

---

### Post by oldfred on 2012-11-19
Sometimes starting over is the easiest way to solve the issues.

Windows may not erase the gpt meta data. If you still have an issue with gpt data left on drive use fixparts to erase it.

---

### Post by diablo75 on 2012-11-19
> **oldfred said:**
> Sometimes starting over is the easiest way to solve the issues.

Windows may not erase the gpt meta data. If you still have an issue with gpt data left on drive use fixparts to erase it.

Diskpart should thoug.  Still waiting for it to zero the whole drive right now.  I'll post again if it doesnt work.  Thanks again!

---

