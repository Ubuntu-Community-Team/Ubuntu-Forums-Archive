---
title: "Cannot boot into Ubuntu after installation alongside Windows 7"
date: 2017-12-18
forum: New to Ubuntu
---

### Post by jonas-muellergastell on 2017-12-18
I installed Ubuntu 16.04 from USB onto a laptop that has Windows 7 installed. I had created a ~100GB partition beforehand and selected "Install alongside Windows 7". Everything went fine. Now, however, I cannot boot into Ubuntu. There is no grub menu on start-up and when I go into boot manager, it tells me that there is win7 but nothing else shows up. 

I attached the results.txt from bootinfo below. It claims grub2 is installed and seems to be looking in the right direction on my drive... what is going on?

```
                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    310079488 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 97 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootwinre.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/lenovobt.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 30442 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   500,118,191   500,118,191  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   310,079,487   309,610,496 Data partition (Windows/Linux)
/dev/sda4     472,023,040   500,117,503    28,094,464 Data partition (Windows/Linux)
/dev/sda5     310,079,488   310,081,535         2,048 BIOS Boot partition
/dev/sda6     310,081,536   456,476,671   146,395,136 Data partition (Linux)
/dev/sda7     456,476,672   472,023,039    15,546,368 Swap partition (Linux)

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 59.2 GiB, 63518539776 bytes, 124059648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   124,059,647   124,057,600   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0872-2770                              vfat       SYSTEM_DRV
/dev/sda2                                                          
/dev/sda3        869276F09276E3D9                       ntfs       Windows7_OS
/dev/sda4        D4D2700BD26FF062                       ntfs       Lenovo_Recovery
/dev/sda5                                                          
/dev/sda6        bb80a290-66cb-42c8-86ee-b8a1d3b1288e   ext4       
/dev/sda7        14ad098d-d7b5-41c1-961d-bd868a9a6f44   swap       
/dev/sdb1        1DF5-1063                              vfat       UBUNTU 16_0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/ubuntu/Windows7_OS fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda6        /media/ubuntu/bb80a290-66cb-42c8-86ee-b8a1d3b1288e ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
else
  search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
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
  set timeout=30
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
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bb80a290-66cb-42c8-86ee-b8a1d3b1288e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
    else
      search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
    fi
        linux    /boot/vmlinuz-4.10.0-28-generic root=UUID=bb80a290-66cb-42c8-86ee-b8a1d3b1288e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.10.0-28-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bb80a290-66cb-42c8-86ee-b8a1d3b1288e' {
    menuentry 'Ubuntu, with Linux 4.10.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-28-generic-advanced-bb80a290-66cb-42c8-86ee-b8a1d3b1288e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
        else
          search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
        fi
        echo    'Loading Linux 4.10.0-28-generic ...'
            linux    /boot/vmlinuz-4.10.0-28-generic root=UUID=bb80a290-66cb-42c8-86ee-b8a1d3b1288e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 4.10.0-28-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-28-generic-init-upstart-bb80a290-66cb-42c8-86ee-b8a1d3b1288e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
        else
          search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
        fi
        echo    'Loading Linux 4.10.0-28-generic ...'
            linux    /boot/vmlinuz-4.10.0-28-generic root=UUID=bb80a290-66cb-42c8-86ee-b8a1d3b1288e ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 4.10.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-28-generic-recovery-bb80a290-66cb-42c8-86ee-b8a1d3b1288e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
        else
          search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
        fi
        echo    'Loading Linux 4.10.0-28-generic ...'
            linux    /boot/vmlinuz-4.10.0-28-generic root=UUID=bb80a290-66cb-42c8-86ee-b8a1d3b1288e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-28-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
    else
      search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  bb80a290-66cb-42c8-86ee-b8a1d3b1288e
    else
      search --no-floppy --fs-uuid --set=root bb80a290-66cb-42c8-86ee-b8a1d3b1288e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-869276F09276E3D9' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  869276F09276E3D9
    else
      search --no-floppy --fs-uuid --set=root 869276F09276E3D9
    fi
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=bb80a290-66cb-42c8-86ee-b8a1d3b1288e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=14ad098d-d7b5-41c1-961d-bd868a9a6f44 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 70 27 72 08 4e  4f 20 4e 41 4d 45 20 20  |..)p'r.NO NAME  |
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


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-ETkcphMr/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ETkcphMr/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ETkcphMr/Tmp_Log: No such file or directory

  
```

---

### Post by oldfred on 2017-12-18
For longer text or code please use code tags. Easy to add with Forum's advanced editor and # icon.

You used the older link to bootinfoscript. That is not maintained, but there is an much more updated fork.
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

Also the report from Boot-Repair uses the updated fork and adds even more info. And then all you have to post is link to pastebin site.
       
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
 It looks like you have Windows 7 in UEFI mode. That is a bit unusual as most Windows 7 systems are BIOS/MBR, but yours is UEFI/gpt. And Windows 7 does not support the UEFI Secure Boot mode, so make sure that stays off. It may say other or Windows and you must have "Other" as that is secure boot off. "Windows" setting is for Windows 8 or later with Secure boot on.
And then you installed Ubuntu in BIOS boot mode on gpt partitioned drive.

You should be able to dual boot but only from UEFI boot menu, but may have to turn off UEFI boot or turn on BIOS/CSM/Legacy boot mode. And then turn on UEFI again to boot Windows.

Boot-Repair also can convert your Ubuntu install to UEFI boot. It uninstalls grub-pc(BIOS) and installs grub-efi-amd64 and that also changes a few settings. Do not run an auto fix, only advanced mode and total uninstall of grub. Be sure to boot Ubuntu live installer in UEFI mode and then add Boot-Repair using ppa.

Before that be sure to back up Windows and particularly backup ESP. Your ESP is not showing the typical /EFI/Microsoft folder which most Windows systems use. You have just the fallback or /EFI/Boot folder which some systems do not even create, but sometimes we have to use that to boot Ubuntu as not all vendors comply with UEFI standards. And Boot-Repair will backup and rename /EFI/Boot/bootx64.efi which is your current Windows boot and copy shimx64.efi to bootx64.efi to make it an Ubuntu/grub boot. 

For time being there seems to be issues with Lenovo UEFI/BIOS and newer kernels in Ubuntu 17.10 or later. Stay with 16.04 for time being and do some research before upgrading to 18.04 next year.
      
 Ubuntu 17.10 "corrupting" BIOS - many LENOVO laptops models
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

---

