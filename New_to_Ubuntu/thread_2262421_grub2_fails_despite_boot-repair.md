---
title: "grub2 fails despite boot-repair"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by st_le on 2015-01-24
Trying desparately to boot xubuntu on my old asus laptop.

Boot-repair claims to finish succesfully, but on reboot grub2 always starts in rescue mode.
Previously, I had winxp running on the laptop.
I have already completely formatted the laptop and newly installed xubuntu, but in vain.

Below you can see the Boot Info.
Any help is appreciated

Greetings
stle




 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 NTFS / exFAT / HPFS
/dev/sda2          40,966,142   312,580,095   271,613,954   5 Extended
/dev/sda5          40,966,144    84,494,335    43,528,192  83 Linux
/dev/sda6         310,618,112   312,580,095     1,961,984  82 Linux swap / Solaris
/dev/sda7          84,496,384   310,616,063   226,119,680  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A88C66BB8C6683A2                       ntfs       
/dev/sda5        5504b4a2-bcee-4162-9edb-9d443d4193f8   ext4       
/dev/sda7        a2d7f297-9889-440a-987a-92bb16e0a367   ext4       
/dev/sr0                                                iso9660    Boot-Repair-Disk 32bit
/dev/zram0       73bd653f-2eb3-4000-a60d-81776200e42a   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jan 24 17:47 ata-SAMSUNG_HM160HC_S12TJDRZB28409 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 24 17:47 ata-SAMSUNG_HM160HC_S12TJDRZB28409-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 24  2015 ata-SAMSUNG_HM160HC_S12TJDRZB28409-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 24  2015 ata-SAMSUNG_HM160HC_S12TJDRZB28409-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 24  2015 ata-SAMSUNG_HM160HC_S12TJDRZB28409-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 24  2015 ata-SAMSUNG_HM160HC_S12TJDRZB28409-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Jan 24  2015 ata-TOSHIBA_DVD-ROM_SD-R2312_Z34A415282 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan 24 17:47 wwn-0x50f000002a228409 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 24 17:47 wwn-0x50f000002a228409-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 24  2015 wwn-0x50f000002a228409-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 24  2015 wwn-0x50f000002a228409-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 24  2015 wwn-0x50f000002a228409-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 24  2015 wwn-0x50f000002a228409-part7 -> ../../sda7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
--------------------------------------------------------------------------------

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5504b4a2-bcee-4162-9edb-9d443d4193f8
else
  search --no-floppy --fs-uuid --set=root 5504b4a2-bcee-4162-9edb-9d443d4193f8
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5504b4a2-bcee-4162-9edb-9d443d4193f8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5504b4a2-bcee-4162-9edb-9d443d4193f8
    else
      search --no-floppy --fs-uuid --set=root 5504b4a2-bcee-4162-9edb-9d443d4193f8
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=5504b4a2-bcee-4162-9edb-9d443d4193f8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5504b4a2-bcee-4162-9edb-9d443d4193f8' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-5504b4a2-bcee-4162-9edb-9d443d4193f8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5504b4a2-bcee-4162-9edb-9d443d4193f8
        else
          search --no-floppy --fs-uuid --set=root 5504b4a2-bcee-4162-9edb-9d443d4193f8
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=5504b4a2-bcee-4162-9edb-9d443d4193f8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-5504b4a2-bcee-4162-9edb-9d443d4193f8' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5504b4a2-bcee-4162-9edb-9d443d4193f8
        else
          search --no-floppy --fs-uuid --set=root 5504b4a2-bcee-4162-9edb-9d443d4193f8
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=5504b4a2-bcee-4162-9edb-9d443d4193f8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5504b4a2-bcee-4162-9edb-9d443d4193f8
    else
      search --no-floppy --fs-uuid --set=root 5504b4a2-bcee-4162-9edb-9d443d4193f8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  5504b4a2-bcee-4162-9edb-9d443d4193f8
    else
      search --no-floppy --fs-uuid --set=root 5504b4a2-bcee-4162-9edb-9d443d4193f8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-A88C66BB8C6683A2' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  A88C66BB8C6683A2
    else
      search --no-floppy --fs-uuid --set=root A88C66BB8C6683A2
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
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
UUID=5504b4a2-bcee-4162-9edb-9d443d4193f8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=d321de01-f373-4328-a51f-bcd462e0b76f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  03 11 e4 8b 11 00 13 00  00 00 cb ff 7c fe 05 12  |............|...|
00000010  94 08 be ff 0b 13 00 00  00 74 ff 3e fe 06 22 e4  |.........t.>..".|
00000020  cf cd 09 44 03 13 00 00  00 bd fc a0 fd 06 22 90  |...D..........".|
00000030  dc 01 37 23 00 13 00 00  00 66 fe 01 fe 06 32 14  |..7#.....f....2.|
00000040  a1 e0 db df 08 13 00 00  00 bd ff 41 fe 09 23 f0  |...........A..#.|
00000050  a7 08 81 1f c2 a0 f1 0f  13 00 00 00 68 fe 0c fe  |............h...|
00000060  06 23 1c 81 d8 b8 ef 0d  13 00 00 00 aa fd d5 fd  |.#..............|
00000070  06 32 f0 e4 08 e4 ce 3e  13 00 00 00 df fd e9 fd  |.2.....>........|
00000080  09 32 64 5f 33 02 f8 03  09 90 0c 13 00 00 00 fe  |.2d_3...........|
00000090  fd d7 fd 07 33 14 38 ee  ef 08 22 00 13 00 00 00  |....3.8...".....|
000000a0  20 fd c7 fd 05 12 90 f7  cd 43 0c 13 00 00 00 49  | ........C.....I|
000000b0  01 a0 fe 06 22 98 50 74  f6 fc 00 13 00 00 00 23  |....".Pt.......#|
000000c0  02 ae fe 05 12 98 10 ad  df 0f 13 00 00 00 84 01  |................|
000000d0  9c fe 06 22 18 21 f8 fe  7d 00 13 00 00 00 60 fd  |...".!..}.....`.|
000000e0  cd fd 0b 22 f0 23 40 08  bf 0c 20 f4 d0 fa 03 13  |...".#@... .....|
000000f0  00 00 00 df 01 72 fe 0b  13 10 01 fc ff 81 d3 fe  |.....r..........|
00000100  87 22 bf 00 13 00 00 00  8f 00 4d fe 0c 32 94 20  |."........M..2. |
00000110  f4 23 08 7e 07 04 be 01  be 00 13 00 00 00 c3 fc  |.#.~............|
00000120  9c fd 09 22 b0 41 b2 fe  c1 6b ff 05 3f 13 00 00  |...".A...k..?...|
00000130  00 0f 01 7c fe 07 24 3c  c6 80 c3 bb 9f 00 13 00  |...|..$<........|
00000140  00 00 fe ff 20 fe 06 22  94 9c fd 3e 47 00 13 00  |.... .."...>G...|
00000150  00 00 28 02 89 fe 06 22  8c 30 b8 ff 9c 00 13 00  |..(....".0......|
00000160  00 00 b0 fc bf fd 08 22  68 00 86 00 80 10 00 32  |......."h......2|
00000170  13 00 00 00 59 01 94 fe  0d 42 28 77 f6 7b c2 08  |....Y....B(w.{..|
00000180  74 43 ff eb 04 0a 00 13  00 00 00 e1 fc 37 03 05  |tC...........7..|
00000190  12 74 df 43 84 34 13 00  00 00 a0 fc 6a 03 06 23  |.t.C.4......j..#|
000001a0  20 db f7 b8 11 02 13 00  00 00 4d fc 1f 03 07 33  | .........M....3|
000001b0  dc c8 20 28 38 ef 03 13  00 00 00 77 fc 21 00 fe  |.. (8......w.!..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 98 02 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff c9 8a  12 10 39 f5 1d 00 00 00  |..........9.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 10 (/proc/2340/mounts) leaked on lvs invocation. Parent PID 11765: bash
File descriptor 63 (pipe:[26078]) leaked on lvs invocation. Parent PID 11765: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-01-24__17h45 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 10 (/proc/2340/mounts) leaked on lvs invocation. Parent PID 4686: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 29nov2014, trusty, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sda5:Ubuntu 14.04.1 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="A88C66BB8C6683A2" TYPE="ntfs"
/dev/sda5: UUID="5504b4a2-bcee-4162-9edb-9d443d4193f8" TYPE="ext4"
/dev/sda7: UUID="a2d7f297-9889-440a-987a-92bb16e0a367" TYPE="ext4"
/dev/sr0: LABEL="Boot-Repair-Disk 32bit" TYPE="iso9660"
/dev/zram0: UUID="73bd653f-2eb3-4000-a60d-81776200e42a" TYPE="swap"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 23  2014 grub.d
total 76
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== sda5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
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
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sda7    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA SAMSUNG HM160HC (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      32.3kB  21.0GB  21.0GB  primary   ntfs         boot
2      21.0GB  160GB   139GB   extended
5      21.0GB  43.3GB  22.3GB  logical   ext4
7      43.3GB  159GB   116GB   logical   ext4
6      159GB   160GB   1005MB  logical



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:160GB:scsi:512:512:msdos:ATA SAMSUNG HM160HC;
1:32.3kB:21.0GB:21.0GB:ntfs::boot;
2:21.0GB:160GB:139GB:::;
5:21.0GB:43.3GB:22.3GB:ext4::;
7:43.3GB:159GB:116GB:ext4::;
6:159GB:160GB:1005MB:::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu_dma_latency cuse disk ecryptfs fd fd0 full fuse fw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  36 16 71 02 00 00 00 00  |........6.q.....|
00000030  00 00 0c 00 00 00 00 00  63 11 27 00 00 00 00 00  |........c.'.....|
00000040  f6 00 00 00 01 00 00 00  a2 83 66 8c bb 66 8c a8  |..........f..f..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 46 65 68  6c 65 72 20 62 65 69 6d  |.....Fehler beim|
00000190  20 4c 65 73 65 6e 20 64  65 73 20 44 61 74 65 6e  | Lesen des Daten|
000001a0  74 72 84 67 65 72 73 00  0d 0a 4e 54 4c 44 52 20  |tr.gers...NTLDR |
000001b0  66 65 68 6c 74 00 0d 0a  4e 54 4c 44 52 20 69 73  |fehlt...NTLDR is|
000001c0  74 20 6b 6f 6d 70 72 69  6d 69 65 72 74 00 0d 0a  |t komprimiert...|
000001d0  4e 65 75 73 74 61 72 74  20 6d 69 74 20 53 74 72  |Neustart mit Str|
000001e0  67 2b 41 6c 74 2b 45 6e  74 66 0d 0a 00 00 00 00  |g+Alt+Entf......|
000001f0  00 00 00 00 00 00 00 00  83 a8 b6 ce 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  470M  5.0M  465M   2% /
udev           devtmpfs   456M   12K  456M   1% /dev
tmpfs          tmpfs       94M  984K   93M   2% /run
/dev/sr0       iso9660    599M  599M     0 100% /cdrom
/dev/loop0     squashfs   543M  543M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      470M  8.0K  470M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      470M     0  470M   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk     20G  2.5G   18G  13% /mnt/boot-sav/sda1
/dev/sda5      ext4        21G  3.3G   17G  17% /mnt/boot-sav/sda5
/dev/sda7      ext4       107G   60M  101G   1% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba34b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS/exFAT
/dev/sda2        40966142   312580095   135806977    5  Extended
/dev/sda5        40966144    84494335    21764096   83  Linux
/dev/sda6       310618112   312580095      980992   82  Linux swap / Solaris
/dev/sda7        84496384   310616063   113059840   83  Linux

Partition table entries are not in disk order



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sda5 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325]
Subsystem: ASUSTeK Computer Inc. Device [1043:1612]
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1,grub-install (GRUB) 2.

Reinstall the GRUB of sda5 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda5 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by mörgæs on 2015-01-25
Hi, welcome to the fora.
Please use CODE tags. I have edited your post.

This is very old hardware. Are you able to run X/Lubuntu 14.04.1 in a live boot?

---

### Post by st_le on 2015-01-25
Booting from the xubuntu live dvd 14.04 LTS works well. The problem is just booting from the hard drive.

---

### Post by mörgæs on 2015-01-25
So far, so good.
In a live boot please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by st_le on 2015-01-25
This is the lshw output.
I just realized, that actually, the laptop has an integrated cd player which may be booted separately by a special switch. This boot option still works. Maybe this is the source of the problems?
```

computer
    description: Tower Computer
    product: L3000D
    vendor: ASUSTEK
    version: 1.0
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower uuid=[REMOVED]
  *-core
       description: Motherboard
       product: L3000D_L
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: V2.00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: 0115a
          date: 02/10/2004
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb
     *-cpu
          description: CPU
          product: mobile AMD Athlon(tm) XP-M 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: SOCKET A
          size: 1874MHz
          capacity: 1874MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 740 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:e7800000-e7ffffff memory:f0000000-febfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:f0000000-f7ffffff memory:e7800000-e781ffff ioport:d800(size=128)
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e800(size=32)
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_sis latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:b800(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=32 maxlatency=11 mingnt=52
             resources: ioport:b400(size=256) ioport:b000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=32 maxlatency=11 mingnt=52
             resources: irq:11 ioport:a800(size=256) ioport:a400(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:9 memory:e7000000-e7000fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:9 memory:e6800000-e6800fff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:9 memory:e6000000-e6000fff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32 maxlatency=80
             resources: irq:9 memory:e5800000-e5800fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
             resources: irq:11 ioport:a000(size=256) memory:e5000000-e5000fff memory:4c000000-4c01ffff
        *-pcmcia:0
             description: CardBus bridge
             product: RL5c476 II
             vendor: Ricoh Co Ltd
             physical id: a
             bus info: pci@0000:00:0a.0
             version: aa
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
             resources: iomemory:b00502000-b00501fff irq:5 memory:e4800000-e4800fff ioport:1000(size=256) ioport:1400(size=256) memory:3c000000-3fffffff memory:40000000-43ffffff
        *-pcmcia:1
             description: CardBus bridge
             product: RL5c476 II
             vendor: Ricoh Co Ltd
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: aa
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
             resources: iomemory:b00906000-b00905fff irq:11 memory:e2800000-e2800fff ioport:1800(size=256) ioport:1c00(size=256) memory:44000000-47ffffff memory:48000000-4bffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C552 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: a.2
             bus info: pci@0000:00:0a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:11 memory:e0800000-e08007ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HM160HC
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: LQ10
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ba34b
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-01-21 19:21:02 filesystem=ntfs state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 129GiB
                capacity: 129GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 20GiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 958MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 107GiB
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM SD-R2312
             vendor: TOSHIBA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             logical name: /cdrom
             version: 1708
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=7d2105db state=mounted
              *-volume UNCLAIMED
                   description: Hidden HPFS/NTFS partition
                   physical id: 1
                   capacity: 915MiB
                   capabilities: primary bootable hidden


```

---

### Post by mörgæs on 2015-01-25
I don't know with the CD drive but under all circumstances I would reinstall Lubuntu 14.04.1 and not Xubuntu. 

This is indeed old stuff so I recommend that you read the link in my signature, especially the part about SSE2.

Your install of XP is new. Are you aware that there is no support for this system so security bugs are left unfixed?

---

### Post by oldfred on 2015-01-25
You say you can boot with recovery mode?
That uses nomodeset to use a default video mode.

Not familiar with the old SIS video. But SIS was one of the many video drivers shown in list from Ubuntu.

Edit - Thread on SIS video
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by st_le on 2015-01-25
Now I'm completely lost: The computer doesn't boot with an Lubuntu Live CD (which works for another computer). After completely formatting the hard drive (and only after that) I was able to reinstall xp which boots well now. I just did this to get rid of the grub entry in the MBR, probably not very elegant... But still, Lubuntu Live CD doesn't boot (whereas Xubuntu live DVD boots).

---

### Post by st_le on 2015-01-25
Oldfred, the problem is that I can't boot from hard disk at all (apart from fresh xp installations which I want to get rid of). Xubuntu boots from live DVD, works well and reports no errors at all afterwards, whereas Lubuntu doesn't boot from live CD.

---

### Post by oldfred on 2015-01-25
So was the lshw from Xubuntu live installer or from the install now erased?

If you boot Xubuntu, does this show on configuration line the driver in use?

 sudo lshw -c display

This was about 10 lines down on mine and shows I am using the i915 driver.
configuration: driver=i915 latency=0

---

### Post by st_le on 2015-01-26
since I can't boot at all from hard drive (only if I install xp as a single os), the lshw output was from the xubuntu live dvd boot while xubuntu was actually still installed on hard drive.  Now, after formatting the hard drive, installing xp and running xubuntu live dvd I get the following lshw output (line 10): configuration: latency=0  Do you think that non-booting from hard drive results from a display problem?

---

### Post by oldfred on 2015-01-26
That is just saying you have no video driver configured.
But live installer uses a lot of defaults and does not have any proprietary video drivers.

From hard drive can you boot second line in grub menu or recovery mode?
If not seen as dual boot, you may need to hold shift key from BIOS to get to grub menu.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

