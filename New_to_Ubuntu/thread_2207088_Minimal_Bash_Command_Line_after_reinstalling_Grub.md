---
title: "Minimal Bash Command Line after reinstalling Grub"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by arjun6 on 2014-02-22
[COLOR=#000000]I recently installed ubuntu alongside my Windows 8. Grub failed to load so I was told you try boot-repair. I reinstalled grub as suggested. However, it seems to have corrupted my partion and I'm unable to load into Ubuntu or Windows now. 

When I boot on top of screen it says "GNU Grub version ....."(approximately)[/COLOR]
[COLOR=#000000]then it says "Minimal BASH-like line editing is supported.(also says about Tab)"[/COLOR]
[COLOR=#000000]then grub prompt.

I really really appreciate any help. Thank you in advance. 

Here is the bootinfoscript if it helps: 
[/COLOR]```
                   Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/grub/grubx64.efi /efi/grub/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda8: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda9: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  elementary OS Luna
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda10: _________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda11: _________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  elementary OS Luna
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 311552 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   500,118,191   500,118,191  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 EFI System partition
/dev/sda2         616,448     1,845,247     1,228,800 Windows Recovery Environment (Windows)
/dev/sda3       1,845,248     2,107,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,107,392   216,440,831   214,333,440 Data partition (Windows/Linux)
/dev/sda5     216,440,832   217,157,631       716,800 Windows Recovery Environment (Windows)
/dev/sda6     435,316,736   441,610,239     6,293,504 Data partition (Windows/Linux)
/dev/sda7     449,765,376   458,153,983     8,388,608 -
/dev/sda8     458,153,984   500,117,503    41,963,520 Windows Recovery Environment (Windows)
/dev/sda9     217,157,632   256,219,903    39,062,272 Data partition (Windows/Linux)
/dev/sda10    441,610,240   449,765,375     8,155,136 Swap partition (Linux)
/dev/sda11    256,221,184   435,316,735   179,095,552 Data partition (Windows/Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        3091-7187                              vfat       SYSTEM
/dev/sda10       4eaa58a3-034c-4208-8bfc-11d80bc78747   swap       
/dev/sda11       7970d9cc-09d1-416b-a860-a161f55174cb   ext4       
/dev/sda2        B604ACB304AC77CF                       ntfs       Recovery
/dev/sda4        84ECB3ECECB3D6A0                       ntfs       OS
/dev/sda5        F65E46045E45BDDD                       ntfs       
/dev/sda6        7830896B30893164                       ntfs       Data
/dev/sda8        3068BEE768BEAB4C                       ntfs       Restore
/dev/sda9        d0d22194-e4a8-4190-bf9a-56bb9633ce70   ext4       
/dev/sdb1        B84D-327D                              vfat       UUI


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sda9/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/25_custom ###


menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 3091-7187
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}


menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 3091-7187
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
### END /etc/grub.d/25_custom ###
--------------------------------------------------------------------------------


=============================== sda9/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=d0d22194-e4a8-4190-bf9a-56bb9633ce70 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=3091-7187  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda10 during installation
UUID=4eaa58a3-034c-4208-8bfc-11d80bc78747 none            swap    sw              0       0
UUID=3091-7187    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------


=================== sda9: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-51-generic               2
               =                boot/vmlinuz-3.2.0-51-generic                  1
               =                boot/vmlinuz-3.2.0-51-generic.efi.signed       1
               =                initrd.img                                     2
               =                vmlinuz                                        1


========================== sda11/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
true
}


insmod part_gpt
insmod ext2
set root='(hd0,gpt11)'
search --no-floppy --fs-uuid --set=root 7970d9cc-09d1-416b-a860-a161f55174cb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'elementary OS, with Linux 3.2.0-51-generic' --class elementary --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt11)'
    search --no-floppy --fs-uuid --set=root 7970d9cc-09d1-416b-a860-a161f55174cb
    linux    /boot/vmlinuz-3.2.0-51-generic.efi.signed root=UUID=7970d9cc-09d1-416b-a860-a161f55174cb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-51-generic
}
menuentry 'elementary OS, with Linux 3.2.0-51-generic (recovery mode)' --class elementary --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt11)'
    search --no-floppy --fs-uuid --set=root 7970d9cc-09d1-416b-a860-a161f55174cb
    echo    'Loading Linux 3.2.0-51-generic ...'
    linux    /boot/vmlinuz-3.2.0-51-generic.efi.signed root=UUID=7970d9cc-09d1-416b-a860-a161f55174cb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-51-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root B604ACB304AC77CF
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 8 (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 84ECB3ECECB3D6A0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "elementary OS Luna (0.2) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root d0d22194-e4a8-4190-bf9a-56bb9633ce70
    linux /vmlinuz root=/dev/sda9
    initrd /initrd.img
}
menuentry "elementary OS Luna (0.2) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root d0d22194-e4a8-4190-bf9a-56bb9633ce70
    linux /vmlinuz root=/dev/sda9
    initrd /initrd.img
}
menuentry "elementary OS Luna (0.2) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root d0d22194-e4a8-4190-bf9a-56bb9633ce70
    linux /boot/vmlinuz-3.2.0-51-generic root=/dev/sda9
    initrd /boot/initrd.img-3.2.0-51-generic
}
menuentry "elementary OS Luna (0.2) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root d0d22194-e4a8-4190-bf9a-56bb9633ce70
    linux /boot/vmlinuz-3.2.0-51-generic.efi.signed root=/dev/sda9
}
menuentry "elementary OS Luna (0.2) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root d0d22194-e4a8-4190-bf9a-56bb9633ce70
    linux /vmlinuz root=/dev/sda9
    initrd /initrd.img
}
menuentry "elementary OS Luna (0.2) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root d0d22194-e4a8-4190-bf9a-56bb9633ce70
    linux /vmlinuz root=/dev/sda9
    initrd /initrd.img
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------


=============================== sda11/etc/fstab: ===============================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=7970d9cc-09d1-416b-a860-a161f55174cb /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=3091-7187  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda10 during installation
UUID=4eaa58a3-034c-4208-8bfc-11d80bc78747 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda11: Location of files loaded by Grub: ===================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-51-generic               2
               =                boot/vmlinuz-3.2.0-51-generic                  1
               =                boot/vmlinuz-3.2.0-51-generic.efi.signed       1
               =                initrd.img                                     2
               =                vmlinuz                                        1


=========================== sdb1/boot/grub/grub.cfg: ===========================


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


menuentry "Try elementary OS without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install elementary OS" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


========================= sdb1/syslinux/syslinux.cfg: ==========================


--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50


# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/grub.cfg                             1


================= sdb1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1


============== sdb1: Version of COM32(R) files used by Syslinux: ===============


 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown GPT Partiton Type
dee2bfd3af3ddf11ba40e3a556d89593
Unknown BootLoader on sda1


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 87 71 91 30 4e  4f 20 4e 41 4d 45 20 20  |..).q.0NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200




========= Devices which don't seem to have a corresponding hard drive: =========


sdc 


=============================== StdErr Messages: ===============================


awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/elementary/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected



```

---

