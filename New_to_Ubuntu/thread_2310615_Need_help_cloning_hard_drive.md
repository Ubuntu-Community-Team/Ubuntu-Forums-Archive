---
title: "Need help cloning hard drive"
date: 2016-01-20
forum: New to Ubuntu
---

### Post by heather8 on 2016-01-20
I need help cloning my dying hard drive on my laptop to an external hard drive.  I am running ubuntu through a usb memory stick to access my files.  I need everything that is on that hard drive to be cloned over.

ETA:  this is what I get when I run sudo fdisk - l

```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

```

---

### Post by newbie-user on 2016-01-20
Use the dd command.
[https://wiki.archlinux.org/index.php/disk_cloning#Using_dd]("https://wiki.archlinux.org/index.php/disk_cloning#Using_dd")
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/]("http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/")

---

### Post by heather8 on 2016-01-22
Followed the information given in the second link.  This is what I got:

```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe28236a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *      206848  1953522687   976657920    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe28236a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *      206848  1953522687   976657920    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdc
dd: error reading &#8216;/dev/sda&#8217;: Input/output error
15268408+0 records in
15268408+0 records out
7817424896 bytes (7.8 GB) copied, 4500.23 s, 1.7 MB/s
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
ubuntu@ubuntu:~$ 

```

So....what does this mean?

---

