---
title: "&quot;Tried&quot; Ubuntu 12.10 and now win 7 will not load"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by floridafan86 on 2013-01-31
I was messing around trying Ubuntu(on a USB) when apparently I screwed something up, now windows will not load (It will sit on the Windows splash screen until I restart it). I've been reading/trying to figure out what I could have messed up for a few hours now and I still can't figure out what's wrong.

I read something that said to run bootinfoscript, so I did that and here are the results:
Please any help would be greatly appreciated!


                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       602200063 sectors, but according to the info from 
                       fdisk, it has 602210886 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       20479999 sectors, but according to the info from 
                       fdisk, it has 20493697 sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootrnr.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/lenovobt.efi

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 1854840.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 32896 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2           2,459,648   604,670,534   602,210,887   7 NTFS / exFAT / HPFS
/dev/sda3         604,659,712   625,153,409    20,493,698   7 NTFS / exFAT / HPFS

/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   250,069,679   250,069,679  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       206,847       204,800 EFI System partition
/dev/sdb2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb3       1,854,840   206,085,231   204,230,392 EFI System partition
/dev/sdb4     248,020,992   250,068,991     2,048,000 -

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 31.0 GB, 31029460992 bytes
55 heads, 55 sectors/track, 20034 cylinders, total 60604416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    60,604,415    60,596,352   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7E5EC4775EC42A2B                       ntfs       SYSTEM_DRV
/dev/sda2        C804CC8504CC77C8                       ntfs       Windows7_OS
/dev/sda3        E6D6D4C4D6D495E1                       ntfs       Lenovo_Recovery
/dev/sdb1        C483-924A                              vfat       
/dev/sdb3        94C429D4C429B8FE                       ntfs       
/dev/sdb4        5AB21BF7B21BD5FB                       ntfs       rr_recovery
/dev/sdc1        71D5-E240                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
a4bb94ded106404da1a6bfd50179d6ac

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found
```

---

### Post by arpanaut on 2013-01-31
Did you disable uefi and or secure boot in bios to get the live usb to boot.
Because I see efi partition on sdb so you may need to reset your settings back to what they were before trying to boot the usb.
That's the only obvious thing I can see.

hth

---

### Post by floridafan86 on 2013-01-31
> **arpanaut said:**
> Did you disable uefi and or secure boot in bios to get the live usb to boot.
Because I see efi partition on sdb so you may need to reset your settings back to what they were before trying to boot the usb.
That's the only obvious thing I can see.
 
hth
 
No I did not disable UEFI or secure boot as far as I know. I did notice that right before it loads Ubuntu it will say "secure boot is not enabled" at the top of the screen. I didn't do anything to disable secure boot to my knowledge.
 
Also, every attempt to repair windows has not worked. Once I go to repair windows, I get an error message that says "this version of system recovery options is not compatible with the version of windows you are trying to repair"
 
I know the repair disk is win 7 x64 so I'm assuming this is all related somehow.

---

### Post by oldfred on 2013-02-02
Strange configuration as you have Windows in BIOS/legacy mode in sda and UEFI mode in sdb. You have to go into UEFI/BIOS and change boot from/to UEFI and drive order to boot one or the other.

If looks like something changed partition sizes on sda and made errors.

/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda

```
sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       602200063 sectors, but according to the info from 
                       fdisk, it has 602210886 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       20479999 sectors, but according to the info from 
                       fdisk, it has 20493697 sectors.
    Operating System:  
    Boot files:        
```With NTFS partitions both partition table and NTFS partition Boot sector (PBR) must match with the same size info. 

You need to fix partition table first and then from Windows will need to run chkdsk on both sda2 & sda3 to update PBR.

       First backup partition table, and save to another drive or external device.
sudo sfdisk -d /dev/sda > parts_sda.txt


Overlapping can be a problem as we do not know if you have written data into that area from one or the other partition, or if shrinking one damages data on the other. Best to backup all important data first.


        this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v


If still beyond end of drive you can use fixparts.
       
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
       
Then use a Windows repairCD to run chkdsk on the NTFS partitions.

---

### Post by floridafan86 on 2013-02-02
When i try to use the commands you suggested (fdisk or sfdisk) I get this:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

---

### Post by oldfred on 2013-02-02
Your sdb drive is gpt. Did drives change boot order? BIOS may not always report them to the system the same or booting from flash drive may change order.  We want to try to repair the MBR drive, not the gpt drive.

For gpt drives you cannot use fdisk. You can use parted, gparted and you should download gdisk which is the fdisk for gpt drives. gdisk is in the repositories but works a bit different. 
sudo apt-get install gdisk

       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by floridafan86 on 2013-02-02
Yes I think the boot order did change. I am a complete noob at this but from what I am reading in gparted sda is my backup HDD that also has Win7 on it. This drive is not the problem.

The problem is with the sdb (msata ssd main drive, which is UEFI). I'm not sure if this makes a difference or not, I will look at the gdisk stuff.

Thanks

---

### Post by oldfred on 2013-02-02
Your Windows partition on sdb3 in boot script also shows PBR as not matching and it looks like it needs chkdsk. You can only run chkdsk from a Windows repairCD.
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by floridafan86 on 2013-02-03
I think I officially brokededed it...I've spent too much time trying to fix it so I'm just going to format it and start over...Thanks for the help!

---

