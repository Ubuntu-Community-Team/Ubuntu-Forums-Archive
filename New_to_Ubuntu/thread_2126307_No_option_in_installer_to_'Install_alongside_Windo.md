---
title: "No option in installer to 'Install alongside Windows',"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Scooterdork07 on 2013-03-16
Hey, I just wiped my computer completely, and re-installed Win7. There is, however, no option that shows that my Win installation is recognized by linux. I am attampting to install 12.04. When I look at 'Something Else", it says I have one 500 GB drive, unpartitioned, for sda. Can I fix this?

---

### Post by grahammechanical on 2013-03-16
There could be a couple of reasons why the installer doe snot offer you an option to install alongside Windows. 

1) Windows is using up the maximum number of allowed primary partitions - 4. 

2) The new install of Windows formatted the driver as a dynamic disk which the partitioner cannot read as it is a proprietary format.

[http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx](http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx)

Regards.

---

### Post by Scooterdork07 on 2013-03-16
Windows is Using 2 disks, and the drive is Basic.

---

### Post by oldfred on 2013-03-16
Post this from  terminal in  live mode of installer. 

sudo fdisk -lu

---

### Post by Scooterdork07 on 2013-03-16
ubuntu@ubuntu:~$ sudo fdisk -lu 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe54a8aa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   976771071   488282112    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2047 MB, 2047679488 bytes
255 heads, 63 sectors/track, 248 cylinders, total 3999374 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6cbbb57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128     3995775     1997824    6  FAT16
ubuntu@ubuntu:~$

---

### Post by oldfred on 2013-03-16
Was this originally Windows 8 or why was it gpt before. Windows converts to BIOS with MBR(msdos) and does not delete the backup gpt partition table. Linux tools then get confused as they see MBR and gpt and are not sure what you really want.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by Scooterdork07 on 2013-03-16
So, I have to:
GO Live, 
Install Fixparts
use it to remove the GPT?

Oh, and it has always been win7. I don't know where GPT stuff would have come from

---

### Post by Scooterdork07 on 2013-03-17
Well, that didn't work. Trying it with Fixparts, I'm not sure which I want to select, but when I try to select the GPT and delete it, it says that there are no partitions...

---

### Post by Scooterdork07 on 2013-03-17
Please help me get rid of these errors! Will they be overwritten if I just wipe windows and install linux to my HDD?

---

### Post by oldfred on 2013-03-17
I do not think with fixparts you want to select gpt, but want mbr(msdos) and have it remove the gpt data. 
Did you download gdisk which is the gpt partition tool?

Windows will not overwrite that backup partition table. It is a bug in Windows.

---

