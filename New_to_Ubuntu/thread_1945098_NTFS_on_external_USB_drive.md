---
title: "NTFS on external USB drive"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by JodiBosa on 2012-03-22
I have an external USB Seagate drive that failed on me while trying to write a ~3GB file.  At the point of failure, the file was roughly 1.6GB in size.  It's hard to imagine this is a hardware failure since the drive is less than 6months old, has been used infrequently, has not to my knowledge been dropped/mishandled, is less than 15% full (it's most ever).

I cannot remember whether I reformatted it or not after purchase and was recently thinking it was FAT - however all indications now say it is/was NTFS.

I would typically:
        1) attach external Seagate drive using USB
        2) mount /dev/sdd1 /mnt

The drive is not in my fstab (I boot off a live CD).

From memory, the partition is nothing unusual - consists of maybe a couple dozen multi-GB files (mostly ISO's) and several thousand smaller files.

I have not (yet) performed anything potentially damaging - such as running "chkdsk" on Windows.  I don't mind paying another $60 for a duplicate drive and temporarily use something like dd to copy data to before performing further actions (e.g. chkdsk).

Is it possible that it was a FAT partition but that Linux/Ubuntu mounted it as NTFS??




fdisk -l /dev/sdd1

```
Disk /dev/sdd1: 500.1 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdd1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdd1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdd1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdd1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```



sfdisk -uS -l /dev/sdd

```
Disk /dev/sdd: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1            63 976768127  976768065   7  HPFS/NTFS
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty
```




parted /dev/sdd1
```
GNU Parted 2.2
Using /dev/sdd1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: Unknown (unknown)
Disk /dev/sdd1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  500GB  500GB  ntfs
```


mount -t auto /dev/sdd1 /mnt
```
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

mount -t ntfs-3g /dev/sdd1 /mnt
```
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```


mount -t ntfs-3g /dev/sdd /mnt
```
NTFS signature is missing.
Failed to mount '/dev/sdd': Invalid argument
The device '/dev/sdd' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

dmesg
```
[  297.412154] usb 2-1: new high speed USB device number 4 using ehci_hcd
[  297.547106] scsi7 : usb-storage 2-1:1.0
[  298.549376] scsi 7:0:0:0: Direct-Access     Seagate  FreeAgent GoFlex 0148 PQ: 0 ANSI: 4
[  298.550384] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  298.552605] sd 7:0:0:0: [sdd] 976773167 512-byte logical blocks: (500 GB/465 GiB)
[  298.553092] sd 7:0:0:0: [sdd] Write Protect is off
[  298.553098] sd 7:0:0:0: [sdd] Mode Sense: 1c 00 00 00
[  298.553102] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  298.555858] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  298.626398]  sdd: sdd1
[  298.628088] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  298.628093] sd 7:0:0:0: [sdd] Attached SCSI disk
[  364.995127] sd 7:0:0:0: [sdd] Unhandled sense code
[  364.995134] sd 7:0:0:0: [sdd]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  364.995140] sd 7:0:0:0: [sdd]  Sense Key : Medium Error [current]
[  364.995147] sd 7:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  364.995155] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 24 53 1c df 00 00 20 00
[  364.995170] end_request: critical target error, dev sdd, sector 609426655
[  364.995178] Buffer I/O error on device sdd1, logical block 609426592
[  364.995185] Buffer I/O error on device sdd1, logical block 609426593
[  364.995189] Buffer I/O error on device sdd1, logical block 609426594
[  364.995193] Buffer I/O error on device sdd1, logical block 609426595
[  364.995198] Buffer I/O error on device sdd1, logical block 609426596
[  364.995202] Buffer I/O error on device sdd1, logical block 609426597
[  364.995207] Buffer I/O error on device sdd1, logical block 609426598
[  364.995211] Buffer I/O error on device sdd1, logical block 609426599
[  364.995220] Buffer I/O error on device sdd1, logical block 609426600
[  364.995224] Buffer I/O error on device sdd1, logical block 609426601
[  367.383378] sd 7:0:0:0: [sdd] Unhandled sense code
[  367.383384] sd 7:0:0:0: [sdd]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  367.383390] sd 7:0:0:0: [sdd]  Sense Key : Medium Error [current]
[  367.383397] sd 7:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  367.383411] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 24 53 1c df 00 00 08 00
[  367.383422] end_request: critical target error, dev sdd, sector 609426655
[  369.771642] sd 7:0:0:0: [sdd] Unhandled sense code
[  369.771647] sd 7:0:0:0: [sdd]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  369.771653] sd 7:0:0:0: [sdd]  Sense Key : Medium Error [current]
[  369.771660] sd 7:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  369.771667] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 24 53 1c df 00 00 08 00
[  369.771686] end_request: critical target error, dev sdd, sector 609426655
[  414.628521] sd 7:0:0:0: [sdd] Unhandled sense code
[  414.628527] sd 7:0:0:0: [sdd]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  414.628533] sd 7:0:0:0: [sdd]  Sense Key : Medium Error [current]
[  414.628540] sd 7:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  414.628548] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 24 53 1c df 00 00 20 00
[  414.628566] end_request: critical target error, dev sdd, sector 609426655
[  414.628571] quiet_error: 38 callbacks suppressed
[  414.628574] Buffer I/O error on device sdd1, logical block 609426592
[  414.628579] Buffer I/O error on device sdd1, logical block 609426593
[  414.628583] Buffer I/O error on device sdd1, logical block 609426594
[  414.628586] Buffer I/O error on device sdd1, logical block 609426595
[  414.628589] Buffer I/O error on device sdd1, logical block 609426596
[  414.628593] Buffer I/O error on device sdd1, logical block 609426597
[  414.628596] Buffer I/O error on device sdd1, logical block 609426598
[  414.628599] Buffer I/O error on device sdd1, logical block 609426599
[  414.628606] Buffer I/O error on device sdd1, logical block 609426600
[  414.628609] Buffer I/O error on device sdd1, logical block 609426601
[  417.082761] sd 7:0:0:0: [sdd] Unhandled sense code
[  417.082767] sd 7:0:0:0: [sdd]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  417.082774] sd 7:0:0:0: [sdd]  Sense Key : Medium Error [current]
[  417.082781] sd 7:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  417.082788] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 24 53 1c df 00 00 08 00
[  417.082803] end_request: critical target error, dev sdd, sector 609426655
[  419.372398] sd 7:0:0:0: [sdd] Unhandled sense code
[  419.372404] sd 7:0:0:0: [sdd]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  419.372410] sd 7:0:0:0: [sdd]  Sense Key : Medium Error [current]
[  419.372417] sd 7:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  419.372424] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 24 53 1c df 00 00 08 00
[  419.372439] end_request: critical target error, dev sdd, sector 609426655
```

lsusb | grep -i Seagate
```
Bus 002 Device 004: ID 0bc2:5021 Seagate RSS LLC FreeAgent GoFlex USB 2.0
root@root:~# dmesg | grep -i Seagate
[  298.549376] scsi 7:0:0:0: Direct-Access     Seagate  FreeAgent GoFlex 0148 PQ: 0 ANSI: 4
```



mount -t vfat /dev/sdd1 /mnt
```
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```dmesg
```
[  875.631724] FAT: bogus number of reserved sectors
[  875.631731] VFS: Can't find a valid FAT filesystem on dev sdd1.
```



udisks --dump

```
========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdd
  native-path:                 /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/host7/target7:0:0/7:0:0:0/block/sdd
  device:                      8:32
  device-file:                 /dev/sdd
    presentation:              /dev/sdd
    by-id:                     /dev/disk/by-id/usb-Seagate_FreeAgent_GoFlex_NA0ERPPN-0:0
    by-path:                   /dev/disk/by-path/pci-0000:00:1d.7-usb-0:1:1.0-scsi-0:0:0:0
  detected at:                 Wed 21 Mar 2012 06:39:58 PM EDT
  system internal:             0
  removable:                   0
  has media:                   1 (detected at Wed 21 Mar 2012 06:39:58 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:
  presentation icon:
  size:                        500107861504
  block size:                  512
  job underway:                no
  usage:
  type:
  version:
  uuid:
  label:
  partition table:
    scheme:                    mbr
    count:                     1
  drive:
    vendor:                    Seagate
    model:                     FreeAgent GoFlex
    revision:                  0148
    serial:                    NA0ERPPN
    WWN:
    detachable:                1
    can spindown:              1
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:
      compat:
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 Updated at Wed 21 Mar 2012 06:40:29 PM EDT
      overall assessment:      Disk has a few bad sectors
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate          89| 89|  6   good    27608789    Pre-fail Online
 spin-up-time                 98| 98|  0    n/a    0           Pre-fail Online
 start-stop-count            100|100| 20   good    97          Old-age  Online
 reallocated-sector-count     85| 85| 36   good    324 sectors Pre-fail Online
 seek-error-rate             100|253| 30   good    270103      Pre-fail Online
 power-on-hours              100|100|  0    n/a    1.9 days    Old-age  Online
 spin-retry-count            100|100| 97   good    0           Pre-fail Online
 power-cycle-count           100| 37| 20   good    54          Old-age  Online
 end-to-end-error            100|100| 99   good    0           Old-age  Online
 reported-uncorrect            1|  1|  0    n/a    201 sectors Old-age  Online
 command-timeout             100|100|  0    n/a    0           Old-age  Online
 high-fly-writes             100|100|  0    n/a    0           Old-age  Online
 airflow-temperature-celsius  71| 65| 45   good    29C / 84.2F Old-age  Online
 g-sense-error-rate          100|100|  0    n/a    0           Old-age  Online
 power-off-retract-count     100|100|  0    n/a    20          Old-age  Online
 load-cycle-count            100|100|  0    n/a    1552        Old-age  Online
 temperature-celsius-2        29| 40|  0    n/a    29C / 84.2F Old-age  Online
 hardware-ecc-recovered       47| 47|  0    n/a    27608789    Old-age  Online
 current-pending-sector      100|100|  0    n/a    2 sectors   Old-age  Online
 offline-uncorrectable       100|100|  0    n/a    2 sectors   Old-age  Offline
 udma-crc-error-count        200|200|  0    n/a    0           Old-age  Online

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdd1
  native-path:                 /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/host7/target7:0:0/7:0:0:0/block/sdd/sdd1
  device:                      8:33
  device-file:                 /dev/sdd1
    presentation:              /dev/sdd1
    by-id:                     /dev/disk/by-id/usb-Seagate_FreeAgent_GoFlex_NA0ERPPN-0:0-part1
    by-id:                     /dev/disk/by-uuid/----REMOVED-----
    by-path:                   /dev/disk/by-path/pci-0000:00:1d.7-usb-0:1:1.0-scsi-0:0:0:0-part1
  detected at:                 Wed 21 Mar 2012 06:39:58 PM EDT
  system internal:             0
  removable:                   0
  has media:                   1 (detected at Wed 21 Mar 2012 06:39:58 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:
  presentation icon:
  size:                        500105249280
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:
  uuid:                        ----REMOVED-----
  label:                       FreeAgent GoFlex Drive
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sdd
    scheme:                    mbr
    number:                    1
    type:                      0x07
    flags:
    offset:                    32256
    alignment offset:          0
    size:                      500105249280
    label:
    uuid:
```

*****WINDOWS*****
C:\Windows\system32>chkdsk H:
```
The type of the file system is NTFS.
Volume label is FreeAgent GoFlex Drive.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
Attribute record (128, "") from file record segment 38019sed)
is corrupt.
File record segment 241592 is unreadable.le records processed)
File record segment 241593 is unreadable.le records processed)
File record segment 241594 is unreadable.le records processed)
File record segment 241595 is unreadable.le records processed)
  241616 file records processed.
File verification completed.
  110 large file records processed.

Errors found.  CHKDSK cannot continue in read-only mode.
```

---

### Post by JodiBosa on 2012-03-22
I forgot to add my question - what can I do to get this partition straightened out?

---

### Post by Mark Phelps on 2012-03-22
When you run CHKDSK, if not doing it from the Recovery Console (which is not available in Vista and Win7), the default is read-only.

To actually fix the problems, you need to add the "/f" option.

---

### Post by JodiBosa on 2012-03-22
I was trying to avoid running "chkdsk /f" before either being fairly sure it won't cause further problems - doing a drive backup.  In the later, how hard is it to use 'dd'?   and do I need a 2nd drive, or can I write it to a file on another drive?

---

