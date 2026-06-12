---
title: "Ubuntu Server 12.04 Won't Boot After Install"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by ADelosSantos on 2014-02-11
The installation of Ubuntu Server 12.04 on my PC was finished smoothly but when I try to boot it, the following message appears: 

Reboot and select proper boot device...

This is the output after I run a boot info:

[http://paste.ubuntu.com/6914342/](http://paste.ubuntu.com/6914342/)

And after running the boot info script

                   ```
       Boot Info Script 0.61      [1 April 2012]
    
    
    ============================= Boot Info Summary: ===============================
    
     => No boot loader is installed in the MBR of /dev/sda.
     => No boot loader is installed in the MBR of /dev/sdb.
    
    sda1: __________________________________________________________________________
    
        File system:       linux_raid_member
        Boot sector type:  -
        Boot sector info: 
    
    sda2: __________________________________________________________________________
    
        File system:       ext4
        Boot sector type:  -
        Boot sector info: 
        Operating System:  
        Boot files:        
    
    sdb1: __________________________________________________________________________
    
        File system:       linux_raid_member
        Boot sector type:  -
        Boot sector info: 
    
    sdb2: __________________________________________________________________________
    
        File system:       ext4
        Boot sector type:  -
        Boot sector info: 
        Operating System:  
        Boot files:        
    
    ============================ Drive/Partition Info: =============================
    
    Drive: sda _____________________________________________________________________
    
    Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
    
    /dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT
    
    
    GUID Partition Table detected.
    
    Partition    Start Sector    End Sector  # of Sectors System
    /dev/sda1           2,048     7,813,119     7,811,072 RAID partition (Linux)
    /dev/sda2       7,813,120 1,953,523,711 1,945,710,592 EFI System partition
    
    Drive: sdb _____________________________________________________________________
    
    Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
    
    /dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT
    
    
    GUID Partition Table detected.
    
    Partition    Start Sector    End Sector  # of Sectors System
    /dev/sdb1           2,048     7,813,119     7,811,072 RAID partition (Linux)
    /dev/sdb2       7,813,120 1,953,523,711 1,945,710,592 EFI System partition
    
    "blkid" output: ________________________________________________________________
    
    Device           UUID                                   TYPE       LABEL
    
    /dev/loop0                                              squashfs   
    /dev/sda1        8bcf74b5-7cbd-25a9-31c5-537344fcd5c0   linux_raid_member server:0
    /dev/sda2        80d5941c-88e4-4ffc-bdf4-42cf53dbfee8   ext4       
    /dev/sdb1        8bcf74b5-7cbd-25a9-31c5-537344fcd5c0   linux_raid_member server:0
    /dev/sdb2        677c215a-c736-44e6-a7f3-3026764fc715   ext4       
    /dev/sr0                                                iso9660    Ubuntu 12.04.2 LTS i386
    
    ================================ Mount points: =================================
    
    Device           Mount_Point              Type       Options
    
    /dev/loop0       /rofs                    squashfs   (ro,noatime)
    /dev/sr0         /cdrom                   iso9660    (ro,noatime)
```

What should I do?

---

### Post by sudodus on 2014-02-11
> => No boot loader is installed in the MBR of /dev/sda.
=> No boot loader is installed in the MBR of /dev/sdb.

You have installed the bootloader to the wrong place (or not at all).

If I understand correctly, you have a RAID system. Unfortunately I know very little about RAID, so I cannot help much, except that you might try to repair the system by installing a bootloader into the head of a device, either [FONT=courier new]**/dev/sda**[/FONT] or[FONT=courier new]** /dev/sdb**[/FONT] (no digit).

See this link [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2014-02-11
I do not know RAID either, but you normally install the boot loader to the root of the RAID not the drive's MBR.

Is your system UEFI. The boot flag making an ext4 partition as the efi partition may confuse it, as efi partitions are supposed to be FAT32  and only have the efi boot files, but your ext4 looks like your main install.

While sda1 & sdb1 have same UUID, your sda2 and sdb2 do not. Is your RAID broken, should not both be the same?

---

