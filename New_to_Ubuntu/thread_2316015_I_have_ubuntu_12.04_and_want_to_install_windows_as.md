---
title: "I have ubuntu 12.04 and want to install windows as a partition(dual boot)."
date: 2016-03-04
forum: New to Ubuntu
---

### Post by nithin6 on 2016-03-04
Hi guys, i am having ubuntu 12.04 in my laptop and i want to install windows as dual boot.Can anyone guide me how to partition my ubuntu(1 TB) and install windows side by side?

---

### Post by nithin6 on 2016-03-04
when i type  sudo fdisk -l     i get the following:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x045735bf


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      718847      358400   de  Dell Utility
/dev/sda2          718848     7010303     3145728    c  W95 FAT32 (LBA)
/dev/sda3   *     7010304   999625538   496307617+  83  Linux
/dev/sda4      1937143806  1953523711     8189953    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1937143808  1953523711     8189952   82  Linux swap / Solaris

---

### Post by yancek on 2016-03-04
Which windows version do you want to install?
First determine whether you are using UEFI or MBR if you don't know.  Boot Ubuntu and open a terminal.  Copy and paste the command below.  It will output either EFI or Legacy boot.

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

You have an Extended partition (sda4) which would indicate MBR.  If that's the case, you already have used the four primary partitions allowed.  You need to put windows or at least it's boot files on a primary partition and there are none available.   Did you previously have windows installed on this computer?  If so, which windows?  You have a FAT32 partition (sda2) which would not be there if you have just had a Linux system unless you were using UEFI.  If you have Ubuntu installed UEFI, you need to install windows UEFI.  Take a look at the link below for some general information on that.

   
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by nithin6 on 2016-03-06
> **yancek said:**
> Which windows version do you want to install?
First determine whether you are using UEFI or MBR if you don't know.  Boot Ubuntu and open a terminal.  Copy and paste the command below.  It will output either EFI or Legacy boot.

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

You have an Extended partition (sda4) which would indicate MBR.  If that's the case, you already have used the four primary partitions allowed.  You need to put windows or at least it's boot files on a primary partition and there are none available.   Did you previously have windows installed on this computer?  If so, which windows?  You have a FAT32 partition (sda2) which would not be there if you have just had a Linux system unless you were using UEFI.  If you have Ubuntu installed UEFI, you need to install windows UEFI.  Take a look at the link below for some general information on that.

   
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)





when i typed the command u gave, it shows  Legacy boot on HDD


i did not have any windows installed previously. I bought my laptop with ubuntu already installed in it. no history of windows. I want to install windows 8.1 .

---

### Post by oldfred on 2016-03-06
Windows only boots from a primary NTFS formatted partition with the boot flag when using BIOS with MBR(msdos) partitioning.
Standard BIOS installs use two primary partitions, a small Boot and main install. But you can install to just one NTFS, if created in advance.

You will have to backup data on one of your primary partitions and delete it, best to backup entire system.
Then create new NTFS primary partition with boot flag.

You also may be able to use fixparts to convert Linux install sda3 to a logical partition. But you also have a lot of unusable space between end of Linux partition and start of extended partition. Moving partitions with gparted can take a long time and any power failure or issue can fully corrupt system. So good back ups are required, even though it usually works ok. 

       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by yancek on 2016-03-06
With Legacy Boot, you are only allowed 4 primary partitions and you already have 4 primary partitions so you would need to delete one of them as windows will not boot unless it has boot files on a primary partition.  I'm not sure why you have a FAT32 (sda2) partition or what is on it so you should check to see what it is before deleting it.  You would then need to turn swap off and delete it and then delete the Extended partition (sda4) and you would then have to shrink the Ubuntu partition (sda3) to leave unallocated space to install windows.  You would need to use an Ubuntu or any Linux Live CD or the GParted iso to do this as you can't modify partitions from a running system.  You can download GParted from the link below and burn it as an image.  After doing that, you reboot the computer with the GParted iso in the drive and perform the operations above.

  [http://gparted.org/download.php](http://gparted.org/download.php)

I can't give you any advice on installing windows as I haven't done that for over ten years.

A possible simpler process would be to back up all your personal data from the Ubuntu install and just install windows 8 over it and then download and re-install Ubuntu.  If you have a lot of configurations or modifications to your Ubuntu this will be a problem as none of it will be saved on re-installing.  It would have been simpler if Ubuntu was installed using UEFI/GPT but...?  The installation is complicated by the fact that windows can't boot unless the boot files are on a primary partition and also windows will overwrite any boot code on an MBR system.

---

### Post by oldfred on 2016-03-06
Windows installs also have been known to not write the Linux partitions back to partition table.
You do need good backups, but often can just re-add Linux partitions' entry to partition table with testdisk or parted rescue.
But after finalizing partition table structure, but before installing Windows, backup partition table and save to another device.
       
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sdb > parts_sdb.txt

---

### Post by stalkingwolf on 2016-03-07
in times past windows installs had to be done first as windows cant read ext partitions and see them as bad sectors and wont install.   is this still true?

---

### Post by oldfred on 2016-03-07
Windows does not read Linux formats.
But If you have unallocated space or better a pre-formatted primary NTFS partition with boot flag it will install to that.
The issue then is will it include the Linux partitions when writing new partition table. Many times it does not. But Linux data is still there, not erased by Windows. So recovery possible.

---

