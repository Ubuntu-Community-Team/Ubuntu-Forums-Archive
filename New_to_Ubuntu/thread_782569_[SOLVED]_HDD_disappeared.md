---
title: "[SOLVED] HDD disappeared"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by oldtom on 2008-05-05
Hi All,
Installed Ubuntu on my main HDD which has XP. At bootup, now have an option to boot into XP or Ubuntu and all this goes off without a hitch.

But I also have another HDD installed on my machine. It's D:\ in win. After Installing Ubuntu, this drive has disappeared when I search for it in win. Linux programs see it as normal but in win it has disappeared.

How can I get it back as it's now not accessable in win. It's formatted as fat32 BTW and my main HDD is an ntfs partition.

Mystery! #-o

---

### Post by hyper_ch on 2008-05-05
Post the output of:

```

sudo fdisk -l

```

---

### Post by fahadsadah on 2008-05-05
Please type the following command into a terminal, and paste the output here:
```
sudo fdisk -l /dev/sda && sudo fdisk -l /dev/sdb
```
You may be asked to enter a password. If so, please do.
Thank you very much.

EDIT: Woops, someone beat me to it!
My command is better, anyway =]

---

### Post by oldtom on 2008-05-05
OutPut:-
user1@user1-desktop:~$ sudo fdisk -l
[sudo] password for user1: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c0b1c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
/dev/sda2           19457       19457        8032+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1058

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3191    25631676    b  W95 FAT32

Disk /dev/sdg: 1030 MB, 1030750208 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fbb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         125     1004031    b  W95 FAT32

Disk /dev/sdh: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dbfb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1         501     4024251    b  W95 FAT32

Disk /dev/sdi: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023686

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1         125     1004031    6  FAT16

End of Output of sudo fdisk -l





> **hyper_ch said:**
> Post the output of:

```

sudo fdisk -l

```

---

### Post by oldtom on 2008-05-05
Result from typing your suggestion.
user1@user1-desktop:~$ sudo fdisk -l /dev/sda && sudo fdisk -l /dev/sdb

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c0b1c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
/dev/sda2           19457       19457        8032+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1058

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3191    25631676    b  W95 FAT32







> **fahadsadah said:**
> Please type the following command into a terminal, and paste the output here:
```
sudo fdisk -l /dev/sda && sudo fdisk -l /dev/sdb
```
You may be asked to enter a password. If so, please do.
Thank you very much.

EDIT: Woops, someone beat me to it!
My command is better, anyway =]

---

### Post by hyper_ch on 2008-05-05
in windows try the disk manager:  [http://support.microsoft.com/kb/309000](http://support.microsoft.com/kb/309000)

---

