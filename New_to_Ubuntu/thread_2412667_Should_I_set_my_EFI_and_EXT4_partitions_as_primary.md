---
title: "Should I set my EFI and EXT4 partitions as primary ?what should be the mount points ?"
date: 2019-02-15
forum: New to Ubuntu
---

### Post by automate-stuff on 2019-02-15
I am installing in UEFI mode...I have set my EFI and EXT4 partitions to primary. I have also set the mount points for both to "/" . Are these settings OK ?

---

### Post by TheFu on 2019-02-15
If you are using UEFI, then it is common to use GPT partition tables. Those support over 100 primary partitions. No need for extended or logical, like in the old days for MBR partition tables.

Plus, Windows will only boot EFI using GPT partitions.
```

I have:
/dev/sda2                         ext2      473M  144M  305M  32% /boot
/dev/sda1                         vfat      511M  4.8M  507M   1% /boot/efi
/dev/mapper/ubuntu--vg-root       ext4       51G   38G   11G  79% /
```
but this is with LVM and encrytion, so /boot **must** be a separate partition using 16.04.   / could be sda3 and ext4, if you prefer NOT to use LVM.

---

### Post by Dennis N on 2019-02-15
> **automate-stuff said:**
> I am installing in UEFI mode...I have set my EFI and EXT4 partitions to primary. I have also set the mount points for both to "/" . Are these settings OK ?

No - You only need to set the partition to mount at /. That would be an ext4 partition. You don't specify a mount point for the EFI system partition - installer will take care of that, and mount it at /boot/efi.

For GPT partitioning, which you use for UEFI, all partitions are the same type. The EFI system partition is formatted FAT32, and the / partition is formatted ext4. You set the boot flag on the EFI system partition (which also sets an ESP flag).

---

### Post by automate-stuff on 2019-02-15
Minimal Ubuntu(mini.iso) installer also takes care of that ? or just the Ubuntu installer  ?


do you recommend installing in UEFI ? any downsides to installing in legacy mode ?

Here is the spec of the laptop I am installing Ubuntu on: 

[https://support.hp.com/ca-en/product/hp-stream-11-pro-g3-notebook-pc/11623748/document/c05283034](https://support.hp.com/ca-en/product/hp-stream-11-pro-g3-notebook-pc/11623748/document/c05283034)

---

### Post by Dennis N on 2019-02-15
> Minimal Ubuntu(mini.iso) installer also takes care of that ? or just the Ubuntu installer  ?
I haven't used the mini iso myself, but it should. 
> do you recommend installing in UEFI ? any downsides to installing in legacy mode ?
You have UEFI - you should use it. I always use UEFI if the computer has that capability. I find it easier to work with when multibooting several operating systems, but I have an older BIOS desktop too and Linux is fine on that.  Even with a BIOS computer, you can use the more modern GPT partitioning for your disk. 
> Here is the spec of the laptop I am installing Ubuntu on: 
It has Intel graphics, wireless and processor - those are good choices for Linux. I don't have an HP machine, so can't say more beyond that.

Good luck with your new Ubuntu!

---

### Post by oldfred on 2019-02-15
I suggest at least to use the much newer gpt partitioning which then can be used to boot in BIOS mode if you add a 1 or 2MB unformatted partition with bios_grub flag. And an ESP - efi system partition FAT32. For larger drives 300 to 500, but I use as little as 100MB when doing a full install to a 32 or 64GB flash drive.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[URL="http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr"]http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr

      [/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

            UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    ```
Disk /dev/sdc: 55.9 GiB, 60022480384 bytes, 117231407 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1   117,231,406   117,231,406  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdc1                 2,048       616,447       614,400 EFI System partition
/dev/sdc2               616,448       618,495         2,048 BIOS Boot partition
/dev/sdc3               618,496    58,925,055    58,306,560 Data partition (Linux)
/dev/sdc4            58,925,056   117,229,743    58,304,688 Data partition (Linux)
```

---

### Post by TheFu on 2019-02-19
I agree that you should use UEFI if you can.  This is a security thing and recommended in the _Linux Foundation Workstation security_ recommendations.  [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

---

