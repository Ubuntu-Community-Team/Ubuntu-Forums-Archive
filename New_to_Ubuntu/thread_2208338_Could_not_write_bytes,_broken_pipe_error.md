---
title: "Could not write bytes, broken pipe error"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by Bronny_Jones on 2014-02-27
I installed ubuntu 12.04 a few days ago, using an USB stick, havent had any issues, then I dont know what i've done i was just watching youtube vids when my laptop suddenly crashed so i restarted and this error came up, could not write bytes, broken pipe, currently on my ipod to post this, i installed ubuntu over windows so its the only OS on there. Help?!

---

### Post by Bashing-om on 2014-02-27
Bronny_Jones; Hi ! Welcome to the forum .

Let's presuppose that the file system is now in an inconsistent state.
From the liveUSB, so the target filesystem is not mounted. (bios boot priority reset)
Boot the liveUSB -> "try ubuntu" mode -> terminal :
Assuming there is only 1 hard disk installed on your system, AND that /root is on the 1st partition; else adjust the target hard drive,
Run terminal commands:
e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```
If there are doubts and you are unsure, post pack to us the output - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

For our inspection and advisement on the exact commands to run to effect the check/repair of your file system.

Once the file system check/repair is completed, what results when you attempt to boot into your install ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bronny_Jones on 2014-03-02
for the e2fsck check i got;
```
 
  275392 inodes used (0.61%)
     927 non-contiguous files (0.3%)
     232 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 232346/145/2
10093539 blocks used (5.56%)
       0 bad blocks
       1 large file

  190298 regular files
   27230 directories
      57 character device files
      25 block device files
       1 fifo
       5 links
   57760 symbolic links (42796 fast symbolic links)
      12 sockets

```

then for fdisk -lu i got;
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1452673023   726335488   83  Linux
/dev/sda2      1452675070  1465147391     6236161    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1452675072  1465147391     6236160   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16080961536 bytes
128 heads, 63 sectors/track, 3894 cylinders, total 31408128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       10408    15619814     7804703+   c  W95 FAT32 (LBA)
/dev/sdb2        15620094    31406079     7892993    5  Extended
/dev/sdb5        15620096    18931711     1655808   83  Linux
/dev/sdb6        18933760    31406079     6236160   82  Linux swap / Solaris

```

for parted -l i got;
```

Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  744GB  744GB   primary   ext4            boot
 2      744GB   750GB  6386MB  extended
 5      744GB   750GB  6386MB  logical   linux-swap(v1)


Model: hp USB FLASH DRIVE (scsi)
Disk /dev/sdb: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      5329kB  7997MB  7992MB  primary   fat32        boot, lba
 2      7997MB  16.1GB  8082MB  extended
 5      7997MB  9693MB  1696MB  logical
 6      9694MB  16.1GB  6386MB  logical

```

and for parted dev/sda unit s print i got;
```

Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        1452673023s  1452670976s  primary   ext4            boot
 2      1452675070s  1465147391s  12472322s    extended
 5      1452675072s  1465147391s  12472320s    logical   linux-swap(v1)

```

---

### Post by Bashing-om on 2014-03-02
Bronny_Jones; Hey,

Looking good, the file system is intact. However, we still have not determined the source of the problem.
What results from:
Boot the install, at the GUI login do a key combo ctl+alt+F1 -> text console;
Login here with username and password (no response to the screen).
Now we need to know what happens here with terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

A thought, many times this situation is brought on by a broken proprietary driver. More info will be given by the outputs of the update/upgrade process.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2014-03-02
FWIW, I get this message sometimes when shutting down. I researched it and learned it has something to do with the amount of information needing to be written before the process can be completed. It happens to folks during boot up as well. Nothing is permanently broken and as Bashing-om says, you're system is looking good.

---

