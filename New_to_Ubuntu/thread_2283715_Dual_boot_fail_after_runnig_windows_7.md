---
title: "Dual boot fail after runnig windows 7"
date: 2015-06-23
forum: New to Ubuntu
---

### Post by nelson6 on 2015-06-23
Hi, I am new to Ubuntu. I have install ubuntu 15.04 in dual boot with my windows 7. However, after running widows 7 and reboot my computer, the system fail and I use live usb ubuntu to boot the system. Then fix the problem with boot-repair and can boot from windows 7 again. However,   after running widows 7 the system dead again. Please help, thank you very much.
 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 11097372 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,052       205,199       203,148   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   409,806,847   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda3         409,806,848   859,377,538   449,570,691   7 NTFS / exFAT / HPFS
/dev/sda4         859,377,662   976,771,071   117,393,410   5 Extended
/dev/sda5         859,377,664   968,615,935   109,238,272  83 Linux
/dev/sda6         968,617,984   976,771,071     8,153,088  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7.5 GiB, 8000110592 bytes, 15625216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1CF0D380F0D35E98                       ntfs       &#31995;&#32113;&#20445;&#30041;
/dev/sda2        E05CC7345CC7046E                       ntfs       
/dev/sda3        3E26EF9526EF4C89                       ntfs       DATA
/dev/sda5        78f01101-4c90-4165-a12e-0d527f85fdf3   ext4       
/dev/sda6        2acecc43-e406-47eb-a619-2f6980132481   swap       
/dev/sdb1        1413-1362                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jun 24 01:49 ata-PLDS_DVD+_-RW_DH-16ACS_H_HDD0H73639386522DA01 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jun 24 02:01 ata-WDC_WD5000AAKX-75U6AA0_WD-WCC2EMK00552-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Jun 24 02:00 usb-SanDisk_Cruzer_Slice_20044527710F55A0A102-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun 24 02:00 usb-SanDisk_Cruzer_Slice_20044527710F55A0A102-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jun 24 02:01 wwn-0x9224883084982374401x -> ../../sda
lrwxrwxrwx 1 root root 10 Jun 24 02:01 wwn-0x9224883084982374401x-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun 24 02:01 wwn-0x9224883084982374401x-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun 24 02:01 wwn-0x9224883084982374401x-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jun 24 02:01 wwn-0x9224883084982374401x-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jun 24 02:01 wwn-0x9224883084982374401x-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jun 24 02:01 wwn-0x9224883084982374401x-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
else
  search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
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
  set timeout=10
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
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
else
  search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
