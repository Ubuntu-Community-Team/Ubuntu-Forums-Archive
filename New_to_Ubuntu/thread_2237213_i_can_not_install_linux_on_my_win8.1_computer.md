---
title: "i can not install linux on my win8.1 computer"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by bluebird2 on 2014-07-31
Hello i am trying install ubuntu on my computer i do all of them:[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) . i have a few problem. ubuntu's install completed and then  when my computer restarted, installing start again and again. i ejected dvd and show this :

[ATTACH=CONFIG]255175[/ATTACH]

and when i use tool manager on try mode it give me an error. this:
```

[quote author=bluesky link=topic=44426.msg517215#msg517215 date=1406761630]
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector
    1100808192 of the same hard drive for core.img. core.img is at this
    location and looks in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:       

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi
                       /EFI/Microsoft/Boot/bootmgr.efi
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts
                       at sector 591624192. But according to the info from
                       fdisk, sda6 starts at sector 1920006145.
    Operating System: 
    Boot files:       

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  According to the info in the boot sector, sda7 starts
                       at sector 623044608. But according to the info from
                       fdisk, sda7 starts at sector 1951426561.
    Operating System: 
    Boot files:        /EFI/Asclepius/bootx64.efi
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:
    Operating System: 
    Boot files:        /grub/grub.cfg

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System: 
    Boot files:       

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 15416 of /dev/sdb for its
                       second stage. SYSLINUX is installed in the /uui
                       directory. No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,023,999     1,021,952 Windows Recovery Environment (Windows)
/dev/sda2       1,024,000     1,638,399       614,400 EFI System partition
/dev/sda3       1,638,400     1,900,543       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,900,544 1,100,806,144 1,098,905,601 Data partition (Windows/Linux)
/dev/sda5   1,100,808,192 1,100,810,239         2,048 BIOS Boot partition
/dev/sda6   1,920,006,145 1,951,426,560    31,420,416 Windows Recovery Environment (Windows)
/dev/sda7   1,951,426,561 1,953,523,712     2,097,152 Windows Recovery Environment (Windows)
/dev/sda8   1,100,810,240 1,109,403,647     8,593,408 Data partition (Linux)
/dev/sda9   1,109,403,648 1,109,891,071       487,424 Data partition (Linux)
/dev/sda10  1,109,891,072 1,125,892,095    16,001,024 Swap partition (Linux)
/dev/sda11  1,125,892,096 1,920,006,143   794,114,048 Data partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3ECEA9DBCEA98C29                       ntfs       Windows RE tools
/dev/sda10       7b359ffa-79c3-4af6-bd55-462ab4e3b8c1   swap       
/dev/sda11       1aaa1f1d-4788-42e4-8417-b1c8933755a6   ext4       
/dev/sda2        82AC-8B5C                              vfat       SYSTEM
/dev/sda4        FEB015F6B015B5DD                       ntfs       
/dev/sda6        B0EC4B8BEC4B4B34                       ntfs       SAMSUNG_REC2
/dev/sda7        D4B1-95DD                              vfat       SAMSUNG_REC
/dev/sda8        6ddfe2f6-ad43-4964-82b6-7033a16569fa   ext4       
/dev/sda9        e11d5abc-aa8c-4dfb-90fe-74d1d70c4191   ext2       
/dev/sdb         1CE7-345E                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=6ddfe2f6-ad43-4964-82b6-7033a16569fa /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda9 during installation
#UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191 /boot           ext2    defaults        0       2
# /home was on /dev/sda11 during installation
UUID=1aaa1f1d-4788-42e4-8417-b1c8933755a6 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=7b359ffa-79c3-4af6-bd55-462ab4e3b8c1 none            swap    sw              0       0
UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191    /boot    ext2    defaults    0    2
UUID=82AC-8B5C    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

============================= sda9/grub/grub.cfg: ==============================

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
set root='hd0,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  6ddfe2f6-ad43-4964-82b6-7033a16569fa
else
  search --no-floppy --fs-uuid --set=root 6ddfe2f6-ad43-4964-82b6-7033a16569fa
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6ddfe2f6-ad43-4964-82b6-7033a16569fa' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
    else
      search --no-floppy --fs-uuid --set=root e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
    fi
    linux    /vmlinuz-3.13.0-32-generic root=UUID=6ddfe2f6-ad43-4964-82b6-7033a16569fa ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-6ddfe2f6-ad43-4964-82b6-7033a16569fa' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-6ddfe2f6-ad43-4964-82b6-7033a16569fa' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
        else
          search --no-floppy --fs-uuid --set=root e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /vmlinuz-3.13.0-32-generic root=UUID=6ddfe2f6-ad43-4964-82b6-7033a16569fa ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-6ddfe2f6-ad43-4964-82b6-7033a16569fa' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
        else
          search --no-floppy --fs-uuid --set=root e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /vmlinuz-3.13.0-32-generic root=UUID=6ddfe2f6-ad43-4964-82b6-7033a16569fa ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 82AC-8B5C
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 82AC-8B5C
chainloader (${root})/EFI/Boot/bootx64.efi
}

menuentry "efi/EFI/Boot/bootx64.efi" {
search --fs-uuid --no-floppy --set=root e11d5abc-aa8c-4dfb-90fe-74d1d70c4191
chainloader (${root})/efi/EFI/Boot/bootx64.efi
}

menuentry "EFI/Asclepius/bootx64.efi" {
search --fs-uuid --no-floppy --set=root D4B1-95DD
chainloader (${root})/EFI/Asclepius/bootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-82AC-8B5C' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  82AC-8B5C
    else
      search --no-floppy --fs-uuid --set=root 82AC-8B5C
    fi
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

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdb/boot/grub/grub.cfg: ============================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

==================== sdb: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdc

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: /tmp/BootInfo-TblRuYaw/Tmp_Log: No such file or directory
File descriptor 9 (/proc/9088/mounts) leaked on lvscan invocation. Parent PID 5646: bash
File descriptor 63 (pipe:[103518]) leaked on lvscan invocation. Parent PID 5646: bash
  No volume groups found
cat: /tmp/BootInfo-TblRuYaw/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-07-30__23h10 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04.1 LTS, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Windows 8 (loader):Windows:chain
/dev/sda7:Windows Recovery Environment (loader):Windows1:chain
/dev/sda8:Ubuntu 14.04.1 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/sda1: LABEL="Windows RE tools" UUID="3ECEA9DBCEA98C29" TYPE="ntfs"
/dev/sda11: UUID="1aaa1f1d-4788-42e4-8417-b1c8933755a6" TYPE="ext4"
/dev/sda2: LABEL="SYSTEM" UUID="82AC-8B5C" TYPE="vfat"
/dev/sda4: UUID="FEB015F6B015B5DD" TYPE="ntfs"
/dev/sda6: LABEL="SAMSUNG_REC2" UUID="B0EC4B8BEC4B4B34" TYPE="ntfs"
/dev/sda7: LABEL="SAMSUNG_REC" UUID="D4B1-95DD" TYPE="vfat"
/dev/sda8: UUID="6ddfe2f6-ad43-4964-82b6-7033a16569fa" TYPE="ext4"
/dev/sda9: UUID="e11d5abc-aa8c-4dfb-90fe-74d1d70c4191" TYPE="ext2"
/dev/loop0: TYPE="squashfs"
/dev/sda10: UUID="7b359ffa-79c3-4af6-bd55-462ab4e3b8c1" TYPE="swap"
/dev/sdb: LABEL="UUI" UUID="1CE7-345E" TYPE="vfat"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi

=================== sda8/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 30 23:08 grub.d
drwxr-xr-x  2 root root    4096 Jul 30 23:04 grub.d.bak
total 76
-rwxr-xr-x 1 root root  9424 May 15 19:02 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:02 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:02 20_linux_xen
-rwxr-xr-x 1 root root   618 Jul 30 23:08 25_custom
-rwxr-xr-x 1 root root 11692 May 15 19:02 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:02 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:02 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:02 41_custom
-rw-r--r-- 1 root root   483 May 15 19:02 README




=================== sda8/etc/default/grub :

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



/boot/efi detected in the fstab of sda8: UUID=82AC-8B5C    (sda2)
/boot detected in the fstab of sda8: UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191    (sda9)
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda11    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda11.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
sda8    : sda,    not-sepboot,    no-grubenv    grub2,    signed grub-efi ,    update-grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda8.
sda9    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda9.

sda    : GPT,    BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  524MB   523MB   ntfs            Basic data partition          hidden, diag
2      524MB   839MB   315MB   fat32           EFI system partition          boot
3      839MB   973MB   134MB                   Microsoft reserved partition  msftres
4      973MB   564GB   563GB   ntfs            Basic data partition          msftdata
5      564GB   564GB   1049kB                                                bios_grub
8      564GB   568GB   4400MB  ext4
9      568GB   568GB   250MB   ext2
10      568GB   576GB   8193MB  linux-swap(v1)
11      576GB   983GB   407GB   ext4
6      983GB   999GB   16.1GB  ntfs            Basic data partition          hidden, diag
7      999GB   1000GB  1074MB  fat32           Basic data partition          hidden, diag


Model: Lenovo Memory Key 2GB (scsi)
Disk /dev/sdb: 2022MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  2022MB  2022MB  fat32

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM024 HN-M;
1:1049kB:524MB:523MB:ntfs:Basic data partition:hidden, diag;
2:524MB:839MB:315MB:fat32:EFI system partition:boot;
3:839MB:973MB:134MB::Microsoft reserved partition:msftres;
4:973MB:564GB:563GB:ntfs:Basic data partition:msftdata;
5:564GB:564GB:1049kB:::bios_grub;
8:564GB:568GB:4400MB:ext4::;
9:568GB:568GB:250MB:ext2::;
10:568GB:576GB:8193MB:linux-swap(v1)::;
11:576GB:983GB:407GB:ext4::;
6:983GB:999GB:16.1GB:ntfs:Basic data partition:hidden, diag;
7:999GB:1000GB:1074MB:fat32:Basic data partition:hidden, diag;

BYT;
/dev/sdb:2022MB:scsi:512:512:loop:Lenovo Memory Key 2GB;
1:0.00B:2022MB:2022MB:fat32::;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
tmpfs on /var/lib/polkit-1/localauthority/90-mandatory.d type tmpfs (rw)
gvfsd-fuse on /home/ubuntu/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda11 on /mnt/boot-sav/sda11 type ext4 (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type vfat (rw)
/dev/sda8 on /mnt/boot-sav/sda8 type ext4 (rw)
/dev/sda9 on /mnt/boot-sav/sda9 type ext2 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda10 sda11 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 rts51x0 sda sda1 sda10 sda11 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 97 0f 00 00 00 00 00  |................|
00000030  55 a6 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  29 8c a9 ce db a9 ce 3e  |........)......>|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 a0 0f 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 5c 8b ac 82 4e  4f 20 4e 41 4d 45 20 20  |..)...NO NAME  |
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

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 1d 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  00 f8 7f 41 00 00 00 00  |...........A....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  dd b5 15 b0 f6 15 b0 fe  |................|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 78 43 23  |........?....xC#|
00000020  00 00 00 00 80 00 80 00  ff 6f df 01 00 00 00 00  |.........o......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  34 4b 4b ec 8b 4b ec b0  |........4KK..K..|
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
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda7
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 0e 10  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 e8 22 25  |........?....."%|
00000020  00 00 20 00 f9 07 00 00  00 00 00 00 02 00 00 00  |.. .............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 dd 95 b1 d4 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
ls /mnt/boot-sav/sda9/1:
ls /mnt/boot-sav/sda9: abi-3.13.0-32-generic
config-3.13.0-32-generic
efi
grub
grub.bak
initrd.img-3.13.0-32-generic
lost+found
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-3.13.0-32-generic
vmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-32-generic.efi.signed  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  137M  3.8G   4% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      791M  1.3M  789M   1% /run
/dev/sdb       vfat       1.9G  980M  941M  52% /cdrom
/dev/loop0     squashfs   939M  939M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  1.9M  3.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      3.9G   80K  3.9G   1% /run/shm
none           tmpfs      100M   56K  100M   1% /run/user
tmpfs          tmpfs      3.9G  4.0K  3.9G   1% /var/lib/polkit-1/localauthority/90-mandatory.d
/dev/sda1      fuseblk    499M  242M  258M  49% /mnt/boot-sav/sda1
/dev/sda11     ext4       373G   67M  354G   1% /mnt/boot-sav/sda11
/dev/sda2      vfat       296M   44M  253M  15% /mnt/boot-sav/sda2
/dev/sda4      fuseblk    524G   33G  492G   7% /mnt/boot-sav/sda4
/dev/sda6      fuseblk     15G   15G  304M  99% /mnt/boot-sav/sda6
/dev/sda7      vfat      1020M  672M  349M  66% /mnt/boot-sav/sda7
/dev/sda8      ext4       4.0G  3.5G  279M  93% /mnt/boot-sav/sda8
/dev/sda9      ext2       231M   44M  176M  20% /mnt/boot-sav/sda9

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x213e79e3

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order


EFI detected. Please check the options.
/boot detected. Please check the options.
=================== Advices
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?

=================== Recommended repair
Recommended-Repair
This setting will purge (in order to sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sda8, using the following options: upgrade-grub       sda9/boot, sda2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot backup-and-rename-efi-files


Quantity of real Windows: 1
Mount sda9 on /mnt/boot-sav/sda8/boot
Mount sda2 on /mnt/boot-sav/sda8/boot/efi
ls /mnt/boot-sav/sda8/boot/efi/1:
ls /mnt/boot-sav/sda8/boot/efi: Boot
bootmgr
BOOTNXT
EFI  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
No sda8/boot/efi/efi/ ubuntu/mint folder
chroot /mnt/boot-sav/sda8 apt-get -y --force-yes update
Purge the GRUB of sda8
Install last GRUB version in /mnt/boot-sav/sda8/etc/apt/sources.list
chroot /mnt/boot-sav/sda8 apt-get -y --force-yes update
grub-efi-amd64-signed available

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 12 not upgraded.
DEBCHECK debOK, grub-efi-amd64-signed
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo chroot "/mnt/boot-sav/sda8" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda8" apt-get install -fynsudo chroot "/mnt/boot-sav/sda8" apt-get purge -y --force-yes grub* shim-signed linux-signed*
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Boot/bootx64.efi

=================== sda8/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 30 23:08 grub.d
drwxr-xr-x  2 root root    4096 Jul 30 23:04 grub.d.bak
total 76
-rwxr-xr-x 1 root root  9424 May 15 19:02 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:02 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:02 20_linux_xen
-rwxr-xr-x 1 root root   618 Jul 30 23:08 25_custom
-rwxr-xr-x 1 root root 11692 May 15 19:02 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:02 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:02 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:02 41_custom
-rw-r--r-- 1 root root   483 May 15 19:02 README




=================== sda8/etc/default/grub :

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



/boot/efi detected in the fstab of sda8: UUID=82AC-8B5C    (sda2)
/boot detected in the fstab of sda8: UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191    (sda9)
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Boot/bootx64.efi

=================== sda8/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 30 23:08 grub.d
drwxr-xr-x  2 root root    4096 Jul 30 23:04 grub.d.bak
total 76
-rwxr-xr-x 1 root root  9424 May 15 19:02 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:02 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:02 20_linux_xen
-rwxr-xr-x 1 root root   618 Jul 30 23:08 25_custom
-rwxr-xr-x 1 root root 11692 May 15 19:02 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:02 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:02 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:02 41_custom
-rw-r--r-- 1 root root   483 May 15 19:02 README


/boot/efi detected in the fstab of sda8: UUID=82AC-8B5C    (sda2)
/boot detected in the fstab of sda8: UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191    (sda9)
shim-signed available
linux-signed-generic available
Then type: sudo chroot "/mnt/boot-sav/sda8" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Boot/bootx64.efi

=================== sda8/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 30 23:13 grub.d
drwxr-xr-x  2 root root    4096 Jul 30 23:04 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 May 15 19:02 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:02 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:02 20_linux_xen
-rwxr-xr-x 1 root root 11692 May 15 19:02 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:02 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:02 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:02 41_custom
-rw-r--r-- 1 root root   483 May 15 19:02 README




=================== sda8/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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



/boot/efi detected in the fstab of sda8: UUID=82AC-8B5C    (sda2)
/boot detected in the fstab of sda8: UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191    (sda9)
Unhide GRUB boot menu in sda8/etc/default/grub
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda8/boot/efi/EFI/Boot/bootx64.efi

=================== sda8/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 30 23:13 grub.d
drwxr-xr-x  2 root root    4096 Jul 30 23:04 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 May 15 19:02 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:02 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:02 20_linux_xen
-rwxr-xr-x 1 root root 11692 May 15 19:02 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:02 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:02 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:02 41_custom
-rw-r--r-- 1 root root   483 May 15 19:02 README




=================== sda8/etc/default/grub :

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



/boot/efi detected in the fstab of sda8: UUID=82AC-8B5C    (sda2)
/boot detected in the fstab of sda8: UUID=e11d5abc-aa8c-4dfb-90fe-74d1d70c4191    (sda9)

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
Subsystem: Samsung Electronics Co Ltd Device [144d:c737]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
*******

grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
,.
GRUB too old for SecureBoot. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

chroot /mnt/boot-sav/sda8 efibootmgr -v
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

chroot /mnt/boot-sav/sda8 uname -r
Kernel: 3.13.0-32-generic
WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

Reinstall the grub-efi of sda8
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
grub-install : exit code of grub-install :1
Error: no grub*.efi generated. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Add /mnt/boot-sav/sda8/boot/efi efi entries in /mnt/boot-sav/sda8/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda8/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda8/boot/efi/EFI/Boot/bootx64.efi
sda2/bootx64.efi already added
sda2/bootmgfw.efi already added
Add /mnt/boot-sav/sda8/boot efi entries in /mnt/boot-sav/sda8/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda8/boot/efi/EFI/Boot/bootx64.efi
Add /mnt/boot-sav/sda7 efi entries in /mnt/boot-sav/sda8/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda7/EFI/Asclepius/bootx64.efi

---- Grub-install verbose
+ è\C1\FF\D9k\A4\90\86\A8!%hhX\80\80 \C1\80 0I
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: cannot create n\F0\F0TT@T@DDP\E5td\CC\D2\CC\D2L\CC\D2Ll9l9Q\E5tdR\E5td\F0=\F0=n\F0=n/lib64/ld-linux-x86-64.so.2GNUGNU\D6dj?\92\B0\9E: Directory nonexistent
+ ELF @@@@@@\F8\F888@8@@@\A4:\A4: \F0=\F0=n\F0=n\9E{ \81 
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: ELF: not found
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: è\C1\FF\D9k\A4\90\86\A8!%hhX\80\80: not found
/usr/sbin/grub-install: 2: /usr/sbin/grub-install: Syntax error: word unexpected (expecting ")")
--------
/usr/sbin/grub-install : exit code of grub-install :2
---- End of grub-install verbose


chroot /mnt/boot-sav/sda8 efibootmgr -v
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

chroot /mnt/boot-sav/sda8 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Windows 8 (loader) on /dev/sda2

An error occurred during the repair.

You can now reboot your computer.


You may want to retry after deactivating the [Backup and rename Windows EFI files] option.

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
[/QUOTE]
```


