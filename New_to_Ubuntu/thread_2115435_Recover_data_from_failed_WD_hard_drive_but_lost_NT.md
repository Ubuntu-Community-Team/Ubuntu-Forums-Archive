---
title: "Recover data from failed WD hard drive but lost NTFS signature on main partition"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by Sushi Lover on 2013-02-12
It seems that the hard drive on my windows 7 laptop has failed and I'm not able to boot the computer.  When I run diagnostics, I get error codes that lead me to a hard drive failure.  I'm trying to run Ubuntu Live CD 12.10 to recover the data from my hard drive and came across an issue.  
  
When I type "sudo fdisk -l", I get the following output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda2   *      208845    30928844    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30928845  1250261679   609666417+   7  HPFS/NTFS/exFAT

When I type "sudo parted -l", I get the following ouput:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD6400BEVT-7 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  107MB   107MB   primary  fat16        diag
 2      107MB   15.8GB  15.7GB  primary  ntfs         boot
 3      15.8GB  640GB   624GB   primary


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

In short I am not able to mount /dev/sda3 to recover the data.  I can mount the other partitions but not sda3.  It comes back with the following error message, "NTFS signature is missing".  So, why am I able to see the NTFS file system status using "fdisk -l, but not "parted -l"?  Can I still recover the data?

This is my first shot at Linux/Ubuntu, so I am not familiar with the commands or Ubuntu desktop.  I only got this far from researching and it led me to Ubuntu as the best tool to recover my data, if possible.

Thanks in advance.

---

### Post by Mark Phelps on 2013-02-12
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by Sushi Lover on 2013-02-13
Thank you for taking the time to reply.

---

### Post by fdrake on 2013-02-13
previous post is valid too , Check my threat too if you need extra help
[http://ubuntuforums.org/showthread.php?t=2106164](http://ubuntuforums.org/showthread.php?t=2106164)

---

### Post by Sushi Lover on 2013-02-13
Mark/fdrake,
Thanks for the suggestions.  I'll remove the hard drive and run chkdsk before proceeding to other options.  I'll post results later...

---

### Post by Mark Phelps on 2013-02-13
> **Sushi Lover said:**
> Mark/fdrake,
Thanks for the suggestions.  I'll remove the hard drive and run chkdsk before proceeding to other options.  I'll post results later...

IF you're going to use RecoverMyFiles, then do NOT run CHKDSK first; instead, run the utility -- and see how good a job it does at finding your files.  If it works well, and you purchase a license, retrieve your files to another drive for safe keeping.

After that is done, you can run a CHDSK.  And, if you were not able to find ALL the files you need the first time, I would run RecoverMyFiles again.

---

