---
title: "Can't mount external FreeAgent GoFlex Drive"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by pwest1 on 2013-04-16
I had no problems mounting this drive on the same computer, but today, while using it for the first time in a month or so, it has failed to mount. Sorry if this is a really simple query. Here is the output from running fdisk-l. Any ideas would be greatly appreciated. Thanks.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bdeaa


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   602611711   301304832   83  Linux
/dev/sda2       602613758   625141759    11264001    5  Extended
/dev/sda5       602613760   625141759    11264000   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)


Disk /dev/sdb: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xac75909d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   732564062  2930256000    7  HPFS/NTFS/exFAT
peter@peter-laptop:~$ sudo mount -t ntfs /dev/sdb1 /media
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by Cheesemill on 2013-04-16
Have you done what it suggested?
> In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important!

This usually happens when you disconnect the drive without safely removing it first.

---

### Post by pwest1 on 2013-04-16
When I tried to access it via a netbook running Windows 7, it said the external drive was not accessible

---

### Post by alhefner on 2013-04-16
> **pwest1 said:**
> When I tried to access it via a netbook running Windows 7, it said the external drive was not accessible

What all have you done with the drive since you started using it? Does it still have the NTFS partition with the drivers and software that came preinstalled? How about plugging it in and checking out the status in Windows Device Manager to see if it can be enabled there? Also, if it's like mine, it's a USB interfaced device so, checking the status of your USB ports could offer some insight.

I'm only speculating here so, take it for what it's worth!

---

### Post by Mark Phelps on 2013-04-16
> **pwest1 said:**
> When I tried to access it via a netbook running Windows 7, it said the external drive was not accessible

Did you look to see if the "drive" was listed in the Disk Management utility -- but simply not assigned a drive letter?  Without a drive letter, Win7 can't access it -- but the Disk Management utility can "see" it.

If Disk Management can see it, try assigning a drive letter, and then run the file system check on it.

---

### Post by mushistereck on 2014-01-22
I use Ubuntu 12.04 and no windows so how can I boot into nwindows to fix this?

---

