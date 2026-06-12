---
title: "Problems with my 2GB pen drive"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by kl2bmark on 2008-10-13
Been having problems with my pen drive, tried reformatting it but it wont let me.


output of Fdisk -l
> Disk /dev/sdb: 2080 MB, 2080374784 bytes
1 heads, 32 sectors/track, 126976 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x9e414094

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2      126976     2031600    b  W95 FAT32
mark@ubuntu:~$ 



> [  790.325690] usb-storage: device found at 24
[  790.326034] usb-storage: waiting for device to settle before scanning
[  795.324913] usb-storage: device scan complete
[  795.326144] scsi 11:0:0:0: Direct-Access     Corsair  Flash Voyager    1.00 PQ: 0 ANSI: 0 CCS
[  795.328369] sd 11:0:0:0: [sdb] 4063232 512-byte hardware sectors (2080 MB)
[  795.332892] sd 11:0:0:0: [sdb] Write Protect is off
[  795.332905] sd 11:0:0:0: [sdb] Mode Sense: 00 26 00 00
[  795.332909] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[  795.336227] sd 11:0:0:0: [sdb] 4063232 512-byte hardware sectors (2080 MB)
[  795.339369] sd 11:0:0:0: [sdb] Write Protect is off
[  795.339381] sd 11:0:0:0: [sdb] Mode Sense: 00 26 00 00
[  795.339385] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[  795.339392]  sdb: sdb1
[  795.340362] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[  795.340426] sd 11:0:0:0: Attached scsi generic sg3 type 0
[  963.354481] end_request: I/O error, dev fd0, sector 0
[  975.536811] end_request: I/O error, dev fd0, sector 0
[  975.582003] cdrom: sr0: mrw address space DMA selected
[  975.605787] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[  994.634027] end_request: I/O error, dev fd0, sector 0
[ 1006.817560] end_request: I/O error, dev fd0, sector 0
[ 1018.999956] end_request: I/O error, dev fd0, sector 0
[ 1018.999970] printk: 6 messages suppressed.
[ 1018.999974] Buffer I/O error on device fd0, logical block 0
[ 1031.182377] end_request: I/O error, dev fd0, sector 0
[ 1031.182395] Buffer I/O error on device fd0, logical block 0
[ 1031.225314] cdrom: sr0: mrw address space DMA selected
[ 1031.249980] end_request: I/O error, dev sr0, sector 0
[ 1031.249994] Buffer I/O error on device sr0, logical block 0
[ 1031.252551] end_request: I/O error, dev sr0, sector 0
[ 1031.252565] Buffer I/O error on device sr0, logical block 0
[ 1076.023991] usb 7-4.1: reset high speed USB device using ehci_hcd and address 24
[ 1098.622244] end_request: I/O error, dev fd0, sector 0
[ 1110.805672] end_request: I/O error, dev fd0, sector 0
[ 1122.989201] end_request: I/O error, dev fd0, sector 0
[ 1122.989218] Buffer I/O error on device fd0, logical block 0
[ 1135.172562] end_request: I/O error, dev fd0, sector 0
[ 1135.172578] Buffer I/O error on device fd0, logical block 0
[ 1135.215580] cdrom: sr0: mrw address space DMA selected
[ 1167.112073] usb 7-4.1: reset high speed USB device using ehci_hcd and address 24
[ 1197.281053] usb 7-4.1: reset high speed USB device using ehci_hcd and address 24
[ 1214.145371] end_request: I/O error, dev fd0, sector 0
[ 1226.328019] end_request: I/O error, dev fd0, sector 0
[ 1238.509429] end_request: I/O error, dev fd0, sector 0
[ 1238.509446] Buffer I/O error on device fd0, logical block 0
[ 1250.693920] end_request: I/O error, dev fd0, sector 0
[ 1250.693935] Buffer I/O error on device fd0, logical block 0
[ 1250.737984] cdrom: sr0: mrw address space DMA selected
[ 1373.959226] FAT: bogus number of reserved sectors
[ 1373.959239] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 1395.924631] usb 7-4.1: reset high speed USB device using ehci_hcd and address 24
[ 1426.126603] usb 7-4.1: reset high speed USB device using ehci_hcd and address 24
[ 1469.005922] end_request: I/O error, dev fd0, sector 0
[ 1481.188439] end_request: I/O error, dev fd0, sector 0
[ 1493.371893] end_request: I/O error, dev fd0, sector 0
[ 1493.371909] Buffer I/O error on device fd0, logical block 0
[ 1496.609336] ehci_hcd 0000:00:10.3: remove, state 1
[ 1496.609736] usb usb7: USB disconnect, address 1
[ 1496.609943] usb 7-4: USB disconnect, address 23
[ 1496.610116] usb 7-4.1: USB disconnect, address 24
[ 1496.616365] ehci_hcd 0000:00:10.3: USB bus 7 deregistered
[ 1496.616895] ACPI: PCI interrupt for device 0000:00:10.3 disabled
[ 1496.617128] ehci_hcd 0000:00:08.2: remove, state 4
[ 1496.617317] usb usb3: USB disconnect, address 1
[ 1496.638937] ehci_hcd 0000:00:08.2: USB bus 3 deregistered
[ 1496.639040] ACPI: PCI interrupt for device 0000:00:08.2 disabled
[ 1496.856897] usb 5-2: new full speed USB device using uhci_hcd and address 5
[ 1497.017000] usb 5-2: configuration #1 chosen from 1 choice
[ 1497.018925] hub 5-2:1.0: USB hub found
[ 1497.020829] hub 5-2:1.0: 1 port detected
[ 1497.303744] usb 5-2.1: new full speed USB device using uhci_hcd and address 6
[ 1497.423831] usb 5-2.1: configuration #1 chosen from 1 choice
[ 1497.444189] scsi12 : SCSI emulation for USB Mass Storage devices
[ 1497.457229] usb-storage: device found at 6
[ 1497.459022] usb-storage: waiting for device to settle before scanning
[ 1502.459884] usb-storage: device scan complete
[ 1502.462866] scsi 12:0:0:0: Direct-Access     Corsair  Flash Voyager    1.00 PQ: 0 ANSI: 0 CCS
[ 1502.468868] sd 12:0:0:0: [sdb] 4063232 512-byte hardware sectors (2080 MB)
[ 1502.472926] sd 12:0:0:0: [sdb] Write Protect is off
[ 1502.472939] sd 12:0:0:0: [sdb] Mode Sense: 00 26 00 00
[ 1502.472943] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 1502.484829] sd 12:0:0:0: [sdb] 4063232 512-byte hardware sectors (2080 MB)
[ 1502.488846] sd 12:0:0:0: [sdb] Write Protect is off
[ 1502.488859] sd 12:0:0:0: [sdb] Mode Sense: 00 26 00 00
[ 1502.488863] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 1502.488870]  sdb: sdb1
[ 1502.532283] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 1502.532351] sd 12:0:0:0: Attached scsi generic sg3 type 0
[ 1505.553288] end_request: I/O error, dev fd0, sector 0
[ 1505.553304] Buffer I/O error on device fd0, logical block 0
[ 1505.596303] cdrom: sr0: mrw address space DMA selected
[ 1693.950553] end_request: I/O error, dev fd0, sector 0
[ 1706.131922] end_request: I/O error, dev fd0, sector 0
[ 1706.176588] cdrom: sr0: mrw address space DMA selected
[ 1706.199451] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 1727.160608] end_request: I/O error, dev fd0, sector 0
[ 1739.342031] end_request: I/O error, dev fd0, sector 0
[ 1751.522539] end_request: I/O error, dev fd0, sector 0
[ 1751.522555] Buffer I/O error on device fd0, logical block 0
[ 1763.703959] end_request: I/O error, dev fd0, sector 0
[ 1763.703975] Buffer I/O error on device fd0, logical block 0
[ 1861.002659] usb 5-2.1: reset full speed USB device using uhci_hcd and address 6
[ 1891.488521] usb 5-2.1: reset full speed USB device using uhci_hcd and address 6
[ 2024.245944] FAT: bogus number of reserved sectors
[ 2024.246328] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2125.357014] UDF-fs: No partition found (1)
[ 2125.552925] UDF-fs: No partition found (1)
[ 2125.901803] ISOFS: Unable to identify CD-ROM format.
[ 2126.163684] ISOFS: Unable to identify CD-ROM format.
[ 2126.171712] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 2126.174699] FAT: bogus number of reserved sectors
[ 2126.174715] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2126.185675] FAT: bogus number of reserved sectors
[ 2126.185691] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2126.587575] hfs: unable to find HFS+ superblock
[ 2126.602523] hfs: unable to find HFS+ superblock
[ 2126.709499] hfs: can't find a HFS filesystem on dev sdb1.
[ 2126.723512] hfs: can't find a HFS filesystem on dev sdb1.
[ 2126.735499] VFS: Can't find ext3 filesystem on dev sdb1.
[ 2126.746501] VFS: Can't find ext3 filesystem on dev sdb1.
[ 2126.806469] VFS: Can't find an ext2 filesystem on dev sdb1.
[ 2126.817618] VFS: Can't find an ext2 filesystem on dev sdb1.
[ 2126.906429] ReiserFS: sdb1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb1
[ 2126.926418] ReiserFS: sdb1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb1
[ 2127.105724] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[ 2127.107957] SGI XFS Quota Management subsystem
[ 2127.117468] XFS: bad magic number
[ 2127.117481] XFS: SB validate failed
[ 2127.132341] XFS: bad magic number
[ 2127.132354] XFS: SB validate failed
[ 2127.173048] JFS: nTxBlock = 8039, nTxLock = 64316
mark@ubuntu:~$ 

