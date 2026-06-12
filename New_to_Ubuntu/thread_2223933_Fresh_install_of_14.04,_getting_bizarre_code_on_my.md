---
title: "Fresh install of 14.04, getting bizarre code on my screen"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by jmeeter on 2014-05-13
I had Fedora 20 installed on my laptop, but last night I used Unetbootin to make a bootable Ubuntu USB stick. Installed Ubuntu 14.04, everything went fine, but when I restarted the laptop I got a black screen with a purple border. When I restarted the computer again, I got this screen:

[[IMG]http://i.imgur.com/DdlYRv3l.jpg[/IMG]](http://imgur.com/DdlYRv3)

I decided to try to install Xubuntu, and when I tried to boot from the USB it took me to GRUB, and when I attempted to boot up Ubuntu I got the above screen again.

---

### Post by lykwydchykyn on 2014-05-13
Basically, GRUB is miconfigured and trying to boot to a partition that doesn't exist.  Probably something failed to update when you reinstalled.  The first thing I'd try is booting back to your Ubuntu live media and try to reinstall grub.

---

### Post by squakie on 2014-05-13
Boot-repair *might* be able to fix this also.

---

### Post by squakie on 2014-05-13
If you can boot a live media, I think you might be able to run update-grub and straighten that out as well.

---

### Post by jmeeter on 2014-05-14
Ok, I'll try that right now. Wouldn't that just update GRUB on the USB stick and not the hard drive though?

---

### Post by jmeeter on 2014-05-14
Alright, I followed [this guide]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") on how to repair GRUB2. Restarted, and am still getting same error ("Gave up waiting for root device"). Also it said something about the hard drive not existing??

---

### Post by jmeeter on 2014-05-14
Ran boot-repair and it failed. Here are the Pastebin results:

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 0x4d8ae235
    Boot sector info:  Syslinux looks at sector 2084666 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   617,582,591   617,580,544  83 Linux
/dev/sda2         617,584,638   625,141,759     7,557,122   5 Extended
/dev/sda5         617,584,640   625,141,759     7,557,120  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 62.7 GB, 62746787840 bytes
255 heads, 63 sectors/track, 7628 cylinders, total 122552320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              2   122,552,319   122,552,318   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        24f15c0b-292f-42fc-83ff-7bcede64250d   ext4       
/dev/sda5        bf23c8fb-fa98-4fa8-97ee-7a2add4f9bc3   swsuspend  
/dev/sdb1        E413-1104                              vfat       UNTITLED

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  24f15c0b-292f-42fc-83ff-7bcede64250d
else
  search --no-floppy --fs-uuid --set=root 24f15c0b-292f-42fc-83ff-7bcede64250d
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-24f15c0b-292f-42fc-83ff-7bcede64250d' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  24f15c0b-292f-42fc-83ff-7bcede64250d
    else
      search --no-floppy --fs-uuid --set=root 24f15c0b-292f-42fc-83ff-7bcede64250d
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=24f15c0b-292f-42fc-83ff-7bcede64250d ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-24f15c0b-292f-42fc-83ff-7bcede64250d' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-24f15c0b-292f-42fc-83ff-7bcede64250d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  24f15c0b-292f-42fc-83ff-7bcede64250d
        else
          search --no-floppy --fs-uuid --set=root 24f15c0b-292f-42fc-83ff-7bcede64250d
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=24f15c0b-292f-42fc-83ff-7bcede64250d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-24f15c0b-292f-42fc-83ff-7bcede64250d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  24f15c0b-292f-42fc-83ff-7bcede64250d
        else
          search --no-floppy --fs-uuid --set=root 24f15c0b-292f-42fc-83ff-7bcede64250d
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=24f15c0b-292f-42fc-83ff-7bcede64250d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  24f15c0b-292f-42fc-83ff-7bcede64250d
    else
      search --no-floppy --fs-uuid --set=root 24f15c0b-292f-42fc-83ff-7bcede64250d
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  24f15c0b-292f-42fc-83ff-7bcede64250d
    else
      search --no-floppy --fs-uuid --set=root 24f15c0b-292f-42fc-83ff-7bcede64250d
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=24f15c0b-292f-42fc-83ff-7bcede64250d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bf23c8fb-fa98-4fa8-97ee-7a2add4f9bc3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-hlFsMciv/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-hlFsMciv/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-hlFsMciv/Tmp_Log: No such file or directory
File descriptor 9 (/proc/4736/mounts) leaked on lvscan invocation. Parent PID 13178: bash
File descriptor 63 (pipe:[62126]) leaked on lvscan invocation. Parent PID 13178: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-05-14__16h12 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/casper/vmlinuz.efi
mount: unknown filesystem type 'swsuspend'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'swsuspend'
mount -r /dev/sda5 : Error code 32

=================== os-prober:
/dev/sda1:Ubuntu 14.04 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="24f15c0b-292f-42fc-83ff-7bcede64250d" TYPE="ext4"
/dev/sda5: UUID="bf23c8fb-fa98-4fa8-97ee-7a2add4f9bc3" TYPE="swsuspend"
/dev/sdb1: LABEL="UNTITLED" UUID="E413-1104" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: unknown filesystem type 'swsuspend'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'swsuspend'
mount -r /dev/sda5 : Error code 32
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 17 01:26 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11 10:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 10:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:51 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 12:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 10:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 10:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:51 41_custom
-rw-r--r-- 1 root root   483 Apr 11 10:51 README




=================== sda1/etc/default/grub :

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




=================== sda1recordfail=1/grub/grubenv :
recordfail=1



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST320LT020-9YG14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
1      1049kB  316GB  316GB   primary   ext4         boot
2      316GB   320GB  3869MB  extended
5      316GB   320GB  3869MB  logical   swsusp


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 62.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      1024B  62.7GB  62.7GB  primary  fat32        boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:4096:msdos:ATA ST320LT020-9YG14;
1:1049kB:316GB:316GB:ext4::boot;
2:316GB:320GB:3869MB:::;
5:316GB:320GB:3869MB:swsusp::;

BYT;
/dev/sdb:62.7GB:scsi:512:512:msdos:Lexar USB Flash Drive;
1:1024B:62.7GB:62.7GB:fat32::boot;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhost-net video0 watchdog zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.8G  108M  1.7G   7% /
udev           devtmpfs   1.8G   12K  1.8G   1% /dev
tmpfs          tmpfs      356M  1.1M  355M   1% /run
/dev/sdb1      vfat        59G 1004M   58G   2% /cdrom
/dev/loop0     squashfs   923M  923M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.8G  1.2M  1.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.8G   80K  1.8G   1% /run/shm
none           tmpfs      100M   68K  100M   1% /run/user
/dev/sda1      ext4       290G  3.5G  272G   2% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d410b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   617582591   308790272   83  Linux
/dev/sda2       617584638   625141759     3778561    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       617584640   625141759     3778560   82  Linux swap / Solaris

Disk /dev/sdb: 62.7 GB, 62746787840 bytes
255 heads, 63 sectors/track, 7628 cylinders, total 122552320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2   122552319    61276159    b  W95 FAT32



=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda1 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

fsck -fyM /dev/sda1
fsck from util-linux 2.20.1

fsck -fyM /dev/sda5
fsck from util-linux 2.20.1
fsck: fsck.swsuspend: not found
fsck: error 2 while executing fsck.swsuspend for /dev/sda5
mount: unknown filesystem type 'swsuspend'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'swsuspend'
mount -r /dev/sda5 : Error code 32
Unhide GRUB boot menu in sda1/etc/default/grub

*******lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] [1002:9806]
Subsystem: Hewlett-Packard Company Device [103c:3577]
Kernel driver in use: radeon
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
*******

grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
,.

Reinstall the GRUB of sda1 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda1 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
mount: unknown filesystem type 'swsuspend'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'swsuspend'
mount -r /dev/sda5 : Error code 32
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by simplychrislike on 2014-05-14
If you don't mind to make a new installation, then delete all partitions from your hdd first before starting the installation.
That was the way I had to go some installations before.

---

### Post by jmeeter on 2014-05-14
Ok, I kind of inadvertently fixed it... Just for kicks I dual booted Ubuntu 14.04 alongside the existing "broken" installation of 14.04. The new partition ran just fine. Using that new partition I deleted the old partition using gparted. After that I ran the Ubuntu installation, erased everything, and did a clean install. Now it's working. :p

---

