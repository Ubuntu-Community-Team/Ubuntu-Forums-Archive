---
title: "GRUB fails to load Windows 8 with ubuntu on external disk"
date: 2014-10-05
forum: New to Ubuntu
---

### Post by maxpesa on 2014-10-05
I've just installed Ubuntu from live DVD in my external HD to try it  before using it in dual boot with windows 8. I deleted my Windows backup  to make room for it so, even if I have the rescue disk I would get the  factory system.  
  Situation:
  if the external HD is connected on boot I get the correct GRUB which  lets me choose OS, but windows can't load, it says "can't load image" in  /EndingEntry or something similar.
  if it is not connected, I get a GRUB bash-like enviromment, but I  don't know anything about it. (Minimal bash-like line editing is  supported.)
  What can I do to at least recover Windows 8? 
  Boot Info Script:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi

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
    Boot files:        /bootmgr /Boot/BCD

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
256 heads, 63 sectors/track, 38761 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     2,844,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,844,672   591,591,423   588,746,752 Data partition (Windows/Linux)
/dev/sda5     591,591,424   625,141,759    33,550,336 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,046   231,190,527   231,188,482   f W95 Extended (LBA)
/dev/sdb5               2,048   231,190,527   231,188,480   7 NTFS / exFAT / HPFS
/dev/sdb2         231,190,528   259,522,559    28,332,032  82 Linux swap / Solaris
/dev/sdb3    *    259,522,560   976,772,559   717,250,000  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1AF88187F881623D                       ntfs       WINRE_DRV
/dev/sda2        9883-4C19                              vfat       SYSTEM_DRV
/dev/sda4        0480864E808645E0                       ntfs       Windows8_OS
/dev/sda5        603AFDBB3AFD8DF2                       ntfs       Lenovo_Recovery
/dev/sdb2        5de69a97-717c-43d6-b090-8967eff2b1d2   swap       
/dev/sdb3        2226bf96-3170-4af5-8bf5-971ee2df340e   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd2,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos3 --hint-efi=hd2,msdos3 --hint-baremetal=ahci2,msdos3  2226bf96-3170-4af5-8bf5-971ee2df340e
else
  search --no-floppy --fs-uuid --set=root 2226bf96-3170-4af5-8bf5-971ee2df340e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2226bf96-3170-4af5-8bf5-971ee2df340e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos3 --hint-efi=hd2,msdos3 --hint-baremetal=ahci2,msdos3  2226bf96-3170-4af5-8bf5-971ee2df340e
    else
      search --no-floppy --fs-uuid --set=root 2226bf96-3170-4af5-8bf5-971ee2df340e
    fi
    linux    /boot/vmlinuz-3.13.0-36-generic.efi.signed root=UUID=2226bf96-3170-4af5-8bf5-971ee2df340e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-36-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2226bf96-3170-4af5-8bf5-971ee2df340e' {
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-2226bf96-3170-4af5-8bf5-971ee2df340e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos3 --hint-efi=hd2,msdos3 --hint-baremetal=ahci2,msdos3  2226bf96-3170-4af5-8bf5-971ee2df340e
        else
          search --no-floppy --fs-uuid --set=root 2226bf96-3170-4af5-8bf5-971ee2df340e
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic.efi.signed root=UUID=2226bf96-3170-4af5-8bf5-971ee2df340e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-2226bf96-3170-4af5-8bf5-971ee2df340e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos3 --hint-efi=hd2,msdos3 --hint-baremetal=ahci2,msdos3  2226bf96-3170-4af5-8bf5-971ee2df340e
        else
          search --no-floppy --fs-uuid --set=root 2226bf96-3170-4af5-8bf5-971ee2df340e
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic.efi.signed root=UUID=2226bf96-3170-4af5-8bf5-971ee2df340e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-2226bf96-3170-4af5-8bf5-971ee2df340e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos3 --hint-efi=hd2,msdos3 --hint-baremetal=ahci2,msdos3  2226bf96-3170-4af5-8bf5-971ee2df340e
        else
          search --no-floppy --fs-uuid --set=root 2226bf96-3170-4af5-8bf5-971ee2df340e
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=2226bf96-3170-4af5-8bf5-971ee2df340e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-2226bf96-3170-4af5-8bf5-971ee2df340e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos3 --hint-efi=hd2,msdos3 --hint-baremetal=ahci2,msdos3  2226bf96-3170-4af5-8bf5-971ee2df340e
        else
          search --no-floppy --fs-uuid --set=root 2226bf96-3170-4af5-8bf5-971ee2df340e
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=2226bf96-3170-4af5-8bf5-971ee2df340e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-9883-4C19' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  9883-4C19
    else
      search --no-floppy --fs-uuid --set=root 9883-4C19
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc3 during installation
UUID=2226bf96-3170-4af5-8bf5-971ee2df340e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=9883-4C19  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sdc2 during installation
UUID=5de69a97-717c-43d6-b090-8967eff2b1d2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  eb 06 00 00 00 00 00 00  33 c0 fa 8e d0 bc 00 7c  |........3......||
00000010  fb 8e d8 8b f4 8e c0 bf  26 7e 06 57 bf 00 7e b9  |........&~.W..~.|
00000020  00 02 fc f3 a4 cb be 02  7e ad 8b c8 66 ad bb 00  |........~...f...|
00000030  80 83 f9 00 75 2e be be  7f ac 3c 80 74 1b 83 c6  |....u.....<.t...|
00000040  0f 81 fe fe 7f 75 f2 be  44 7f e8 33 00 be 92 7f  |.....u..D..3....|
00000050  e8 2d 00 33 c0 cd 16 cd  19 83 c6 07 66 ad b9 01  |.-.3........f...|
00000060  00 bb 00 7c 32 f6 e8 24  00 be 62 7f 72 dc 8b f3  |...|2..$..b.r...|
00000070  81 c6 fe 01 ad be 7f 7f  3d 55 aa 75 cd 06 53 cb  |........=U.u..S.|
00000080  b4 0e fc ac 3c 00 74 04  cd 10 eb f7 c3 66 60 1e  |....<.t......f`.|
00000090  06 66 50 53 51 52 8b ec  b4 41 bb aa 55 8a 56 00  |.fPSQR...A..U.V.|
000000a0  cd 13 72 39 81 fb 55 aa  75 33 f6 c1 01 74 2e 66  |..r9..U.u3...t.f|
000000b0  33 c0 66 50 66 8b 46 06  66 50 8b 46 0a 50 8b 46  |3.fPf.F.fP.F.P.F|
000000c0  04 50 66 b8 10 00 01 00  66 50 16 1f 8b f4 8b 56  |.Pf.....fP.....V|
000000d0  00 b8 00 42 02 e6 cd 13  83 c4 10 eb 50 b4 08 8a  |...B........P...|
000000e0  56 00 33 ff 8e c7 cd 13  72 43 66 83 e1 3f fe c6  |V.3.....rCf..?..|
000000f0  8a de 66 8b 46 06 66 33  d2 66 f7 f1 42 52 8a cb  |..f.F.f3.f..BR..|
00000100  66 33 d2 66 f7 f1 8a f2  59 66 3d ff 03 00 00 77  |f3.f....Yf=....w|
00000110  1b 86 e0 c0 e0 06 03 c8  8e 46 0a 8b 5e 04 8b 46  |.........F..^..F|
00000120  00 8a d0 80 c4 02 b0 01  cd 13 eb 01 f9 5a 59 5b  |.............ZY[|
00000130  66 58 72 0b 81 c3 00 02  66 40 49 0f 85 52 ff 07  |fXr.....f@I..R..|
00000140  1f 66 61 c3 0d 0a 42 4f  4f 54 20 20 20 70 61 72  |.fa...BOOT   par|
00000150  74 69 74 69 6f 6e 20 6e  6f 74 20 66 6f 75 6e 64  |tition not found|
00000160  21 00 0d 0a 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |!...Error loadin|
00000170  67 20 62 6f 6f 74 20 73  65 63 74 6f 72 21 00 0d  |g boot sector!..|
00000180  0a 42 61 64 20 62 6f 6f  74 20 73 65 63 74 6f 72  |.Bad boot sector|
00000190  21 00 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |!...Press any ke|
000001a0  79 2e 2e 2e 0d 0a 00 00  00 00 00 00 00 00 00 00  |y...............|
000001b0  65 6d 00 00 00 63 7b 9a  b0 36 70 1b 00 00 00 20  |em...c{..6p.... |
000001c0  1f 00 0f fe ff ff fe 07  00 00 02 a8 c7 0d 00 fe  |................|
000001d0  ff ff 82 fe ff ff 00 b0  c7 0d 00 50 b0 01 80 fe  |...........P....|
000001e0  ff ff 83 fe ff ff 00 00  78 0f d0 5d c0 2a 00 00  |........x..].*..|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1f 00  |........?....H..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 19 4c 83 98 4e  4f 20 4e 41 4d 45 20 20  |..).L..NO NAME  |
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

cat: /tmp/BootInfo-LTwHcu4r/Tmp_Log: No such file or directory


```

