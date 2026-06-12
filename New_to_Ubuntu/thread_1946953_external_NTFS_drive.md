---
title: "external NTFS drive"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by JodiBosa on 2012-03-25
I am no longer able to mount an external USB drive that was never more than 15% full, less than 6months old, infrequently used, and unlikely to have been mishandled.  Right before this failure, it was half way through writing a ~3GB file - but the drive had several other files of this size.
'mount' tells me to run chkdsk on Windows except I am reluctant to do this until I either do a drive backup or am sure this won't cause data loss.

mount /dev/sdd1 /mnt

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



More info:


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





So:
 1) What is the best way to backup the drive - use dd?
 2) How trustworthy is Windows chkdsk?
 
 Thanks.

---

### Post by NikTh on 2012-03-25
> **JodiBosa said:**
> 
 2) How trustworthy is Windows chkdsk?
 

Hello , 
at this time i think that windows chkdsk its trustworthy enough . More trustworthy than ntfsfix command. Do not forget that ntfs its Microsoft's file system . So if you have a pc with windows , do what message told you.

---

### Post by JC Cheloven on 2012-03-25
> **NikTh said:**
> at this time i think that windows chkdsk its trustworthy enough . More trustworthy than ntfsfix command. Do not forget that ntfs its Microsoft's file system . So if you have a pc with windows , do what message told you.
+1

Also, how was the disk formatted?  If problems persist, you may format it (as ntfs) from linux' gparted. It seems that w7 formats the ntfs partitions with a different criteria for sector/cylinders boundaries (I admittedly don't understand completely the issue). I use intensively external usb disks daily, and never got a problem that way, either using them under linux or win2. 

JC

---

### Post by BertN45 on 2012-03-25
+1

For problems with ntfs chkdsk is the best.

---

### Post by Mark Phelps on 2012-03-26
Sorry ... but although we have ntfsfix in Linux, it can only repair simple filesystem problems.  

At some point, to completelyn repair NTFS problems, you have no choice other than to connect the drive to an MS Windows PC and run CHKDSK.

---

