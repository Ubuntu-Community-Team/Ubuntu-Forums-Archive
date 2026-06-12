---
title: "Windows partition problem"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by priyank on 2012-05-07
HI
I am a beginner at Ubuntu.  I have windows 7 installed in my Notebook and have 3 partitions i.e. c, d, e.

I installed ubuntu latest release.  After that I checked and found that the e partition of windows is not visible.

Can anyone help me out.

Priyank

---

### Post by lisati on 2012-05-07
From Ubuntu, could you please open the terminal, and post the output of the following here:
```
sudo fdisk -l
```

---

### Post by priyank on 2012-05-07
priyank@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea93ea93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   251742207   125767680    7  HPFS/NTFS/exFAT
/dev/sda3       251742208   438439935    93348864    7  HPFS/NTFS/exFAT
/dev/sda4       438439936   625139711    93349888    f  W95 Ext'd (LBA)
/dev/sda5       438441984   625139711    93348864    7  HPFS/NTFS/exFAT
priyank@ubuntu:~$

---

### Post by priyank on 2012-05-10
hi,

I tried to reinstalled the ubuntu but not luck.  the fdiks shows like

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea93ea93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   251742207   125767680    7  HPFS/NTFS/exFAT
/dev/sda3       251742208   438439935    93348864    7  HPFS/NTFS/exFAT
/dev/sda4       438439936   625139711    93349888    f  W95 Ext'd (LBA)
/dev/sda5       438441984   625139711    93348864    7  HPFS/NTFS/exFAT
priyank@ubuntu:~$ 


kindly help please

---

### Post by Lateralis on 2012-05-10
How are you installing Ubuntu?  Are you using Wubi or installing into a separate partition?

---

### Post by Utkarsh Ray on 2012-05-10
> **Lateralis said:**
> How are you installing Ubuntu?  Are you using Wubi or installing into a separate partition?

Good point!
If you use wubi i.e. Install Inside Windows, you'll be unable to access that partition from ubuntu (most likely you have done this because the computer name is ubuntu by default in wubi install and like yourname-desktop in true install)
If you want to access all the windows data from ubuntu, make another partition according to your needs and install ubuntu in that. Otherwise if you want to 'really' install ubuntu, still make another partition and boot from the CD in the optical drive.

---

### Post by priyank on 2012-05-11
Thanks
I used wubi to install.

when I first installed, it was not showing windows e drive.  On reinstalling its not showing windows c drive... 
can you please let me know how to install after making partition and also I do not have a CD for Ubuntu.

---

### Post by wilee-nilee on 2012-05-11
> **priyank said:**
> Thanks
I used wubi to install.

when I first installed, it was not showing windows e drive.  On reinstalling its not showing windows c drive... 
can you please let me know how to install after making partition and also I do not have a CD for Ubuntu.

A wubi install will only show windows I believe in the media folder, some where I forget anyway.  Wubi is a file in windows, so you will not see windows like you would in  a partitioned install.

You do have access to both OS's from each one, but not like a regular install.

You might consider installing as a true dual boot. There is a thread on the forums that gives you the info you need to transfer that wubi to a regular partition.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

For wubi help I would make sure that thread starter sees your posts so put wubi in your future header if it is related to that type of install.

---

### Post by Mark Phelps on 2012-05-11
IN a wubi install, the MS Windows filesystem is automatically mounter under /host.  Look there to see if your directories and files can be accessed.

If they are not listed there, then click the "home" icon in the launchbar at the top left and see if the individual partitions are listed there.  They won't use the MS Windows convention of "Drive Letters" because Linux filesystems do not use that.

---

