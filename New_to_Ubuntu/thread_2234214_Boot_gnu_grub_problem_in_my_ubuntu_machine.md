---
title: "Boot/ gnu grub problem in my ubuntu machine"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by sozgentaha on 2014-07-13
Hi There;
I have faced a problem in my computer. Windows 7 partition can be seen from my ubuntu sector, but it does not loaded in grub menu. Here is the error definition. How can I overcome the problem? Thanks in advance.

[HTML]

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       215669472 sectors, but according to the info from 
                       fdisk, it has 220845553 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


[/HTML]

---

### Post by yancek on 2014-07-13
What you posted is just a small part of the bootinfoscript standard output which doesn't tell us much.  It shows you have at least two physical hard drives which you did not mention.  It also tells us that you have the Grub bootloader installed to the master boot record on both drives.  It doesn't show the grub.cfg file which contains the boot menu and a lot of other information which would be needed for you to get help.  Post the entire output.  You could also try just running this command, watch the output to see if windows is detected and if it is, try rebooting:  

```
sudo update-grub
```

---

### Post by sozgentaha on 2014-07-13
Hi Yancek;
I have already implemented the command *sudo update grub*. Here is the entire output of the boot info summary:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdc.

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
                       215669472 sectors, but according to the info from 
                       fdisk, it has 220845553 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   221,052,401   220,845,554   7 NTFS / exFAT / HPFS
/dev/sda3         221,052,926   488,396,799   267,343,874   5 Extended
/dev/sda5         221,052,928   484,737,023   263,684,096  83 Linux
/dev/sda6         484,739,072   488,396,799     3,657,728  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    15,240,575    15,232,512   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C20E98790E986865                       ntfs       Sistem Ayr&#305;ld&#305;
/dev/sda2        4C3C9FE03C9FC37E                       ntfs       
/dev/sda5        ed6428a1-922a-403d-bced-394c9570e93d   ext4       
/dev/sda6        9962f394-ef72-423c-b958-81f3d7a25b9d   swap       
/dev/sdc1        E32E-8CC5                              vfat       TAHASOZGEN
/dev/sr1                                                iso9660    VMCLITE 9.4.2.14

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/taha/TAHASOZGEN   vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
else
  search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ed6428a1-922a-403d-bced-394c9570e93d' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
    else
      search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
    fi
    linux    /boot/vmlinuz-3.13.0-30-generic root=/dev/sda5 ro  quiet splash $vt_handoff
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=/dev/sda5 ro  quiet splash $vt_handoff
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=/dev/sda5 ro recovery nomodeset 
    }
    menuentry 'Ubuntu, with Linux 3.11.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-24-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.11.0-24-generic ...'
        linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-24-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.11.0-24-generic ...'
        linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-43-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.5.0-43-generic ...'
        linux    /boot/vmlinuz-3.5.0-43-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-43-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.5.0-43-generic ...'
        linux    /boot/vmlinuz-3.5.0-43-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-41-generic-pae-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.2.0-41-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-41-generic-pae root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-41-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-41-generic-pae-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.2.0-41-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-41-generic-pae root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-41-generic-pae
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
    else
      search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
    else
      search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ed6428a1-922a-403d-bced-394c9570e93d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9962f394-ef72-423c-b958-81f3d7a25b9d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  62 00 61 00 73 00 73 00  79 00 5b 00 31 00 5d 00  |b.a.s.s.y.[.1.].|