fi
insmod tga
if background_image /boot/grub/ubuntu_kylin_grub_bg.tga; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
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
menuentry 'Ubuntu Kylin GNU/Linux' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-78f01101-4c90-4165-a12e-0d527f85fdf3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
    else
      search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
    fi
    linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=78f01101-4c90-4165-a12e-0d527f85fdf3 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-15-generic
}
submenu 'Advanced options for Ubuntu Kylin GNU/Linux' $menuentry_id_option 'gnulinux-advanced-78f01101-4c90-4165-a12e-0d527f85fdf3' {
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-78f01101-4c90-4165-a12e-0d527f85fdf3' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
        else
          search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=78f01101-4c90-4165-a12e-0d527f85fdf3 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-78f01101-4c90-4165-a12e-0d527f85fdf3' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
        else
          search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=78f01101-4c90-4165-a12e-0d527f85fdf3 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-78f01101-4c90-4165-a12e-0d527f85fdf3' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
        else
          search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=78f01101-4c90-4165-a12e-0d527f85fdf3 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-15-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
    else
      search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  78f01101-4c90-4165-a12e-0d527f85fdf3
    else
      search --no-floppy --fs-uuid --set=root 78f01101-4c90-4165-a12e-0d527f85fdf3
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-1CF0D380F0D35E98' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1CF0D380F0D35E98
    else
      search --no-floppy --fs-uuid --set=root 1CF0D380F0D35E98
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-E05CC7345CC7046E' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  E05CC7345CC7046E
    else
      search --no-floppy --fs-uuid --set=root E05CC7345CC7046E
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=78f01101-4c90-4165-a12e-0d527f85fdf3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=2acecc43-e406-47eb-a619-2f6980132481 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

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

menuentry "Try Ubuntu Kylin without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu Kylin" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  64 b6 b7 ff 00 0f d3 da  bf 17 3e 2c 45 e5 fc 45  |d.........>,E..E|
00000010  f1 74 5c 0f 2f 5e b9 8f  67 4c 01 23 57 ad 8f 5e  |.t\./^..gL.#W..^|
00000020  e5 27 e4 5c a7 3a 91 e7  91 e5 e5 79 da 40 c0 1d  |.'.\.:.....y.@..|
00000030  7b 62 a1 da 43 1d bd 33  85 35 e6 98 c2 ea 5b 16  |{b..C..3.5....[.|
00000040  48 0b 0a 64 e0 92 6a 80  fb d8 c8 1f 37 af 4a ae  |H..d..j.....7.J.|
00000050  67 6b 11 28 b7 27 a1 7a  03 f3 15 27 8c 92 1b 8e  |gk.(.'.z...'....|
00000060  b4 d9 14 09 0b 02 70 49  e4 f7 a9 2e 29 44 44 93  |......pI....)DD.|
00000070  e6 63 93 8f cf 06 a4 96  6d c0 82 08 3c 0d d8 3d  |.c......m...<..=|
00000080  2a a3 ba 34 85 f7 4c cc  9d c0 56 04 e4 13 81 c1  |*..4..L...V.....|
00000090  c6 6a 9e ec 48 32 0f 0b  d4 fa d6 c4 4d c9 b7 62  |.j..H2......M..b|
000000a0  65 0b 21 90 9c 01 8e 7b  e6 ab 3a 28 77 3d 89 18  |e.!....{..:(w=..|
000000b0  e9 83 59 47 e2 d4 57 7a  89 2a a3 ff 00 bc 98 c0  |..YG..Wz.*......|
000000c0  eb cd 16 8e 4b 80 72 1b  b6 70 29 d4 0d d6 a8 dd  |....K.r..p).....|
000000d0  b5 52 ea 57 77 ca 79 61  ed 57 0a 90 88 54 e3 0c  |.R.Ww.ya.W...T..|
000000e0  40 07 bd 63 3d 9e 83 db  62 a4 80 ef 6f 30 6d 25  |@..c=...b...o0m%|
000000f0  7e b8 a2 25 22 50 14 f4  5c 75 c6 7b d3 8b ba 1a  |~..%"P..\u.{....|
00000100  6e d6 b9 bb 62 56 47 0b  20 c8 cf 5e 71 9c d6 de  |n...bVG. ..^q...|
00000110  a4 88 a8 88 8b c8 5c 9c  1e bd ff 00 cf d6 b2 92  |......\.........|
00000120  b3 dc 51 a8 e3 a3 46 11  21 88 20 1c 0c 1c 1e c6  |..Q...F.!. .....|
00000130  ba 9d 2d 16 18 23 91 88  7f 31 8b 15 5c 1c 75 15  |..-..#...1..\.u.|
00000140  0d 5e f7 2a 31 8c 9d a4  cd e4 96 31 06 f2 06 e0  |.^.*1......1....|
00000150  f8 e0 8a 91 24 0a b2 36  3e 52 72 3a 56 06 53 92  |....$..6>Rr:V.S.|
00000160  8b 6a 04 9f 69 61 1f de  c6 e5 e7 0b c8 15 5e 29  |.j..ia........^)|
00000170  58 ba c9 9c 6d e0 e4 80  41 e6 88 46 d5 1c 8e aa  |X...m...A..F....|
00000180  52 6e 8d 99 b0 2e 50 26  e5 39 18 00 63 bd 3d a4  |Rn....P&.9..c.=.|
00000190  31 a6 72 32 f9 23 af 02  a6 31 a8 ea 36 ce 75 19  |1.r2.#...1..6.u.|
000001a0  36 d9 51 6e 33 36 d6 e3  04 e3 9e 71 53 1d 41 48  |6.Qn36.....qS.AH|
000001b0  68 48 e1 b3 93 df 35 d7  08 5d 6e 76 42 8b 00 fe  |hH....5..]nvB...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 82 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  82 06 00 70 7c 00 00 00  |...........p|...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/5219/mounts) leaked on lvs invocation. Parent PID 15424: bash
File descriptor 63 (pipe:[62206]) leaked on lvs invocation. Parent PID 15424: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-06-24__02h00 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in live-session (Ubuntu 15.04, vivid, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash --- BOOT_IMAGE=/casper/vmlinuz.efi
ls: cannot access /home/usr/.config: No such file or directory

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda5:Ubuntu 15.04 (15.04):Ubuntu:linux

=================== blkid:
/dev/sda1: LABEL="M-gM-3M-;M-gM-5M-1M-dM-?M-^]M-gM-^UM-^Y" UUID="1CF0D380F0D35E98" TYPE="ntfs" PARTUUID="c476dbe9-01"
/dev/sda2: UUID="E05CC7345CC7046E" TYPE="ntfs" PARTUUID="c476dbe9-02"
/dev/sda3: LABEL="DATA" UUID="3E26EF9526EF4C89" TYPE="ntfs" PARTUUID="c476dbe9-03"
/dev/sda5: UUID="78f01101-4c90-4165-a12e-0d527f85fdf3" TYPE="ext4" PARTUUID="c476dbe9-05"
/dev/sdb1: LABEL="UUI" UUID="1413-1362" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/sda6: UUID="2acecc43-e406-47eb-a619-2f6980132481" TYPE="swap" PARTUUID="c476dbe9-06"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

sfdisk: Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Apr 23 11:21 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr  6 20:43 00_header
-rwxr-xr-x 1 root root  6058 Feb 11 19:53 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr  6 20:43 10_linux
-rwxr-xr-x 1 root root 11082 Apr  6 20:43 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar  6 16:23 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr  6 20:43 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr  6 20:43 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  6 20:43 40_custom
-rwxr-xr-x 1 root root   216 Apr  6 20:43 41_custom
-rw-r--r-- 1 root root   483 Apr  6 20:43 README




=================== sda5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu Kylin
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD5000AAKX-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      1051kB  105MB  104MB   primary   ntfs            boot
2      106MB   210GB  210GB   primary   ntfs
3      210GB   440GB  230GB   primary   ntfs
4      440GB   500GB  60.1GB  extended
5      440GB   496GB  55.9GB  logical   ext4
6      496GB   500GB  4174MB  logical   linux-swap(v1)


Model: SanDisk Cruzer Slice (scsi)
Disk /dev/sdb: 8000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  8000MB  8000MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA WDC WD5000AAKX-7:;
1:1051kB:105MB:104MB:ntfs::boot;
2:106MB:210GB:210GB:ntfs::;
3:210GB:440GB:230GB:ntfs::;
4:440GB:500GB:60.1GB:::;
5:440GB:496GB:55.9GB:ext4::;
6:496GB:500GB:4174MB:linux-swap(v1)::;

BYT;
/dev/sdb:8000MB:scsi:512:512:msdos:SanDisk Cruzer Slice:;
1:16.4kB:8000MB:8000MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL    MODEL            UUID
sda   disk          465.8G          WDC WD5000AAKX-7
sda1  part ntfs      99.2M &#31995;&#32113;&#20445;&#30041;                  1CF0D380F0D35E98
sda2  part ntfs     195.3G                           E05CC7345CC7046E
sda3  part ntfs     214.4G DATA                      3E26EF9526EF4C89
sda4  part              1K
sda5  part ext4      52.1G                           78f01101-4c90-4165-a12e-0d527f85fdf3
sda6  part swap       3.9G                           2acecc43-e406-47eb-a619-2f6980132481
sdb   disk            7.5G          Cruzer Slice
sdb1  part vfat       7.5G UUI                       1413-1362
sr0   rom            1024M          DVD+-RW DH-16ACS
loop0 loop squashfs   1.8G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         [SWAP]
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1951240k,nr_inodes=487810,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=393136k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=393136k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hugepages i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg kvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net watchdog watchdog0 xconsole zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 04 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  8b 19 03 00 00 00 00 00  |................|
00000030  10 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.!..............|
00000040  f6 00 00 00 01 00 00 00  98 5e d3 f0 80 d3 f0 1c  |.........^......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff ff 69 18 00 00 00 00  |..........i.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  6e 04 c7 5c 34 c7 5c e0  |........n..4..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 6d 18  |........?....(m.|
00000020  00 00 00 00 80 00 80 00  80 e7 cb 1a 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  89 4c ef 26 95 ef 26 3e  |.........L.&..&>|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     384M  5.9M  379M   2% /run
/dev/sdb1      vfat      7.5G  5.8G  1.7G  78% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   1.9G  296M  1.6G  16% /
tmpfs          tmpfs     1.9G   84K  1.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     1.9G   48K  1.9G   1% /tmp
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     384M   56K  384M   1% /run/user/999
/dev/sda1      fuseblk   100M   25M   75M  25% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   196G   60G  136G  31% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   215G   45G  171G  21% /mnt/boot-sav/sda3
/dev/sda5      ext4       52G  5.4G   44G  11% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/loop0: 1.8 GiB, 1866420224 bytes, 3645352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc476dbe9

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2052    205199    203148  99.2M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 409806847 409600000 195.3G  7 HPFS/NTFS/exFAT
/dev/sda3       409806848 859377538 449570691 214.4G  7 HPFS/NTFS/exFAT
/dev/sda4       859377662 976771071 117393410    56G  5 Extended
/dev/sda5       859377664 968615935 109238272  52.1G 83 Linux
/dev/sda6       968617984 976771071   8153088   3.9G 82 Linux swap / Solaris

Disk /dev/sdb: 7.5 GiB, 8000110592 bytes, 15625216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 15625215 15625184  7.5G  c W95 FAT32 (LBA)
/dev/sdb3       24897    24897        0    0B  0 Empty



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sda5 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s



*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
Subsystem: Dell Device [1028:052c]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-22ubuntu1,grub-install (GRUB) 2.

Reinstall the GRUB of sda5 into the MBR of sda
Installing for i386-pc platform.
grub-install: warning: Sector 5 is already in use by the program `ZISD'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda5 update-grub
Generating grub configuration file ...
Found background image: ubuntu_kylin_grub_bg.tga
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

```
   [Download as text]("http://paste.ubuntu.com/11765506/plain/")

---

### Post by oldfred on 2015-06-23
Did you see this:

 grub-install: warning: Sector 5 is already in use by the program `ZISD'; avoiding it. 

Grub is trying to work around Windows software that is also using the sectors just after the MBR for code. It looks like your ZISD program is interfering with grub. 
What is that software?

---

### Post by nelson6 on 2015-06-24
Thank you! How can I install the grub in another sector? The ZISD may be the antivirus programme. I try to stop it.

---

### Post by oldfred on 2015-06-24
You cannot, grub has to be in MBR and also then uses sectors after MBR. It does now try to work around software that writes into the sectors after the MBR, but other software may step on grub2's boot code and cause issues.

Best to use different software in Windows if at all possible. 

There are ways to install grub to a partition and then use EasyBCD. But that is not recommended as grub2 does not fit into the partition's boot sector. It has to convert to block lists or hard coded addresses. Then any update to grub or even a fsck may move a file's address and break grub.

Another alternative if you really have to keep that software is just to install grub to a flash drive. Then when you want to boot Ubuntu plug in flash drive. If you set flash drive as first in boot order, it will then boot grub/Ubuntu when plugged in.

If you install grub to flash drive then that will overwrite the boot loader for your live installer, so you need to have another flash drive. If flash drive sdb.
       sudo grub-install /dev/sdb

    
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by cariboo on 2015-06-24
There may be a solution to your problem [here.]("https://www.novell.com/communities/coolsolutions/grub-and-zisd/")

---

### Post by nelson6 on 2015-06-25
USB bootup is a good choice for me. It works. thank you!

---

### Post by jerry49 on 2015-06-25
I had "head" about problems running Ubuntu 15.04, maybe earlier too, dual boot with windows.  I nevertheless installed Ubuntu 15.04 dual boot on my Acer Netbook (seems to have the needed resources, it came with Windows 7 Starter - guess about 5 years ago), no immediate problems.  I am offered on power up to default to Ubuntu or to step down to Windows to boot Windows.  The installation resulted in Windows being given about 100 GB and Ubuentu 40 GB, more than enough for my uses - I believe.

I was also successful in porting Thunderbird Profile data to Thunderbird Ubuntu.  But, after a few time using the Firefox browser I found extensive build up of delays, and maybe other problems.  

Is it better to run Ubuntu on a USB memory stick?  I figure that has to be slower than having Ubuntu on the HDD, maybe not.

is ZISD a generic W7 problem, or is that something special/unique the OP has?

I haven't yet explored the links offered in this thread, so post here in case my problem is an "off the top of the head" answer

Thanks,

EDIT  Read the Novell linked solution, looks to be over my head (don't write code, just changing the Thunderbird profile.ini was a big step for me)  still looking for a recommendation.

---

### Post by oldfred on 2015-06-25
@jerry49
Better to start your own thread on your issues.
The ZISD issue is the first time I have seen that one. But flexnet which is software to control DRM or licenses for Windows proprietary software like Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab & others have similar issues because of the Windows flexnet security software.

If you have a newer computer with USB3 ports and USB3 flash, system will be reasonably fast. USB2 ports and USB2 flash drive is functional with a lighter weight version like Lubuntu or Xubuntu. Flash drives do not have a long life either.

---

