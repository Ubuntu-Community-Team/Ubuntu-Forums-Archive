---
title: "How to uninstall Ubundu 14.04 from PC to make the way for another OS"
date: 2016-01-14
forum: New to Ubuntu
---

### Post by pal-vij on 2016-01-14
I am new to Ubuntu. I installed Ubuntu 14.04 **with out partition.** . It's hard drive is protected by password. After unlocking it only we can get login (user-name) screen
My room mate wants window 8...since it is his PC. I don't have a choice. 
I have Windows 8 recovery CD from DELL. But **I'm unable to install windows 8. :(  **Machine is not picking DVD I mean not showing windows 8 OS option for install when i restart PC. After login Ubuntu shows DVD but if I click setup.exe or bootmgr.efi it gives error. "An Error occurred while loading Archive" 
I installed Ubuntu 14.04 using DVD only. 

Advance thanks for your valuable detailed tips.

---

### Post by TheFu on 2016-01-14
Please post the complete output from 

```
sudo parted -l
```

Since 12.04, there isn't any approved way to install Ubuntu without partitioning, so we don't really know what you have today.
Normally, the answer is to use any partition tool, carefully, delete any Linux partitions, then use the main OS recovery disk and force it to become the primary boot manager for the system.

---

### Post by yancek on 2016-01-14
You won't be able to install windows 8 with a Recovery CD, you need the full installation media which would fit on a DVD.  Did this machine originally have windows 8 on it?  That might work with the Recovery CD.

---

### Post by leunam12 on 2016-01-15
Make sure that the DVD is clean from dust and fingerprints first, then insert it and start the computer and invoke the temporary boot options (usually F12 on Dells) and choose to boot from DVD. The recovery CD (DVD maybe?) should be all you need, however it seems strange to me that there is only one. My laptop has 3.

---

### Post by pal-vij on 2016-01-15
This machine comes with installed windows 8. I don't have Installation CD expect recovery CD. While installing Ubuntu i removed windows, now this has only Ubuntu.

---

### Post by pal-vij on 2016-01-15
Dell Inspiron-660s is my Dell PC
sudo parted -l returns 


Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number Start End Size File system Name Flags
1 1049kB 538MB 537MB fat32 boot
2 538MB 794MB 256MB ext2
3 794MB 1000GB 999GB




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8456MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number Start End Size File system Flags
1 0.00B 8456MB 8456MB linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number Start End Size File system Flags
1 0.00B 991GB 991GB ext4




Error: /dev/mapper/sda3_crypt: unrecognised disk label

---

### Post by pal-vij on 2016-01-15
> **leunam12 said:**
> Make sure that the DVD is clean from dust and fingerprints first, then insert it and start the computer and invoke the temporary boot options (usually F12 on Dells) and choose to boot from DVD. The recovery CD (DVD maybe?) should be all you need, however it seems strange to me that there is only one. My laptop has 3.

I verified in boot first option is DVD next USB drive.

---

### Post by yancek on 2016-01-15
Your parted output shows 3 partitions, none of which are windows and no recovery partition.  You used the LVM option when you installed Ubuntu which overwrites everything.  I don't use windows so I don't know if there is a way to recover from this without a windows installation DVD.

---

### Post by buzzingrobot on 2016-01-16
Existing partitions can be deleted with the Windows installer.  There's no need to to remove them beforehand.  Windows will happily overwrite the existing bootloader, as well.

The Recovery HD is a partition.  Windows contrives to make it invisible in the sense that it won't appear in normal listings of existing partitions,  But, isn't protected from anything that deletes/creates partition tables, which happened when you told the Ubuntu partitioner to use LVM for that drive. (This is not Ubuntu, or even OS specific.  It's the way partitioning works on the PC architecture.) 

 If the Recovery HD is gone, then you can't recover Windows but you must reinstall it. If you have a legitimate Product Key, you can check the Microsoft site to see if you can download a Win8 installation image. I know you can for Win10. You burn that image to a DVD or USB stick, boot, and begin the install.  You are asked for the Product Key very early in the install process. (FYI: Even off  a USB stick, the Windows boot is v-e-r-y slow.)

---

### Post by TheFu on 2016-01-16
> **yancek said:**
> Your parted output shows 3 partitions, none of which are windows and no recovery partition.  You used the LVM option when you installed Ubuntu which overwrites everything.  I don't use windows so I don't know if there is a way to recover from this without a windows installation DVD.

Yep. He has nothing to lose. Windows is gone.

```
Number Start End Size File system Name Flags
1 1049kB 538MB 537MB fat32 boot
2 538MB 794MB 256MB ext2
3 794MB 1000GB 999GB
```
There are 3 partitions - 
1) UEFI
2) tiny boot
3) encrypted container for everything else, which is using LVM inside it. It is about 1TB in size.  Would be nice if the OP used "code tags" for the parted output so everything lines up.

No other partitions (i.e. windows) exist on this HDD.

> Normally, the answer is to use any partition tool, carefully, delete any Linux partitions, then use the main OS recovery disk and force it to become the primary boot manager for the system. 

No need to be careful; delete all the partitions if you don't want any Ubuntu stuff left.  It appears the OP selected whole drive encryption during the Ubuntu setup - /dev/mapper/sda3_crypt message?.  Get to wiping and re-install Windows however you like.  It isn't on the HDD.

---