---

### Post by Dennis N on 2014-10-05
You omitted some of the boot info script with important information, but one can make a couple of observations:

If sdb is disconnected, there is no grub because grub.cfg is on sdb3.
Disk sdb has an extended partition, so its an msdos partition setup,  is not gpt like on disk sda. Confirmed, since It is not flagged as gpt in the summary under Drive/Partition Info. This setup may not (I guess probably won't) work.

Post complete boot info script for better analysis.

---

### Post by maxpesa on 2014-10-05
I didn't omit anything, but your observations were correct, I think.
I installed the bootloader (GRUB?) on sdc (the external HD, was mounted as sdc during installation).

The problem seemd SecureBoot ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)). the bug you posted here seemd like mine, but  changing boot priority (to ubuntu again) made me encounter the same  problem, even with SecureBoot disabled. I think my mistake was setting  the bootloader in 'dev\sdc\' so GRUB is not complete  I'm a newbie to  linux so I really don't know if I'm wrong... Do you think that I can  "delete" GRUB to get the system exactly as it was before?

---

### Post by yancek on 2014-10-05
Your grub.cfg menuentry for Ubuntu shows (hd2, msdos3) which is the equivalent of sdc3.  Your output also shows only sda and sdb partitions since you no longer have the flash installed.  Change the menuentry in grub.cfg for Ubuntu to (hd1,msdos3) then copy it to /etc/grub.d/40_custom and run sudo update-grub.  Actually, just notice that you have an EFI partition with the Ubuntu efi files in sda2 but no windows files there.  You need to use EFI for both systems or MBR for both.  If you mix them, you get the results you are reporting so you need to change one of them.

