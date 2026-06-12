---
title: "Boot up sequence"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by harfin on 2011-11-17
Hello

I have read the step by step guide regarding changing the boot up sequence on my dual boot pc, and am no wiser! 

I ran Start-up Manager and on the boot sequence page of the menu, but it already shows Ubuntu as 1st choice boot (and default) and Windows XP as second choice.

Whenever I boot however, the menu I am presented with shows Windows XP as first and Ubuntu as second.

I have recently upgraded to Ubuntu Oneiric Ocelot

Help!
Alan A Hart

---

### Post by drs305 on 2011-11-17
We need to know more about your system's boot setup: Wubi vs regular installation, Grub version, etc.

If you would download and run the Boot Info Script and post the contents of RESULTS.txt we can give you informed advice on how to fix your system.

Click the "BIS" link in my signature line to take you to the script's download page.

---

### Post by harfin on 2011-11-17
As requested:

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Plop is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr /ubuntu/winboot/wubildr 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   227,801,699   227,705,310   7 NTFS / exFAT / HPFS
/dev/sda3         227,801,700   305,893,664    78,091,965   f W95 Extended (LBA)
/dev/sda5         227,801,763   305,893,664    78,091,902   7 NTFS / exFAT / HPFS
/dev/sda4         305,893,665   312,496,379     6,602,715  db CP/M / CTOS / ...


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       28748dfc-f8a4-4d14-9aa9-b535db825c72   ext3       
/dev/sda1        07D7-010C                              vfat       DellUtility
/dev/sda2        90D8242ED82414CE                       ntfs       
/dev/sda4                                               vfat       DellRestore
/dev/sda5        7EA87C3CA87BF14F                       ntfs       Backup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


==================== sda2/ubuntu/disks/boot/grub/menu.lst: =====================

--------------------------------------------------------------------------------
default 0
timeout 3
color cyan/blue white/blue

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=775

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.10, kernel 3.0.0-13-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-13-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-3.0.0-13-generic

title        Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-13-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-3.0.0-13-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 2.6.38-12-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.38-12-generic

title        Ubuntu 11.10, kernel 2.6.38-12-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-12-generic

title        Ubuntu 11.10, kernel 2.6.32-25-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.10, kernel 2.6.32-25-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault

title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault

title Windows NT/2000/XP
root (hd0,3)
chainloader +1
savedefault

--------------------------------------------------------------------------------

======================== sda2/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ubuntu/disks/boot/grub/menu.lst                1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.32-25-generic  2
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.38-12-generic  2
            ?? = ??             ubuntu/disks/boot/initrd.img-3.0.0-12-generic  2
            ?? = ??             ubuntu/disks/boot/initrd.img-3.0.0-13-generic  4
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.32-25-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.38-12-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-3.0.0-12-generic     1
            ?? = ??             ubuntu/disks/boot/vmlinuz-3.0.0-13-generic     1

======================== sda2/Wubi/boot/grub/menu.lst: =========================

--------------------------------------------------------------------------------
default 0
timeout 3
color cyan/blue white/blue

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=775

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.10, kernel 3.0.0-13-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-13-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-3.0.0-13-generic

title        Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-13-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-3.0.0-13-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-3.0.0-12-generic

title        Ubuntu 11.10, kernel 2.6.38-12-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.38-12-generic

title        Ubuntu 11.10, kernel 2.6.38-12-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.38-12-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.38-12-generic

title        Ubuntu 11.10, kernel 2.6.32-25-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.10, kernel 2.6.32-25-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=90D8242ED82414CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 11.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault

title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault

title Windows NT/2000/XP
root (hd0,3)
chainloader +1
savedefault

--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst                             1
            ?? = ??             boot/initrd.img-2.6.32-25-generic              2
            ?? = ??             boot/initrd.img-2.6.38-12-generic              2
            ?? = ??             boot/initrd.img-3.0.0-12-generic               2
            ?? = ??             boot/initrd.img-3.0.0-13-generic               4
            ?? = ??             boot/vmlinuz-2.6.32-25-generic                 1
            ?? = ??             boot/vmlinuz-2.6.38-12-generic                 1
            ?? = ??             boot/vmlinuz-3.0.0-12-generic                  1
            ?? = ??             boot/vmlinuz-3.0.0-13-generic                  1
            ?? = ??             initrd.img                                     4
            ?? = ??             initrd.img.old                                 2
            ?? = ??             vmlinuz                                        1
            ?? = ??             vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 4a 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.J.Dell 8.0.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 0c  01 d7 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 30 33 c0 8e d0  |...........03...|