output of : sudo mkfs.ext3  /dev/sdb1

> mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
126976 inodes, 507900 blocks
25395 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=520093696
16 block groups
32768 blocks per group, 32768 fragments per group
7936 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Writing inode tables: done                            
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 38 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
mark@ubuntu:~$ 


any suggestions?

---

### Post by houbysoft.xf.cz on 2008-10-13
What is your problem, exactly? And from the mkfs output, it looks that it worked fine, could you post the output of
```

sudo mkdir /mnt/mountpoint
sudo mount /dev/sdb1 /mnt/mountpoint

```
?

---

### Post by homemadejam on 2008-10-13
Have you tried formatting it using Gnome Partition Editor?

Jam

---

### Post by kpkeerthi on 2008-10-13
Just unmount it and plug it in again and run **sudo fdisk -l**

---

### Post by kl2bmark on 2008-10-13
> **houbysoft.xf.cz said:**
> What is your problem, exactly? And from the mkfs output, it looks that it worked fine, could you post the output of
```

sudo mkdir /mnt/mountpoint
sudo mount /dev/sdb1 /mnt/mountpoint

```
?

error : you must specify the filesystem type


Yes I have tried the partition editor, and it comes up with a few errors.

I can't unmount it because according to ubuntu... its not mounted.

In the computer folder, the usb drive logo comes up, and when I double click it, it says that its unable to mount the drive.

---

### Post by kl2bmark on 2008-10-13
> **kpkeerthi said:**
> Just unmount it and plug it in again and run **sudo fdisk -l**

> mark@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x129f4644

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9587    77007546   83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 2080 MB, 2080374784 bytes
1 heads, 32 sectors/track, 126976 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x9e414094

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2      126976     2031600    b  W95 FAT32
mark@ubuntu:~$ 



still not able to mount it

---

### Post by Keen101 on 2008-10-13
I prefer the Gparted Live-CD myself.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