and my bios:




[ATTACH=CONFIG]255176[/ATTACH]

[ATTACH=CONFIG]255177[/ATTACH]

[ATTACH=CONFIG]255178[/ATTACH]

so thank you and i am sorry for my english i am bad at english again again thank you.

---

### Post by yancek on 2014-07-31
Did you change the boot priority in the BIOS from the DVD to the hard drive?

---

### Post by whitesmith on 2014-07-31
Also get rid of Secure Boot if it's on.

---

### Post by edeneen on 2014-07-31
have you tried setting boot mode to Legacy ?

---

### Post by Mark Phelps on 2014-07-31
> **whitesmith said:**
> Also get rid of Secure Boot if it's on.

It's already shown as OFF in the first screen shot.

---

### Post by QIII on 2014-07-31
bluebird2,

Please use code tags instead of quote tags to enclose long text.  It makes things much easier to read.

Also, rather than cutting and pasting large images, please use the attachment feature (the paper clip above the text entry box) to insert images.  Some people with slow connections or data limitations are inconvenienced or may even be charged for data transfer when large images are pasted.

Thanks.

---

### Post by oldfred on 2014-07-31
You show Ubuntu installed in CSM/BIOS/Legacy mode and Windows in UEFI mode.
You have to have CSM on to boot Ubuntu and UEFI on to boot Windows.
Better to have Ubuntu also in UEFI boot mode. How you boot installer is how it installs, but Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc(BIOS) and installing the correct verion of grub-efi(UEFI).

Also generally better for desktops to not have a separate /boot partition. You have to regularly maintain by removing old kernels (which you should do anyway). But with a separate /boot it fills up and then can be very difficult to houseclean if you cannot boot. 

Also do not reinstall Ubuntu except by using Something Else, it may erase entire system. See caution in link in my signature.

And Make sure you have full backups of Windows, the efi partition and recovery partitions.

Some other Samsungs with installs:
 Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

