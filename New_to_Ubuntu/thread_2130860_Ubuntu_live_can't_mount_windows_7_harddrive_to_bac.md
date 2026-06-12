---
title: "Ubuntu live can't mount windows 7 harddrive to backup files"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by lxx33 on 2013-03-30
A friend of my brought his notebook, because it won't boot anymore.
I was thinking to do a fresh install but he wan't to save his files.
Have starting the notebook with a live ubuntu dvd i'd figured i could make a backup of his files. But the most important parition won't mount.

All the partition mount except the partition where windows 7 installed on (and my documents my pictures ect.ect.)
If i put the drive in a windows machine as slave and try to access windows ask for a format.

```
ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf7f49dde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1419773951   709682176    7  HPFS/NTFS/exFAT
/dev/sda3      1419773952  1464936447    22581248    7  HPFS/NTFS/exFAT
/dev/sda4      1464936448  1465147119      105336    c  W95 FAT32 (LBA)

Disk /dev/sdb: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders, total 494080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             101      494079      246989+   6  FAT16
root@ubuntu:~# 


```

it's the /dev/sda2 that i want to open and to backup the files.

also tried:

```
root@ubuntu:/media/disk# mkdir /media/backup
root@ubuntu:/media/disk# mount -t ntfs-3g /dev/sda2 /media/backup/ -o force
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
root@ubuntu:/media/disk# 


```

---

### Post by mharv on 2013-03-30
The error message is telling you that the harddrive named sda2 is either A) damaged or not compatible B) the file system is corrupted. The only case you have control over is the latter but I am not a file system expert so I can not tell you exactly how to proceed. If noone else can give you a better suggestion on recovering files in case B then I recommend looking into [http://www.sleuthkit.org/](http://www.sleuthkit.org/). But also goole "'dmraid' documentation" for more details regarding: "The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory"

---

### Post by DuckHook on 2013-03-30
It sounds like your friend's computer may have a corrupted partition table, which could be why he can't boot and also why Linux cannot mount the needed partition. Did you do as the error message suggested and try running```
chkdsk /f
``` from Windows? The /f switch tells chkdsk to fix errors.

---

### Post by lxx33 on 2013-03-30
> **mharv said:**
> The error message is telling you that the harddrive named sda2 is either A) damaged or not compatible B) the file system is corrupted. 
I think it's B, because al the other partitions are accessable.

Hope maby somebody else have a good tip on how to recover the files.

---

### Post by mharv on 2013-03-30
Googled "ntfs recovery" this is what i got: 
[http://www.diskinternals.com/](http://www.diskinternals.com/) 
or
[http://thewalter.net/stef/software/scrounge/](http://thewalter.net/stef/software/scrounge/) (The author says this is not thoroughly tested so copy an image of the partition somewhere before using, you should do that anyways)

---

### Post by DuckHook on 2013-03-30
> **lxx33 said:**
> ...Hope maby somebody else have a good tip on how to recover the files.

As previously asked, have you run chkdsk?

Also, you will likely have better success asking about Windows issues on a Windows forum.

---

### Post by lxx33 on 2013-03-31
notyet tried chkdsk /f because it's won't boot, and i don't know how to get a dos like promt. I will let you know if the chkdsk is working as soon as i know how to do it ;)

---

### Post by lxx33 on 2013-03-31
> **lxx33 said:**
> notyet tried chkdsk /f because it's won't boot, and i don't know how to get a dos like promt. I will let you know if the chkdsk is working as soon as i know how to do it ;)

Checkdisk don't work for me. If i make and Bootable CHKDSK (Create a System Repair Disc) on a working windows 7 terminal and start the notebook with the disc the computer almost freezes. and cannot go to a promt where i can chkdsk.

But it's getting more a more a problem that i cannot fix with my ubuntu cd, so maby try a different forum.

tnx anyways.

---

### Post by mharv on 2013-03-31
[http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)

---

### Post by lxx33 on 2013-04-01
tnx for the link.

It did not help me this time, because i reinstalled windows without backing up. Even with data recovery software i did not manage, so after 2 days of fiddling, i gave up.

Will try it next time, so still many tnx.

---