00000050  bc 00 07 fc b9 80 00 8e  d8 be 00 7c b8 00 20 8e  |...........|.. .|
00000060  c0 33 ff f3 66 a5 ea 6b  00 00 20 8e d8 b8 01 02  |.3..f..k.. .....|
00000070  b9 01 00 b6 00 8a 16 24  00 bb 00 02 cd 13 0f 82  |.......$........|
00000080  e0 00 80 3e c2 03 06 74  0e c6 06 c2 03 06 b8 01  |...>...t........|
00000090  03 cd 13 0f 82 cb 00 66  0f b7 06 16 00 66 d1 e0  |.......f.....f..|
000000a0  66 40 66 03 06 1c 00 66  a3 3e 00 8b 2e 11 00 89  |f@f....f.>......|
000000b0  2e 44 00 c1 ed 04 e8 cb  00 4d 75 fa b9 0b 00 be  |.D.......Mu.....|
000000c0  ea 01 8b fd f3 a6 74 0f  83 c5 20 ff 0e 44 00 75  |......t... ..D.u|
000000d0  eb be e0 01 e9 8e 00 26  8b 46 1a a3 46 00 66 a1  |.......&.F..F.f.|
000000e0  1c 00 66 40 66 a3 3e 00  c7 06 48 00 00 00 8b 2e  |..f@f.>...H.....|
000000f0  16 00 e8 8f 00 4d 75 fa  c7 06 4a 00 70 00 c7 06  |.....Mu...J.p...|
00000100  48 00 00 00 66 0f b7 06  46 00 66 83 e8 02 66 0f  |H...f...F.f...f.|
00000110  b6 0e 0d 00 66 f7 e1 66  0f b7 0e 16 00 66 d1 e1  |....f..f.....f..|
00000120  66 41 66 03 0e 1c 00 66  03 c1 66 0f b7 0e 11 00  |fAf....f..f.....|
00000130  66 c1 e9 04 66 03 c1 66  a3 3e 00 0f b6 2e 0d 00  |f...f..f.>......|
00000140  e8 41 00 4d 75 fa 8b 36  46 00 b8 00 30 d1 e6 73  |.A.Mu..6F...0..s|
00000150  03 05 00 10 8e c0 26 ad  3d f8 ff 73 0d a3 46 00  |......&.=..s..F.|
00000160  eb a2 be d5 01 e8 0d 00  eb fe 8a 16 24 00 33 ed  |............$.3.|
00000170  ea 00 00 70 00 ac 3c 00  74 09 b4 0e bb 07 00 cd  |...p..<.t.......|
00000180  10 eb f2 c3 66 a1 3e 00  66 33 d2 66 0f b7 0e 18  |....f.>.f3.f....|
00000190  00 66 f7 f1 fe c2 88 16  25 00 32 d2 66 0f b7 0e  |.f......%.2.f...|
000001a0  1a 00 66 f7 f1 8a f2 8b  c8 b8 01 02 c0 e5 06 0a  |..f.............|
000001b0  2e 25 00 86 e9 8a 16 24  00 c4 1e 48 00 cd 13 72  |.%.....$...H...r|
000001c0  a1 66 ff 06 3e 00 81 06  48 00 00 02 75 06 81 06  |.f..>...H...u...|
000001d0  4a 00 00 10 c3 44 69 73  6b 20 65 72 72 6f 72 00  |J....Disk error.|
000001e0  4e 6f 20 6c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No loader.DELLBI|
000001f0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 55 aa  |O BIN.........U.|
00000200
```

---

### Post by bcbc on 2011-11-17
Wow don't often see a grub-legacy version of Wubi these days. I guess you upgraded all the way from 9.04 up to 11.10 (quite a feat).

Anyway... to get Ubuntu as the default in the Windows boot manager:
Right Click on My Computer, Properties, click Advanced tab, Startup & Recovery settings, select Ubuntu from the "default OS to boot" drop down box.

Don't set the "Time to display operating systems" to < 10 or there may be some problems booting XP.

---

### Post by harfin on 2011-11-18
Brilliant!  Easy when you know how, eh.  I had not realised that it was a setting within Windows that required changing.

Now all I have to do, is to get my sound system working as it should - but that's another thread!

Thanks so much.

Alan

---

