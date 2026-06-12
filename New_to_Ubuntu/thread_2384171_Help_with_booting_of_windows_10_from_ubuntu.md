---
title: "Help with booting of windows 10 from ubuntu"
date: 2018-02-03
forum: New to Ubuntu
---

### Post by ubuders222 on 2018-02-03
I have installed and can run ubuntu on an external hard drive, from uefi(i think), but can't run windows from my internal ssd, i get stuck in the grub recovery with message "error no such device". I have tried boot-repair, but it gives the error message "GPT detected. Please create a BIOS-Boot partition". What should i do to get my windows 10 running?   

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid fecf032a-a42a-4bc3-8f38-a0af312a2a85 root hd0,msdos3 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     4,501,503     4,499,456   7 NTFS / exFAT / HPFS
/dev/sda2           4,501,504   439,582,719   435,081,216   7 NTFS / exFAT / HPFS
/dev/sda3         439,582,720   468,860,927    29,278,208   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                65,535     1,048,559       983,025 EFI System partition
/dev/sdb2             1,048,560 1,936,952,459 1,935,903,900 Data partition (Linux)
/dev/sdb3         1,936,952,460 1,953,467,279    16,514,820 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        347C8C417C8C003A                       ntfs       SYSTEM_DRV
/dev/sda2        3A208EFD208EBF7F                       ntfs       Windows7_OS
/dev/sda3        A45689C056899428                       ntfs       Lenovo_Recovery
/dev/sdb1        C6C1-01D5                              vfat       
/dev/sdb2        4d1882ef-38aa-4324-897d-77d632db7a47   ext4       
/dev/sdb3        ed598c76-6422-43ba-986e-d0f6f655f610   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb  3 14:10 ata-KINGSTON_SV300S37A240G_50026B774B097D38 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  3 14:11 ata-KINGSTON_SV300S37A240G_50026B774B097D38-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  3 14:11 ata-KINGSTON_SV300S37A240G_50026B774B097D38-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  3 14:11 ata-KINGSTON_SV300S37A240G_50026B774B097D38-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Feb  3 14:10 usb-JMicron_Generic_74D786116764344-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb  3 14:10 usb-JMicron_Generic_74D786116764344-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Feb  3 14:10 usb-JMicron_Generic_74D786116764344-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Feb  3 14:10 usb-JMicron_Generic_74D786116764344-0:0-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Feb  3 14:10 wwn-0x50026b774b097d38 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  3 14:11 wwn-0x50026b774b097d38-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  3 14:11 wwn-0x50026b774b097d38-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  3 14:11 wwn-0x50026b774b097d38-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb2        /                        ext4       (rw,relatime,errors=remount-ro,stripe=8191,data=ordered)


========================== sdb1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid 4d1882ef-38aa-4324-897d-77d632db7a47 root hd1,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================
```

---

### Post by oldfred on 2018-02-03
Please use code tags with longer code or terminal output to preserve formatting.
Easy to use with Forum's advanced editor and # icon.

But with Boot-Repair's report easier still just to post link it provides.

You have Windows in BIOS/MBR configuration and Ubuntu in UEFI/gpt configuration.
You then must have newer UEFI hardware.
But UEFI and BIOS are not compatible. Once you start booting in one mode you cannot switch modes. Or from grub you can only boot other systems installed in same boot mode. You should be able to boot from UEFI boot menu. Some older UEFI required you to turn on/off UEFI or BIOS/CSM/Legacy settings to match install.

You can reinstall Windows in UEFI mode, convert Ubuntu to BIOS boot, dual boot only using UEFI boot menu, or add rEFInd which will dual boot but reboots to change to non-UEFI system.

Best to have all systems in same boot mode, either all UEFI or all BIOS.

And BIOS/MBR is now 35 years old, and UEFI has been required on new PC systems  since 2012 when Windows 8 was released.

---

