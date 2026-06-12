---
title: "creating NTFS partition with fdisk"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by LRT on 2008-07-02
this is what i'm doing to format an NTFS partition with fdisk:

# fdisk /dev/sda
n (to create new partition)
p (for primary partition)
1 (for partition number)
default for First cylinder
t (change partition's system id)
1 (for partition number)
L (to view hex codes)
87 (for NTFS partition)
w (to write changes)

after this i mount the partition as follows:

```
mount -t ntfs /dev/sda1 /media/sda1
```

but i get this error:

```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

i'm not sure what i'm doing wrong. i'm sure i'm selecting the right device. do i have to create a NTFS file system??? i'm not sure how to do this.

---

### Post by Neo0351 on 2008-07-02
im not sure how to do it with fdisk but you can do it with gparted.  you just need to install ntfsprogs to be able to partition and formate ntfs with gparted.
```
sudo apt-get install ntfsprogs gparted
```

---

### Post by LRT on 2008-07-02
yes i know how to do it with gparted, but i want to know how to do it with fdisk.

---

### Post by cariboo on 2008-07-02
You created a partition, but you haven't created a file system, in other words you have to format your ntfs partition. Make sure you have ntfsprogs installed then in a terminal type:

```
mkntfs /dev/hdx
```

where hdx is your hard drive or partition.

Jim

---

### Post by stchman on 2008-07-02
> **LRT said:**
> yes i know how to do it with gparted, but i want to know how to do it with fdisk.

man fdisk

---

### Post by xitdedragon on 2009-01-09
Try using 7 instead of 86 or 87. Those are for volume sets.

---

### Post by lpbianco on 2010-02-10
After you create the partition with fdisk you need to create the filesystem on the drive. Type "mkfs -t ntfs /dev/sda1" (changing sda1 to whatever are your drive letters). After that you need to enter the drive into the fstab by typing "fsck -f -y /dev/sda1" again replacing the letters.

I hope I could help.

---

### Post by Teonline on 2010-03-31
Hi! You have to install the ntfs-3g package:

```
sudo aptitude install ntfs-3g
```

With this package installed you can create a NTFS Filesystem. The partition that you create with fdisk is not so important, you can create an NTFS filesystem on a FAT32 partition and it will have all the characteristics of NTFS (Windows will not recognize it btw)

To create the filesystem run

```
mkfs.ntfs /dev/sdb1
```

(instead of sdb1 put your partition address). 

To know witch filesystem you have on a device the command is:

```
file -s /dev/sdb1
```

---

### Post by honeybear on 2010-12-05
> **xitdedragon said:**
> Try using 7 instead of 86 or 87. Those are for volume sets.

what is the difference between 86 and 87 ?


```

Command (m for help): t
Partition number (1-6): 2
Hex code (type L to list codes): L

 0  Empty           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 1  FAT12           39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 2  XENIX root      3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 3  XENIX usr       40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 4  FAT16 <32M      41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 5  Extended        42  SFS             86  NTFS volume set da  Non-FS data    
 6  FAT16           4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 7  HPFS/NTFS       4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 8  AIX             4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 9  AIX bootable    50  OnTrack DM      93  Amoeba          e1  DOS access     
 a  OS/2 Boot Manag 51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 b  W95 FAT32       52  CP/M            9f  BSD/OS          e4  SpeedStor      
 c  W95 FAT32 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 e  W95 FAT16 (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  GPT            
 f  W95 Ext'd (LBA) 55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
10  OPUS            56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
11  Hidden FAT12    5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
12  Compaq diagnost 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
14  Hidden FAT16 <3 63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
16  Hidden FAT16    64  Novell Netware  af  HFS / HFS+      fb  VMware VMFS    
17  Hidden HPFS/NTF 65  Novell Netware  b7  BSDI fs         fc  VMware VMKCORE 
18  AST SmartSleep  70  DiskSecure Mult b8  BSDI swap       fd  Linux raid auto
1b  Hidden W95 FAT3 75  PC/IX           bb  Boot Wizard hid fe  LANstep        
1c  Hidden W95 FAT3 80  Old Minix       be  Solaris boot    ff  BBT            
1e  Hidden W95 FAT1

```

---

### Post by srs5694 on 2010-12-05
> **honeybear said:**
> what is the difference between 86 and 87 ?


According to [this site,](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html) 0x86 is for FAT volume sets and 0x87 is for NTFS or HPFS volume sets. I don't know if this is 100% accurate, though.

---

