---
title: "Can't read external hard drive"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by digvijay91 on 2012-02-25
Hey,
I have a Seagate 500 GB external hard drive and ubuntu can't read it. Also I am using ubuntu 10.10. I was trying to install a linux distribution. I had it's iso file and i tried using "Startup disk creator" to make my external hard drive executable. Anyways i thought i'd first erase the hard drive but it gave me an error on doing so which i can't remember. Then i tried formatting the external hard drive on which it gave me an error again. Then it just disappeared. Then when i tried re-connecting it, it wouldn't mount. 
I looked up some posts but none which seemed to have the same problem as mine. Anyways i'll post the common commands that were used:
while the drive is connected
**lsusb**
**sudo fdisk -l**
And after disconnecting the device and re-connecting it
**dmesg | tail -n 20**
```
digvijay@digvijay-Studio-1555:/$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0bc2:2300 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
digvijay@digvijay-Studio-1555:/$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          25      200781   de  Dell Utility
/dev/sda2              26        1984    15728640    7  HPFS/NTFS
/dev/sda3   *        1984       26478   196748276    7  HPFS/NTFS
/dev/sda4           26478       38914    99890177    f  W95 Ext'd (LBA)
/dev/sda5           26478       36239    78405273+   7  HPFS/NTFS
/dev/sda6           38671       38914     1952768   82  Linux swap / Solaris
/dev/sda7           36239       38670    19530752   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aeebe

   Device Boot      Start         End      Blocks   Id  System
digvijay@digvijay-Studio-1555:/$ dmesg | tail -n 20
[ 2932.072953] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[ 2932.076302] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[ 2932.076315]  sdb:
[ 2932.129066] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[ 2932.129071] sd 14:0:0:0: [sdb] Attached SCSI disk
[ 3023.665063] FAT: invalid media value (0x00)
[ 3023.665073] VFS: Can't find a valid FAT filesystem on dev sdb.
[ 3944.688902] usb 2-3: USB disconnect, address 7
[ 3952.296067] usb 2-3: new high speed USB device using ehci_hcd and address 8
[ 3952.432074] scsi15 : usb-storage 2-3:1.0
[ 3953.433319] scsi 15:0:0:0: Direct-Access     Seagate  Portable         0130 PQ: 0 ANSI: 4
[ 3953.434935] sd 15:0:0:0: Attached scsi generic sg2 type 0
[ 3953.436222] sd 15:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 3953.436954] sd 15:0:0:0: [sdb] Write Protect is off
[ 3953.436962] sd 15:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[ 3953.436971] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3953.441172] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3953.441186]  sdb:
[ 3953.500347] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3953.500351] sd 15:0:0:0: [sdb] Attached SCSI disk
digvijay@digvijay-Studio-1555:/$ 

```

I was really excited to install the linux distribution but...
Please help.

Yours,
Digvijay

---

### Post by digvijay91 on 2012-02-25
Hehe,
so i solved the problem. I just went to Disk utilities and formatted my drive and created a new partition. Done!
I forgot ubuntu was awesome. :D

Digvijay

---