---

### Post by oldfred on 2014-10-05
Windows only boots from a gpt drive with UEFI. And it looks like your Windows install in sda is a UEFI install, but your efi partition now does not have any efi boot files for Windows, just Ubuntu which is on sdb in a MBR partitioned drive. I used to think that was impossible as UEFI required gpt, but others have done what you have done and have the grub boot files in a gpt drive, but main Ubuntu install in a MBR(msdos) partitioned drive.

Must better to have external drive partitioned with gpt. With Ubuntu you could boot with UEFI if the external has an efi partition or you could boot with BIOS if you have a bios_grub partition. But having Ubuntu's efi boot on sda, but install on sdb, will be difficult to maintain.

You may be able to manually create an efi boot folder for Windows in your efi partition and copy bootmfgw.efi from your main install. But you also need the /boot/BCD. Best if you had created a Windows 8 repair flash drive as then you could just easily run repairs from that. You may be able to use some third party BCD repair tools to add a BCD.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Some suggestions on partitioning, which you can use as a starting point for reinstalling on external. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

Most of these will be similar to your install, but you will want to install grub to the external whether when installing it is sdb or sdc.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by maxpesa on 2014-10-05
Thank you, oldfred, your reply is very good, bu I have to admit I don't have a very clear knowledge of all these things about OSs. I installed lots of linux flavors in another pc, but with Windows XP everything was simple. 
So, if I understood correctly, what I should do is:
1.Create a Win8 System Repair Disc (fortunately I already have one) as seen here [http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
2.Use it to repair boot issues. -> Does it remove the actually pointless GRUB?
3.Format my extHD in this way:
   Ubuntu's standard install is just / (root) & swap, but it is better  to add another partition for /home if allocating over 30GB.:
   Only if gpt -  all partitions in gpt are primary:
   gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI,  you only can have one per drive, so if already existing do not attempt  another)
   gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
   for gpt(GUID) or MBR(msdos) partitioning
