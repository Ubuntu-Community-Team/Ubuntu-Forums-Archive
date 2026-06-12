---
title: "Unable to mount external hard disk partition G"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by raghu.ndp on 2013-12-29
Hi everyone
My external hard disk partition G seems to be corrupted and unreadable. I am getting below error when I try to open the partition G. Please see I am able to open other partition F from the same hard disk.
[B]"Error mounting: mount exited with exit code 32: mount wrong fs type, bad option , bad superblock on 

/dev/sdb1/,missing code page or helper program or other error in somecases useful info is found in syslog - try dmsesg | 

tail or so".[/B]

Thanks in advance, 
Raghu.

---

### Post by Impavidus on 2013-12-29
As you call the partitions F and G, I assume they are Windows partitions. You may need to use Windows to check and repair them

---

### Post by Mark Phelps on 2013-12-29
Linux does not use drive letters, so to better show us the problem, please connect the external drive, open a terminal, and enter "sudo fdisk -lu" (Lowercase L, not a one).  That will list out the size and type of partitions.  Please post that information.

---

### Post by raghu.ndp on 2013-12-29
Hi Mark
I connected external drive and entered ""sudo fdisk -lu" as you suggested. Please find the output of the command as below:

raghu@raghu-laptop:~$ sudo fdisk -lu
[sudo] password for raghu: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c4749fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    31784959    15891456   27  Unknown
/dev/sda2   *    31784960    32501759      358400    7  HPFS/NTFS
/dev/sda3        32501760   429757303   198627772    7  HPFS/NTFS
/dev/sda4       429770941   976771071   273500065+   f  W95 Ext'd (LBA)
/dev/sda5       529975296   741169151   105596928    7  HPFS/NTFS
/dev/sda6       741171200   976771071   117799936    7  HPFS/NTFS
/dev/sda7       429770943   525775319    48002188+  83  Linux
/dev/sda8       525775383   529968284     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   763776127   381888032+   7  HPFS/NTFS
/dev/sdb2       763777024   976769023   106496000    7  HPFS/NTFS
raghu@raghu-laptop:~$

---

### Post by raghu.ndp on 2013-12-31
Hi guys, 
Please help mounting my external hard disk partition. I'm still facing the issue with it.

---

### Post by Coltman151 on 2013-12-31
I'd say the one you're having problems with is the /dev/sda4. I don't think a w95 ext'd partition is compatible with linux. If you have a windows installation to view it with, copy the files out of it, and reformat it to a more linux friendly filesystem

---

### Post by Impavidus on 2013-12-31
No, sda4 is just a standard container for logical partitions. Has been standard stuff for 30 years. It's on the internal drive anyway.

The problem is with sdb1 (or sdb2, maybe). Have you tried opening it on Windows? It's a Windows partition after all. Maybe Windows can check and repair the file system on sdb1, which may be called F or G or whatever on Windows.

---

### Post by arpanaut on 2013-12-31
Sounds like to me that the external was not properly unmounted, or disconnected while still mounted.
Linux will not work with win. partitions in that condition.
You will need to mount the drive while in windows, or do disc repair from windows.
Then properly unmount in win. then Linux will be able to read and write.

---

### Post by raghu.ndp on 2014-01-01
I tried all the ways like disc repair, scan etc from windows and nothing worked. So I would like to to open the partition in linux if possible.

---

### Post by varunendra on 2014-01-01
Install testdisk (make sure you are connected to internet) -
```
sudo apt-get update
sudo apt-get install testdisk
```
Then open it with -
```
sudo testdisk
```
..and follow this [**TestDisk Step-By-Step guide**]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") to do a normal/deeper search on your drive in question. After the search (quick or deeper, as required), can you list your partitions and files in it with the "P" key as suggested in the guide? If yes, you can proceed to writing the partition table structure to the partition table.

If even testdisk can't list the partitions and the files in it, I doubt the partition is recoverable anymore.

---

### Post by Mark Phelps on 2014-01-01
> So I would like to to open the partition in linux if possible. 

IF the filesystems are corrupted, you will NOT be able to read them from Linux any better than you could from Windows.

Your best best, at this point, is to try to recover the files and folders from the external drive partitions -- and in my experience, Windows data recovery utilities work best with Windows filesystems; Linux data recovery utilities, Linux filesystems.  I would not hold out much hope for Testdisk recovering the Windows files.

You could try using Recuva -- that's a free Windows data recovery app.  If you're willing to spend some money, you could also download, install, and try RecoverMyFiles.  That's free to install and try, but you have to buy a license to do the actual recovery.

---

