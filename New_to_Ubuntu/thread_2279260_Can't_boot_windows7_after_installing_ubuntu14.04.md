---
title: "Can't boot windows7 after installing ubuntu14.04"
date: 2015-05-22
forum: New to Ubuntu
---

### Post by batnox on 2015-05-22
I installed ubuntu14.04 alongside windows7 manually but then i didn't get a boot menu and got directed to windows7 directly. So, i uninstalled and reinstalled grub2 through boot-repair and now i get a boot menu, but windows7 is nowhere in it. It only shows ubuntu and advanced options for ubuntu. 
I got a pastecode whic is : [http://paste.ubuntu.com/11251064/](http://paste.ubuntu.com/11251064/)

I also checked [http://sourceforge.net/apps/mediawik...ms:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") which was given in a solution of another thread. Following which, i got
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       40550399 sectors, but according to the info from 
                       fdisk, it has 40962095 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda10 
                       starts at sector 63.
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda11 
                       starts at sector 63.
    Operating System:  
    Boot files:        

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of 
                       sda12 and looks at sector 907931680 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 14.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2    *        411,648   206,557,183   206,145,536   7 NTFS / exFAT / HPFS
/dev/sda3         935,811,072   976,773,167    40,962,096  12 Compaq diagnostics
/dev/sda4         206,559,230   935,811,071   729,251,842   f W95 Extended (LBA)
/dev/sda5         206,559,232   423,811,071   217,251,840   7 NTFS / exFAT / HPFS
/dev/sda6         423,813,120   505,726,199    81,913,080   7 NTFS / exFAT / HPFS
/dev/sda7         505,733,120   608,131,071   102,397,952   7 NTFS / exFAT / HPFS
/dev/sda8         608,133,120   710,531,071   102,397,952   7 NTFS / exFAT / HPFS
/dev/sda9         710,533,120   771,971,071    61,437,952   7 NTFS / exFAT / HPFS
/dev/sda10        771,973,120   890,370,494   118,397,375   7 NTFS / exFAT / HPFS
/dev/sda11        890,372,096   890,466,884        94,789   7 NTFS / exFAT / HPFS
/dev/sda12        890,468,352   935,811,071    45,342,720  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BE4C4B734C4B260D                       ntfs       SYSTEM_DRV
/dev/sda10       FEA2B3A3A2B35EB9                       ntfs       Studieeezzzzzz :'(
/dev/sda11       66C288EEC288C3B1                       ntfs       New Volume
/dev/sda12       85247a6d-c931-4fa5-b8da-630813a5a0d7   ext4       
/dev/sda2        0CAA4D3CAA4D2394                       ntfs       Windows7_OS
/dev/sda3        6C94368394365036                       ntfs       LENOVO_PART
/dev/sda5        0E826DF7826DE425                       ntfs       Multimedia
/dev/sda6        74F6AAE0F6AAA23A                       ntfs       New Volume
/dev/sda7        E0F2FF9AF2FF7360                       ntfs       My Stuff
/dev/sda8        725217265216EE9B                       ntfs       Food 4 thought
/dev/sda9        3C0C963F0C95F3DC                       ntfs       Software

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda12       /                        ext4       (rw,errors=remount-ro)


========================== sda12/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos12'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
else
  search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
    else
      search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
    fi
    linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-38-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
    menuentry 'Ubuntu, with Linux 3.16.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-advanced-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
        else
          search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
        fi
        echo    'Loading Linux 3.16.0-38-generic ...'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-38-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-recovery-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
        else
          search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
        fi
        echo    'Loading Linux 3.16.0-38-generic ...'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-38-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
        else
          search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
        else
          search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
        else
          search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-85247a6d-c931-4fa5-b8da-630813a5a0d7' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  85247a6d-c931-4fa5-b8da-630813a5a0d7
        else
          search --no-floppy --fs-uuid --set=root 85247a6d-c931-4fa5-b8da-630813a5a0d7
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic root=UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

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

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda12 during installation
UUID=85247a6d-c931-4fa5-b8da-630813a5a0d7 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-ZLL5TcDT/Tmp_Log: No such file or directory
```

Can anyone please help me getting windows7 on my bootmenu?

---

### Post by Bucky Ball on 2015-05-22
Welcome. Open a terminal and:

```
sudo update-grub
```

Do you see it picking up Windows? Reboot and see if it is there. 

I'm presuming Win was installed in legacy mode and so was Ubuntu as I see no EFI FAT32 partition anywhere in your bootinfo output.

When you boot from the Ubuntu selection currently, does it boot into Ubuntu okay? Also, you have no /swap partition. Why?

---

### Post by batnox on 2015-05-22
Thank you so much. Now it shows windows in boot-menu and it boots into ubuntu perfectly fine. I am sorry but i have a very naive queston. The boot menu now shows three options for windows
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Recovery Environment (loader) (on /dev/sda3)

Which one should I boot into?

---

### Post by Bucky Ball on 2015-05-22
Glad it worked. Ah, I see. Go for sda2 I'd say. Have a look at the bootinfo you posted closely and you might see why. sda1 seems to be the Windows boot manager partition, which I completely overlooked previously!

But yes, sda1 seems to be the boot manager, sda2 the Win install, and sda3 for recovery, if you need to recover Win (I think you can also run this for Win repairing).

Try that, if it works, please mark as 'solved' (see second link in my signature). Enjoy and good luck with it. ;)

---

### Post by batnox on 2015-05-22
Thanks a lot!

---

