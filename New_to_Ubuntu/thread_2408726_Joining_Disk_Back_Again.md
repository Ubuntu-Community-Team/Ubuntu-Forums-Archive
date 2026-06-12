---
title: "Joining Disk Back Again"
date: 2018-12-22
forum: New to Ubuntu
---

### Post by alejandro202 on 2018-12-22
Hello Ubuntu community!

I swapped to Ubuntu around two months ago. When I had Win10 installed on the system I divided my disk to store program files, separated from the Windows Disk. Now, I still have this spitted disk on the Ubuntu machine with all the information on it. I want to "join" the disk back together, so In a near future I can split it to store the OS for a Virtual Machine I want to setup. How can I join the disk? 

Thanks.

---

### Post by Impavidus on 2018-12-22
If I get this right, when you had Windows you had 2 big ntfs partitions, one with the Windows OS and one with other stuff, in addition to some small partitions. You formatted the Windows OS partition to some Linux filesystem and installed Ubuntu, but the other ntfs partition is still there with all the stuff you stored on it. Now it's not entirely clear what you want. Did you have the idea to somehow join the partitions, so that all your stuff is on the Ubuntu OS partition, then create a new partition for a VM? You can't really join partitions (nor split them), you'll have to copy stuff from one partition to the other, then delete one and resize the other. And using ntfs partitions when Windows is no longer present is not a good idea. Ubuntu can read and write ntfs, but cannot fix it in case of filesystem damage.

---

### Post by TheFu on 2018-12-22
Windows uses NTFS.  That is problematic, since Linux file systems work best with all the great features that Linux file systems have.

What, exactly, do you want to "Join" and in the future, what, exactly, to you want to "split" for a virtual machine?  If you can explain which OS you intend to run as the real OS and which do you plan to run inside a hypervisor.

And just so we understand the physical disk issue, please post the output from **sudo fdisk -l** but we don't need any of the "loop" devices, so delete those from the output.  When posting it, please use "code tags" so everything lines up in this forum.

---

### Post by alejandro202 on 2018-12-22
So my host OS will be *linux*, it is the only OS currently installed in my  computer. I want to delete the partition I did in Win10, perhaps the  correct term will be resize to 0 and use that memory of that partition  to resize the current disk used by linux. After done this I want to  install a Virtual Machine Software, like for example, *VirtualBox*, and be  able to run Win10 and other Operating Systems. The location in which  this Virtual OS's will be stored will be in a new partition so it  doesn't get mixed up with the *linux* one.

**sudo fdisk -l without "loop" devices (*_Whare are loop devices?_*)**
```
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 8091A5C2-8515-464B-84BE-0771638EEF13

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 250068991 249018368 118,8G Linux filesystem


Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7313E643-CFA4-4A0B-95FF-5BE12F817223

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048 1844809727 1844807680 879,7G Microsoft basic data
/dev/sdb2  1926731776 1953523711   26791936  12,8G Microsoft basic data


Disk /dev/sdc: 1,4 TiB, 1500267937792 bytes, 2930210816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4be0d81e

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1        2048 2930210815 2930208768  1,4T  7 HPFS/NTFS/exFAT


Disk /dev/sdd: 14,5 GiB, 15518924800 bytes, 30310400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x44fc321d

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1          63 30308543 30308481 14,5G  b W95 FAT32


Disk /dev/sde: 962 MiB, 1008730112 bytes, 1970176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8d373cc8

Device     Boot Start     End Sectors   Size Id Type
/dev/sde1         696 1970175 1969480 961,7M  6 FAT16


Disk /dev/sdg: 14,9 GiB, 16004415488 bytes, 31258624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdg1          32 31258623 31258592 14,9G  c W95 FAT32 (LBA)
```

---

### Post by TheFu on 2019-01-01
If you will only have Linux, then just backup anything you want to keep and do a fresh "use whole disk" install.  I would choose to use LVM during the install to have much more flexibility with the storage management in the future.  

There are many guides for LVM.  It hasn't changed in years and there isn't any safe GUI to use it, but because it is CLI, pretty much any guide you find works the same regardless of underlying OS.

Post install, I'd shrink the OS LV, create a /home LV and an LV for VMs.  Generally, you can consider an LV as the same as a really, really, flexible partition.  Since you have multiple disks, I'd caution against using LVM to span disks.  I lost 80% of my data doing that when 1 disk failed out of 3 total.  OTOH, that loss convinced me to get backup religion. I don't fear disk failures anymore. Data is all safe. If you cannot restore a specific backup from 60+ different versions to a newly bought HDD in less than 45 minutes, then you need a better backup/restore solution.   And LVM is very helpful to eliminate downtime needed by most backup solutions.

Remove as much NTFS as you can from the system. Keep LVM PEs, VGs, and LVs confined within a single HDD, just have different setups on each disk and if you do need striping, RAID, or spanning with LVM, please, please, please have backup storage that doesn't depend on those tricks.  Sometimes the only solution to RAID failures is to recreate the RAID-set from scratch and restore from a backup.

For virtualization, I'd avoid virtualbox and go with kvm + libvirt + virt-manager.  Why?  Performance: [https://www.phoronix.com/scan.php?page=article&item=virtualbox-60-kvm](https://www.phoronix.com/scan.php?page=article&item=virtualbox-60-kvm)

Or you could fandagle around by deleting partitions, converting NTFS to ext4 or ZFS (ZFS only for data, never OS), and then fixing any boot issues manually in the fstab, then grub.  But really a fresh install and reloading the data from backups should take less than 45min total.  Linux isn't Windows. We have control over our setups.

---

