---
title: "Installing multiple Linux OS on Logical partition"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by Rajatheprogrammer on 2012-11-21
Im a newbee to linux. I have my windows7 as my primary OS (installed) and want to install Windows8, Ubuntu 12.04, fedora and other Linux OS on logical partitions.
ScreenShot of my partition table is attached.
I would like to install them on the following partitions

Partition 2 : Windows7 (installed)
Partition 3 : data
  Partition 5 : data
  Partition 6 : Windows8
  Partition 7 : Ubuntu 12.04
  Partition 8 : Fedora
  Partition 9 : Other Linux(for trying)
  Partition 10: Swap

Please help me accomplish this.

Also what should be my Partition Type and file system for each partition.

Installing converts my logical partition into primary partition which can be seen in disk management in Windows, which gives disk consistency error at windows startup. How do I prevent conversion of logical partition to primary partition on installation.

Your help would be really appreciated.

---

### Post by Wim Sturkenboom on 2012-11-21
> 
Installing converts my logical partition into primary partition which can be seen in disk management in Windows, which gives disk consistency error at windows startup. How do I prevent conversion of logical partition to primary partition on installation.

I don't see additional primary partitions. sda4 is an extended partition that holds your logical partitions.

The types should be 83 (Linux), 82 (swap; can be shared between all Linux installations unless you want to use hibernation) and 7 for ntfs

Below the output of fdisk -l on my system with 3 harddisks so you can see the types used (there is even a fat32 ;))

```

wim@i3-2120:~$ sudo fdisk -l
[sudo] password for wim: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd2efff31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   511999999   255896576    7  HPFS/NTFS/exFAT
/dev/sda3       512000000   528001023     8000512   82  Linux swap / Solaris
/dev/sda4       528003070  1953523711   712760321    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       528003072   820969471   146483200   83  Linux
/dev/sda6       820971520  1953523711   566276096   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e192e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    52436159    26218048+   7  HPFS/NTFS/exFAT
/dev/sdb2        52436221   472655871   210109825+   f  W95 Ext'd (LBA)
/dev/sdb5        52436223   115346699    31455238+   7  HPFS/NTFS/exFAT
/dev/sdb6       115346763   167782859    26218048+   b  W95 FAT32
/dev/sdb7       167782923   220219019    26218048+  83  Linux
/dev/sdb8       220219392   228579327     4179968   82  Linux swap / Solaris
/dev/sdb9       228581376   472655871   122037248   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c8c2717

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001   83  Linux
wim@i3-2120:~$ 

```

---

### Post by andrew.46 on 2012-11-21
You are not keen on virtualisation? I attach own setup...

---

### Post by Rajatheprogrammer on 2012-11-21
> **andrew.46 said:**
> You are not keen on virtualisation? I attach own setup...

I would like to enjoy the real fun in linux.. ;)

---

### Post by arpanaut on 2012-11-21
AFAIK Win OS insist on being installed on primary partitions.

---

### Post by Rajatheprogrammer on 2012-11-21
> **Wim Sturkenboom said:**
> I don't see additional primary partitions. sda4 is an extended partition that holds your logical partitions.


Upon changing partition type to Linux and installing Linux OS, Windows shows the partitions as Primary partition in disk manager. As you can see in the screenshot attached it shows seven primary partitions. I get Disk consistency error upon windows startup.

---

### Post by sandyd on 2012-11-21
> **Rajatheprogrammer said:**
> Upon changing partition type to Linux and installing Linux OS, Windows shows the partitions as Primary partition in disk manager. As you can see in the screenshot attached it shows seven primary partitions. I get Disk consistency error upon windows startup.

Are you using GPT?

---

### Post by oldfred on 2012-11-21
If you have an extended partition (and logicals) then it is not gpt.

Windows does not 'see' Linux formatted partitions correctly and can cause issues when it modifies a partition table with Linux partitions. Best not to use Windows partition tools to create partitions for Linux, but only to shrink Windows partition. Use gparted from a gparted disk, from Ubuntu or from partedmagic.

Often Windows will convert basic to dynamic partitions (like Linux LVM) when creating more than 4 partitions and then it will not work with Linux.

It is best to install Windows to primary partitions. Windows will not boot directly from a logical partition and still uses the primary install to boot from, but may move the boot files from the logical install into the primary partition. We often see users with a primary install of Windows, a newer install in a logical, then decide to delete the old primary partition install and wonder why then cannot boot Windows at all.

---

### Post by Rajatheprogrammer on 2012-11-21
Thank you to all the people who enlightened me.. I guess windows misreads logical partition of linux partition type as primary partition. I have repartitioned and installed all linux OS in logical partitions by making it of linux partition type of ext4 filesystem and windows8 in a logical partition of NTFS type. All works fine now. :)

---