00000010  2e 00 6a 00 70 00 67 00  53 27 02 00 00 00 10 00  |..j.p.g.S'......|
00000020  70 00 5a 00 00 00 00 00  74 21 02 00 00 00 15 00  |p.Z.....t!......|
00000030  b5 7f 43 d8 89 21 cd 01  32 02 47 d8 89 21 cd 01  |..C..!..2.G..!..|
00000040  32 02 47 d8 89 21 cd 01  b5 7f 43 d8 89 21 cd 01  |2.G..!....C..!..|
00000050  00 20 00 00 00 00 00 00  34 18 00 00 00 00 00 00  |. ......4.......|
00000060  20 20 00 00 00 00 00 00  0c 02 4c 00 45 00 46 00  |  ........L.E.F.|
00000070  54 00 5f 00 45 00 7e 00  31 00 2e 00 4a 00 50 00  |T._.E.~.1...J.P.|
00000080  47 00 02 00 00 00 40 00  ca 1e 02 00 00 00 40 00  |G.....@.......@.|
00000090  68 00 54 00 00 00 00 00  74 21 02 00 00 00 15 00  |h.T.....t!......|
000000a0  16 8f 11 b0 70 20 cd 01  a2 b3 25 b0 70 20 cd 01  |....p ....%.p ..|
000000b0  a2 b3 25 b0 70 20 cd 01  91 8c 25 b0 70 20 cd 01  |..%.p ....%.p ..|
000000c0  30 00 00 00 00 00 00 00  2b 00 00 00 00 00 00 00  |0.......+.......|
000000d0  20 20 00 00 00 00 00 00  09 01 6c 00 67 00 5b 00  |  ........l.g.[.|
000000e0  31 00 5d 00 2e 00 67 00  69 00 66 00 74 00 6d 00  |1.]...g.i.f.t.m.|
000000f0  ca 1e 02 00 00 00 40 00  68 00 58 00 00 00 00 00  |......@.h.X.....|
00000100  74 21 02 00 00 00 15 00  16 8f 11 b0 70 20 cd 01  |t!..........p ..|
00000110  a2 b3 25 b0 70 20 cd 01  a2 b3 25 b0 70 20 cd 01  |..%.p ....%.p ..|
00000120  91 8c 25 b0 70 20 cd 01  30 00 00 00 00 00 00 00  |..%.p ..0.......|
00000130  2b 00 00 00 00 00 00 00  20 20 00 00 00 00 00 00  |+.......  ......|
00000140  0b 02 4c 00 47 00 5f 00  31 00 5f 00 7e 00 31 00  |..L.G._.1._.~.1.|
00000150  2e 00 47 00 49 00 46 00  b6 28 02 00 00 00 0a 00  |..G.I.F..(......|
00000160  70 00 5e 00 00 00 00 00  74 21 02 00 00 00 15 00  |p.^.....t!......|
00000170  00 8a 4c 59 58 22 cd 01  d8 ac 7d 59 58 22 cd 01  |..LYX"....}YX"..|
00000180  d8 ac 7d 59 58 22 cd 01  00 8a 4c 59 58 22 cd 01  |..}YX"....LYX"..|
00000190  00 20 00 00 00 00 00 00  83 13 00 00 00 00 00 00  |. ..............|
000001a0  20 20 00 00 00 00 00 00  0e 01 6c 00 69 00 6b 00  |  ........l.i.k.|
000001b0  65 00 62 00 6f 00 78 00  5b 00 31 00 5d 00 00 fe  |e.b.o.x.[.1.]...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 b7 0f 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  b7 0f 00 d8 37 00 00 00  |............7...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-J5KhQtXM/Tmp_Log: No such file or directory



```

and here is the content of the grub.cfg file:

```

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
else
  search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ed6428a1-922a-403d-bced-394c9570e93d' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
    else
      search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
    fi
    linux    /boot/vmlinuz-3.13.0-30-generic root=/dev/sda5 ro  quiet splash $vt_handoff
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=/dev/sda5 ro  quiet splash $vt_handoff
    }
    menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-30-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.13.0-30-generic ...'
        linux    /boot/vmlinuz-3.13.0-30-generic root=/dev/sda5 ro recovery nomodeset 
    }
    menuentry 'Ubuntu, with Linux 3.11.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-24-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.11.0-24-generic ...'
        linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-24-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.11.0-24-generic ...'
        linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-43-generic-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.5.0-43-generic ...'
        linux    /boot/vmlinuz-3.5.0-43-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-43-generic-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.5.0-43-generic ...'
        linux    /boot/vmlinuz-3.5.0-43-generic root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-41-generic-pae-advanced-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.2.0-41-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-41-generic-pae root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-41-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-41-generic-pae-recovery-ed6428a1-922a-403d-bced-394c9570e93d' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
        else
          search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
        fi
        echo    'Loading Linux 3.2.0-41-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-41-generic-pae root=UUID=ed6428a1-922a-403d-bced-394c9570e93d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-41-generic-pae
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
    else
      search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  ed6428a1-922a-403d-bced-394c9570e93d
    else
      search --no-floppy --fs-uuid --set=root ed6428a1-922a-403d-bced-394c9570e93d
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

```

Thanks in advance.

---

### Post by oldfred on 2014-07-13
Changed to code tags. 

It looks like a Windows issue. The boot sector must have the same start & size info as the partition table and it is reporting that it is different. This cannot be fixed from Linux but is easily fixed with chkdsk from your Windows repairCD or flash drive.

If you did not make a Windows repair flash drive, you may be able to get into it with f8. But that almost never works from grub as it is too quick. You can try that but have to hit f8 at almost the same time as enter for Windows entry in grub.

You can also temporarily reinstall a Windows boot loader with Boot-Repair or manually from Linux and then f8 should be easier to use. 

But if f8 to get into repair console for Windows then your repair CD or flash drive is best.
Also some third party Windows tools may have drive repair tools that are similar or are chkdsk.

This often is caused by resizing Windows from outside Window with gparted for example. Much better to use Windows own tools to resize Windows and reboot immediately so it automatically runs chkdsk.

---

