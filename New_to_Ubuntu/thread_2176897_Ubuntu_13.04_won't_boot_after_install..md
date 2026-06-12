---
title: "Ubuntu 13.04 won't boot after install."
date: 2013-09-26
forum: New to Ubuntu
---

### Post by matthew18 on 2013-09-26
I'm currently running Windows 7 but I installed Ubuntu 13.04 as a dual-boot onto an external hard drive. The install process went fine but it refuses to boot and I'm not sure what to do. I ran the Boot Info Script and the Grub fix and here are the results:

Grub fix log: [http://paste.ubuntu.com/6159410/](http://paste.ubuntu.com/6159410/)

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdg: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 15254 of /dev/sdg for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    20,803,583    20,721,664   7 NTFS / exFAT / HPFS
/dev/sda3          20,803,584   976,769,023   955,965,440   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 2,063,824,895 2,063,822,848   7 NTFS / exFAT / HPFS
/dev/sdb2       2,063,824,896 3,846,404,095 1,782,579,200   7 NTFS / exFAT / HPFS
/dev/sdb3       3,846,406,142 3,907,022,847    60,616,706   5 Extended
/dev/sdb5       3,894,724,608 3,907,022,847    12,298,240  82 Linux swap / Solaris
/dev/sdb6       3,846,406,144 3,894,724,607    48,318,464  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        DEB65C55B65C2FEF                       ntfs       RECOVERY
/dev/sda3        BE2AC82A2AC7DE11                       ntfs       Dat, Dat, Dat, Hard Drive
/dev/sdb1        A4C45E13C45DE856                       ntfs       Space For Days Yo
/dev/sdb2        D6064B6B064B4BA5                       ntfs       Linux Storage
/dev/sdb5        041b44e8-ccef-4386-88b4-c5900e158fcd   swap       
/dev/sdb6        602f25c6-ebae-45f2-8685-c8f466fe5119   ext4       
/dev/sdg         10E0-2C2E                              vfat       MULTIBOOT
/dev/sr1                                                iso9660    U3 System

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/this/Space For Days Yo fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/this/Linux Storage fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6        /media/this/602f25c6-ebae-45f2-8685-c8f466fe5119 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdg         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
else
  search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
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
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-602f25c6-ebae-45f2-8685-c8f466fe5119' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
    else
      search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
    fi
    linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=602f25c6-ebae-45f2-8685-c8f466fe5119 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-30-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-602f25c6-ebae-45f2-8685-c8f466fe5119' {
    menuentry 'Ubuntu, with Linux 3.8.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-30-generic-advanced-602f25c6-ebae-45f2-8685-c8f466fe5119' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
        else
          search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
        fi
        echo    'Loading Linux 3.8.0-30-generic ...'
        linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=602f25c6-ebae-45f2-8685-c8f466fe5119 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-30-generic-recovery-602f25c6-ebae-45f2-8685-c8f466fe5119' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
        else
          search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
        fi
        echo    'Loading Linux 3.8.0-30-generic ...'
        linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=602f25c6-ebae-45f2-8685-c8f466fe5119 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-602f25c6-ebae-45f2-8685-c8f466fe5119' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
        else
          search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=602f25c6-ebae-45f2-8685-c8f466fe5119 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-602f25c6-ebae-45f2-8685-c8f466fe5119' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
        else
          search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=602f25c6-ebae-45f2-8685-c8f466fe5119 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
    else
      search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  602f25c6-ebae-45f2-8685-c8f466fe5119
    else
      search --no-floppy --fs-uuid --set=root 602f25c6-ebae-45f2-8685-c8f466fe5119
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-DEB65C55B65C2FEF' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  DEB65C55B65C2FEF
    else
      search --no-floppy --fs-uuid --set=root DEB65C55B65C2FEF
    fi
    chainloader +1
}
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=602f25c6-ebae-45f2-8685-c8f466fe5119 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=041b44e8-ccef-4386-88b4-c5900e158fcd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.8.0-19-generic               2
               =                boot/initrd.img-3.8.0-30-generic               1
               =                boot/vmlinuz-3.8.0-19-generic                  1
               =                boot/vmlinuz-3.8.0-30-generic                  1
               =                boot/vmlinuz-3.8.0-30-generic.efi.signed       1
               =                initrd.img                                     1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

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
  No volume groups found
/home/this/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected


```

---

### Post by andreazzz on 2013-09-27
Can't you boot into Windows, Ubuntu or nothing at all? According to the file you attached, you have two GRUB-files: one on each hard disk. I have screwed up my GRUB too lately, I fixed it by installing another Linux distro. 
Also worth trying: [http://askubuntu.com/questions/288396/windows-7-and-ubuntu-13-04-dual-boot-grub-menu-not-showing](http://askubuntu.com/questions/288396/windows-7-and-ubuntu-13-04-dual-boot-grub-menu-not-showing) 

Edit: I don't know if you tried grubfix from LiveCD?

---

### Post by matthew18 on 2013-10-03
I can boot into Windows 7. Ubuntu is installed but won't boot. Yes I did the grub fix from the LiveCD. Do I need to remove one of the grub files? If so, how?

---

### Post by oldfred on 2013-10-03
I would just install a Windows boot loader to sda.
Boot-Repair often defaults to installing grub to everything, so no matter what drive you have selected in BIOS it will boot grub.
But better to turn off auto repair, check update MBR and choose which operationg system and which MBR to install. I like having boot loader for each drive to boot the install on that drive. Or put the Windows boot loader on sda and grub on sdb. Then select to boot from sdb.
Do you get grub menu? 
If so may be video issue. If black screen you may need nomodeset.
Or some BIOS just do not like grub or kernel on external drives where files are beyond 100GB. Not sure if BIOS or grub issue. But solution is either a smaller / (root)  (with rest of space as /home or data) at beginning of drive or separate /boot at beginning of drive.

---