4. Follow this [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html) to get the new enviromment work properly

Did I understand correctly?

PS: Worried about possible brick (do we call it this way even for computers?), I entered in Windows Troubleshooting and ran SWindows Automatic Repair, which loaded a previous "good" restore point (now Windows seems working perfectly, as before installation, since I changed boot priority in BIOS, but this of course is a palliative)

---

### Post by oldfred on 2014-10-05
I did not think your Windows would boot in BIOS/CSM mode. Or is system not finding BIOS boot in MBR and auto switching to UEFI?

I would leave grub in efi partition in internal drive so you can boot Ubuntu if needed until you are sure Windows boots ok. But you will have to manually delete the /efi/ubuntu folder and manually delete the entry in UEFI for that. 

If dual booting with Windows you may also want a NTFS data partition on external as Windows will not read any Linux formatted partitions.

I prefer to create partitions in advance with gparted, but you can create all but the NTFS partitions during install. But be sure to make drive gpt partitioned. And converting from MBR to gpt will erase your data on external, so back that up if needed. In gparted before doing anything select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 
You still need to boot installer in UEFI boot mode to install in UEFI mode. And use Something Else, but if partitions exist you can skip the partition creation steps in the install and just mount / partition and /home with ext4 format.

---

### Post by maxpesa on 2014-10-06
Right now I don't have anythig I need in ubuntu, can I format the recently-created partitions in my external HD (sdb2 and sdb3)? 

> But you will have to manually delete the /efi/ubuntu folder and manually delete the entry in UEFI for that.

do you mean this?[IMG]http://www.mediafire.com/view/nuysbgp1sl2ob6c/Cattura40.PNG[/IMG]


[http://www.mediafire.com/view/nuysbgp1sl2ob6c/Cattura40.PNG](http://www.mediafire.com/view/nuysbgp1sl2ob6c/Cattura40.PNG)
if you can't see the picture

I'm Italian, but there aren't lots of words, I think you'll understand anyways

---

### Post by oldfred on 2014-10-06
the ubuntu folder in the screenshot has grub and ubuntu's boot files. The UEFI adds that entry for ubuntu into its NVRAM, so you have to delete that folder before deleting the UEFI entry.
Every system you install in UEFI boot mode adds a separate folder with its boot files.

Some systems let you manage UEFI entries in UEFI/BIOS. Others will need you to use efibootmgr which is in Ubuntu if booted in UEFI mode.
 # from liveDVD or flash and use efibootmgr
modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by maxpesa on 2014-10-06
Ok, finally the situation is clear for me. Now I'll format my extHD linux partitions and then get a backup of Windows 8 (with, ofc, a backup of EFI, I think) .

As it is complete I'll do what you said.
Have a look at this image, does the description on the right say that I just jave to press Delete to remove "ubuntu" entry? 
[http://www.mediafire.com/view/q7ur1n2lpx6hrfg/IMG_20141006_181934.jpg](http://www.mediafire.com/view/q7ur1n2lpx6hrfg/IMG_20141006_181934.jpg)

---

### Post by oldfred on 2014-10-06
It looks like then your system lets you delete it, some do not.
But remove ubuntu folder first in efi partition or it may just re-add it again on a reboot.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by maxpesa on 2014-10-06
Thank you for your support, everything is fine now 
Have a nice day,
Massimo

---

