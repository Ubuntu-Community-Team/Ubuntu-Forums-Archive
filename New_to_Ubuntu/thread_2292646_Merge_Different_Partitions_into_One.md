---
title: "Merge Different Partitions into One"
date: 2015-08-29
forum: New to Ubuntu
---

### Post by MathManiac on 2015-08-29
**EDIT:** I realized that, even though I have to mount them separately, I don't need to for what I need to do (make backup) - I can just use /dev/sdb itself to make my backups.

Hello,
I've started using Raspberry Pi and installed Ubuntu Mate - because, IMHO, the Raspian OS looks outdated.

While it does look outdated, I wanted to keep a backup of the SD card in case something bad happens with that and/or the SD card I'm using for Ubuntu Mate. I plugged the SD card into a USB adapter, and plugged *that* into the USB port in Ras-pi (along with another USB drive to hold the backup). That's when three different devices start showing up on my desktop both as icons and windows. While I was extremely confused why this happened, doing an **lsblk** command showed that it was just different partitions of the same drive. I know that there are more than three folders of the SD Card (I also plugged it in a Windows Computer), so I separately unmounted each directory and then mounted the main drive on newly-created directory /mnt/sdb. I got this error:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

dmesg | tail shows this:

```

[ 3429.647026] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[ 3429.686994] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[ 3518.520849] F2FS-fs (sdb): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 3518.520879] F2FS-fs (sdb): Can't find valid F2FS filesystem in 1th superblock
[ 3518.522211] F2FS-fs (sdb): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 3518.522963] F2FS-fs (sdb): Can't find valid F2FS filesystem in 2th superblock
[ 3518.522996] F2FS-fs (sdb): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 3518.523010] F2FS-fs (sdb): Can't find valid F2FS filesystem in 1th superblock
[ 3518.523025] F2FS-fs (sdb): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 3518.523037] F2FS-fs (sdb): Can't find valid F2FS filesystem in 2th superblock
```

I am stumped to know what this means. Can somebody help me?

[SIZE=4]Extra Info:
[SIZE=2]
[B]Device In Question:
[/B]sdb
SD/MicroSD to USB Adapter connected to MicroUSB w/ NOOBS[/SIZE]
[SIZE=2][B]lsblk pre-unmounting:
[/B]
```
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb           8:16   1   7.4G  0 disk 
&#9500;&#9472;sdb1        8:17   1 814.3M  0 part 
&#9500;&#9472;sdb2        8:18   1     1K  0 part 
&#9500;&#9472;sdb3        8:19   1    32M  0 part /media/sam/SETTINGS
&#9500;&#9472;sdb5        8:21   1    60M  0 part /media/sam/boot
&#9492;&#9472;sdb6        8:22   1   6.5G  0 part /media/sam/root
mmcblk0     179:0    0   7.4G  0 disk 
&#9500;&#9472;mmcblk0p1 179:1    0    64M  0 part /boot/firmware
&#9492;&#9472;mmcblk0p2 179:2    0   7.3G  0 part /
```
[B]
Post- Unmounting:[/B]

```
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb           8:16   1   7.4G  0 disk 
&#9500;&#9472;sdb1        8:17   1 814.3M  0 part 
&#9500;&#9472;sdb2        8:18   1     1K  0 part 
&#9500;&#9472;sdb3        8:19   1    32M  0 part 
&#9500;&#9472;sdb5        8:21   1    60M  0 part 
&#9492;&#9472;sdb6        8:22   1   6.5G  0 part 
mmcblk0     179:0    0   7.4G  0 disk 
&#9500;&#9472;mmcblk0p1 179:1    0    64M  0 part /boot/firmware
&#9492;&#9472;mmcblk0p2 179:2    0   7.3G  0 part /
```

**Command to Mount:**
```
mount /dev/sdb /mnt/sdb
```
[/SIZE][/SIZE]

---

### Post by yancek on 2015-08-29
> then mounted the main drive on newly-created directory /mnt/sdb. I got this error:

You forgot to post the actual command you used to mount the partition so we don't know which partition you were trying to mount.  The error is often a result of trying to mount a partition using the incorrect filesystem type.

---

### Post by MathManiac on 2015-08-30
> **yancek said:**
> You forgot to post the actual command you used to mount the partition so we don't know which partition you were trying to mount.  The error is often a result of trying to mount a partition using the incorrect filesystem type.

I used **mount /dev/sdb /mnt/sdb**. I have no idea what filesystem the SD Card is. I tried vFat, ext3 and ext4.

---

### Post by deadflowr on 2015-08-30
/dev/sdb is a full [s]hard drive[/s] disk, you need to mount the individual partitions like /dev/sdb1

---

### Post by yancek on 2015-08-30
Use this command to show mounted and unmounted partitions and post the output here.

sudo parted -l(Lower Case Letter L in the command)

---

### Post by MathManiac on 2015-08-31
> **yancek said:**
> Use this command to show mounted and unmounted partitions and post the output here.

sudo parted -l(Lower Case Letter L in the command)

Here's the Result:
```
Model: Kingston DT 101 II (scsi)
Disk /dev/sda: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:


Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4005MB  4000MB  primary  fat32        boot, lba




Model: Multiple Flash Reader (scsi)
Disk /dev/sdc: 7948MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:


Number  Start   End     Size    Type      File system  Flags
 1      4194kB  858MB   854MB   primary   fat32        lba
 2      860MB   7915MB  7055MB  extended
 5      864MB   927MB   62.9MB  logical   fat32        lba
 6      931MB   7915MB  6984MB  logical   ext4
 3      7915MB  7948MB  33.6MB  primary   ext4




Model: SD SS08G (sd/mmc)
Disk /dev/mmcblk0: 7948MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  68.2MB  67.1MB  primary  fat16        boot, lba
 2      68.2MB  7948MB  7880MB  primary  ext4

```
**NOTE:** I ran this command while running **dd** to do a test backup on a Kingston Thumbdrive, if that means anything to you.
I believe the drive I want to merge is the Multiple Flash Reader.

---

### Post by sandyd on 2015-08-31
Try using
```

sudo mount /dev/sdc6 */path/to/folder*
```
Where */path/to/folder* is the mount point

---

