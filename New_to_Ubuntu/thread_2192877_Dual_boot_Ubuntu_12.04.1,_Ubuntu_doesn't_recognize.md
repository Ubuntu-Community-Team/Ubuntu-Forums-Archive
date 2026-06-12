---
title: "Dual boot Ubuntu 12.04.1, Ubuntu doesn't recognize the Windows installation"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by lucian.andercou on 2013-12-10
I've tried installing Ubuntu 12.04.1 on a lap-top with a Windows 7 Professional OS already installed on it,as a dual boot, and it kept saying that there is no detected operating system and also didn't detect any Windows partition at all, it just saw my 320 GB hard-disk as a whole. I looked up several questions on similar topics and I tried booting Ubuntu as a live cd and typing "sudo os-prober" in the terminal and "sudo apt-get -y remove dmraid", I also typed "sudo fdisk -lu".In the end I've installed Ubuntu 12.04.1 inside windows with wubi, but I would still like to find out how should I install it alongside Windows.
After the wubi instalation I typed again "sudo fdisk -lu" in the terminal and this is what it shows:

lucian@ubuntu:~$ sudo fdisk -lu
[sudo] password for lucian: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x27375a4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   317939711   158866432    7  HPFS/NTFS/exFAT
/dev/sda3       317939712   420341759    51201024    f  W95 Ext'd (LBA)
/dev/sda4       420341760   625139711   102398976    7  HPFS/NTFS/exFAT
/dev/sda5       317941760   420341759    51200000    7  HPFS/NTFS/exFAT
lucian@ubuntu:~$ 

I also typed "sudo os-prober" and this is the result :

lucian@ubuntu:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain

---

### Post by fantab on 2013-12-10
The installer needs to see some space for it to run. Either have a linux partition or 'unallocated space' for the ubuntu installer to work.
You can 'Shrink' a Windows partition to make space for ubuntu.

Also make sure that your Windows is NOT 'Hibernating' when you shut it down. Shut down windows properly...

Post the output of:

```
sudo parted -l
```

---

### Post by lucian.andercou on 2013-12-10
I shrinked 50 GB out of my Windows D:\ drive for Ubuntu, also, Windows was not hibernating at shutdown. 
This is the output of "sudo parted -l" :

lucian@ubuntu:~$ sudo parted -l
[sudo] password for lucian: 
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?                                                                   

I don't know how to answer the question it asks.

---

### Post by fantab on 2013-12-10
Say 'Yes' first.
Then try 'no'.

---

### Post by oldfred on 2013-12-10
I do not know if parted will remove the backup gpt partition table.

Windows 7 standard install from DVD only installs in BIOS boot mode which has to have MBR partitions. So if drive was gpt, Windows will convert drive to MBR(msdos) but incorrectly leaves the backup gpt partition table. Often fixparts is the only easy way to fix that issue.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

