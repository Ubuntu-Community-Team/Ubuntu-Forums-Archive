---
title: "Windows xp wont start after installing Lubuntu dual boot"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by simplical complex on 2013-06-14
Lubuntu loads up fine, but when I try to load up windows xp, all I get is a black screen with a blinking white rectangle in the top left. If I load up Hirens boot cd and select "boot from hard drive (Windows xp)", it starts up fine.   One thing that might have caused this. During the installation, at the part where you select partitions (after clicking &#8220;something else&#8221;), I accidentally clicked &#8220;create new partition table&#8221; and then accidentally clicked &#8220;continue&#8221; :P. I then hit &#8220;revert&#8221; in hopes it would undo whatever I did.   Any ideas on how to fix this? I was thinking maybe looking for a restore point on the windows system, or some program that could repair the boot process, or a windows boot cd (which doesn't look easy to create with Windows xp), but maybe this is something as simple as assigning a mount point, I have no idea.  May the code form in your favor

---

### Post by zemega on 2013-06-14
When your computer starts up, does it load GRUB first? Can you try enter Lubuntu first, enter terminal and type 'sudo update-grub' . Then try entering Windows XP.

---

### Post by simplical complex on 2013-06-14
> **zemega said:**
> When your computer starts up, does it load GRUB first? Can you try enter Lubuntu first, enter terminal and type 'sudo update-grub' . Then try entering Windows XP.

Here's what is says, but window still doesn't load up without hirens boot cd; I don't know why it found so many different linux things.

[https://www.dropbox.com/s/74dntvfw8laidym/update%20grub%20screenshot.png](https://www.dropbox.com/s/74dntvfw8laidym/update%20grub%20screenshot.png)

Thanks for the suggestion

P.S. there where a few different terminal programs that came with the os, I hit "Ctrl + Alt +T" to open the one I used.

---

### Post by coffeecat on 2013-06-14
> **simplical complex said:**
> I don't know why it found so many different linux things.

That's fairly normal. There are three versions of the Linux kernel in your Lubuntu installation and grub will create menu entries for all three in case the newest doesn't work.

We need a lot more information. All that screenshot tells us is that you seem to have two Windows installations on partitions sda1 and sda2, and if running update-grub hasn't helped booting into Windows, I suspect there may be a problem with Windows partition boot sector.

Boot up Lubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by simplical complex on 2013-06-14
RESULTS.txt:
```
                  Boot Info Script 0.61      [1 April 2012]








============================= Boot Info Summary: ===============================




 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => No boot loader is installed in the MBR of /dev/sdb.




sda1: __________________________________________________________________________




    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM




sda2: __________________________________________________________________________




    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 470337840. But according to the info from 
                       fdisk, sda2 starts at sector 227536896.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM




sda3: __________________________________________________________________________




    File system:       swap
    Boot sector type:  -
    Boot sector info: 




sda4: __________________________________________________________________________




    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab




sdb1: __________________________________________________________________________




    File system:       vfat
    Boot sector type:  -
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




/dev/sda1    *             63   227,536,895   227,536,833   7 NTFS / exFAT / HPFS
/dev/sda2         227,536,896   245,590,015    18,053,120   c W95 FAT32 (LBA)
/dev/sda3         482,082,816   488,396,799     6,313,984  82 Linux swap / Solaris
/dev/sda4         245,590,016   482,082,815   236,492,800  83 Linux








Drive: sdb _____________________________________________________________________




Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes




Partition  Boot  Start Sector    End Sector  # of Sectors  Id System




/dev/sdb1               8,192    15,523,839    15,515,648   b W95 FAT32








"blkid" output: ________________________________________________________________




Device           UUID                                   TYPE       LABEL




/dev/sda1        C23056183056142F                       ntfs       HP_PAVILION
/dev/sda2        4B6E-6BC0                              vfat       HP_RECOVERY
/dev/sda3        480c0aec-e6da-43d5-926f-1ee0815d4c80   swap       
/dev/sda4        d815476b-1916-4f52-a4ce-c4c3febefd21   ext4       
/dev/sdb1        3863-3033                              vfat       




================================ Mount points: =================================




Device           Mount_Point              Type       Options




/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/artie/3863-3033   vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)








================================ sda1/boot.ini: ================================




--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS




[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------




================================ sda2/boot.ini: ================================




--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------




=========================== sda4/boot/grub/grub.cfg: ===========================




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
set root='hd0,msdos4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
else
  search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d815476b-1916-4f52-a4ce-c4c3febefd21' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
    else
      search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
    fi
    linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-25-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-recovery-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-recovery-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro recovery nomodeset 
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
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
    else
      search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
    else
      search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###




### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows XP Media Center Edition (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-C23056183056142F' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  C23056183056142F
    else
      search --no-floppy --fs-uuid --set=root C23056183056142F
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows NT/2000/XP (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-4B6E-6BC0' {
    insmod part_msdos
    insmod fat
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  4B6E-6BC0
    else
      search --no-floppy --fs-uuid --set=root 4B6E-6BC0
    fi
    drivemap -s (hd0) ${root}
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




=============================== sda4/etc/fstab: ================================




--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=480c0aec-e6da-43d5-926f-1ee0815d4c80 none            swap    sw              0       0
--------------------------------------------------------------------------------




=================== sda4: Location of files loaded by Grub: ====================




           GiB - GB             File                                 Fragment(s)




               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.8.0-19-generic               1
               =                boot/initrd.img-3.8.0-23-generic               1
               =                boot/initrd.img-3.8.0-25-generic               1
               =                boot/vmlinuz-3.8.0-19-generic                  1
               =                boot/vmlinuz-3.8.0-23-generic                  1
               =                boot/vmlinuz-3.8.0-25-generic                  2
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2




======================== Unknown MBRs/Boot Sectors/etc: ========================




Unknown BootLoader on sda2




00000000  e9 a7 00 4d 53 57 49 4e  34 2e 31 00 02 10 3a 00  |...MSWIN4.1...:.|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 30 c9 08 1c  |........?...0...|
00000020  00 78 13 01 6b 22 00 00  00 00 00 00 f7 bd 0d 00  |.x..k"..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 6b 6e 4b 4e  4f 20 4e 41 4d 45 20 20  |..).knKNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200








========= Devices which don't seem to have a corresponding hard drive: =========




sdc sdd sde 




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
                  Boot Info Script 0.61      [1 April 2012]








============================= Boot Info Summary: ===============================




 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => No boot loader is installed in the MBR of /dev/sdb.




sda1: __________________________________________________________________________




    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM




sda2: __________________________________________________________________________




    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 470337840. But according to the info from 
                       fdisk, sda2 starts at sector 227536896.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM




sda3: __________________________________________________________________________




    File system:       swap
    Boot sector type:  -
    Boot sector info: 




sda4: __________________________________________________________________________




    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab




sdb1: __________________________________________________________________________




    File system:       vfat
    Boot sector type:  -
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




/dev/sda1    *             63   227,536,895   227,536,833   7 NTFS / exFAT / HPFS
/dev/sda2         227,536,896   245,590,015    18,053,120   c W95 FAT32 (LBA)
/dev/sda3         482,082,816   488,396,799     6,313,984  82 Linux swap / Solaris
/dev/sda4         245,590,016   482,082,815   236,492,800  83 Linux








Drive: sdb _____________________________________________________________________




Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes




Partition  Boot  Start Sector    End Sector  # of Sectors  Id System




/dev/sdb1               8,192    15,523,839    15,515,648   b W95 FAT32








"blkid" output: ________________________________________________________________




Device           UUID                                   TYPE       LABEL




/dev/sda1        C23056183056142F                       ntfs       HP_PAVILION
/dev/sda2        4B6E-6BC0                              vfat       HP_RECOVERY
/dev/sda3        480c0aec-e6da-43d5-926f-1ee0815d4c80   swap       
/dev/sda4        d815476b-1916-4f52-a4ce-c4c3febefd21   ext4       
/dev/sdb1        3863-3033                              vfat       




================================ Mount points: =================================




Device           Mount_Point              Type       Options




/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/artie/3863-3033   vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)








================================ sda1/boot.ini: ================================




--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS




[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------




================================ sda2/boot.ini: ================================




--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------




=========================== sda4/boot/grub/grub.cfg: ===========================




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
set root='hd0,msdos4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
else
  search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d815476b-1916-4f52-a4ce-c4c3febefd21' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
    else
      search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
    fi
    linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-25-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-recovery-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-recovery-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-d815476b-1916-4f52-a4ce-c4c3febefd21' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
        else
          search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 ro recovery nomodeset 
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
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
    else
      search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos4 --hint-efi=hd0,msdos4 --hint-baremetal=ahci0,msdos4  d815476b-1916-4f52-a4ce-c4c3febefd21
    else
      search --no-floppy --fs-uuid --set=root d815476b-1916-4f52-a4ce-c4c3febefd21
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###




### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows XP Media Center Edition (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-C23056183056142F' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  C23056183056142F
    else
      search --no-floppy --fs-uuid --set=root C23056183056142F
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows NT/2000/XP (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-4B6E-6BC0' {
    insmod part_msdos
    insmod fat
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  4B6E-6BC0
    else
      search --no-floppy --fs-uuid --set=root 4B6E-6BC0
    fi
    drivemap -s (hd0) ${root}
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




=============================== sda4/etc/fstab: ================================




--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=d815476b-1916-4f52-a4ce-c4c3febefd21 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=480c0aec-e6da-43d5-926f-1ee0815d4c80 none            swap    sw              0       0
--------------------------------------------------------------------------------




=================== sda4: Location of files loaded by Grub: ====================




           GiB - GB             File                                 Fragment(s)




               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.8.0-19-generic               1
               =                boot/initrd.img-3.8.0-23-generic               1
               =                boot/initrd.img-3.8.0-25-generic               1
               =                boot/vmlinuz-3.8.0-19-generic                  1
               =                boot/vmlinuz-3.8.0-23-generic                  1
               =                boot/vmlinuz-3.8.0-25-generic                  2
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2




======================== Unknown MBRs/Boot Sectors/etc: ========================




Unknown BootLoader on sda2




00000000  e9 a7 00 4d 53 57 49 4e  34 2e 31 00 02 10 3a 00  |...MSWIN4.1...:.|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 30 c9 08 1c  |........?...0...|
00000020  00 78 13 01 6b 22 00 00  00 00 00 00 f7 bd 0d 00  |.x..k"..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 6b 6e 4b 4e  4f 20 4e 41 4d 45 20 20  |..).knKNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200








========= Devices which don't seem to have a corresponding hard drive: =========




sdc sdd sde 




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







```


Another thing that I thought was unrelated, but maybe not, is when I boot up the computer, the grub menu doesn't display. Instead my HP vs17e monitor displays a message reading 
"Input Signal Out of Range
Change Settings to 1280x1024-60Hz"

and my sony sony SDM-HS75 (which displays the grub fine on my other computer running Ubuntu) reads
"Out of range
kHz/44Hz"

---

### Post by oldfred on 2013-06-14
For the video you can try this from Boot-Repair or manually edit the file we are not supposed to edit for a one time change. 

 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply

Grub tries to use the video from your install, what video card do you have and is system video ok?
      
 #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB.

   mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

Change the entry for gfxmode.
You can try this.

 gfxmode=640x480
or the suggestion it made.
      
 gfxmode=1280x1024-60Hz

For the XP issue. I might try chkdsk on both sda1 and sda2 from an XP install disk. I do not see anything specific and if it boots then nothning major should be wrong.


 XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by simplical complex on 2013-06-14
> **oldfred said:**
> For the video you can try this from Boot-Repair or manually edit the file we are not supposed to edit for a one time change. 

 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply

Awesome! GRUB displays beautifully now ^_^

I'll work on Windows again tomorrow.

Thanks!

---

### Post by simplical complex on 2013-06-15
> **oldfred said:**
> XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers  the drive if the drive requires it. The command also marks any bad  sectors and it recovers readable information. Run chkdsk several times,  until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you  specify the chkdsk command without arguments, the command checks the  current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

After fixing the grub I tried booting into windows again, and now after the white rectangle blinks for a while it displays
"No system disk or
Disk I/O error
press a key to restart
DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER"

I'm not sure if I have the system disk...

Running boot repair suggested that the windows backup partition was  almost full and that this could prevent it from loading, so I shrunk the  main windows partition to make space, but it didn't help.

So this morning I live booted into mini windows xp via hirens boot cd,  and ran the chkdsk as you suggested. The first run on the c drive  repaired a few clusters, but everything else came up clean and windows  still doesn't boot on it's own.

Maybe this was caused by resizing/moving around partitions with gparted in preparation to installing Lubuntu.
[http://gparted.sourceforge.net/faq.php#faq-6](http://gparted.sourceforge.net/faq.php#faq-6)
[http://gparted.sourceforge.net/faq.php#faq-16](http://gparted.sourceforge.net/faq.php#faq-16)

So I see two options, I can try to fix it with the window recovery  console (again I'm not sure if I can find my install cd, but I might be  able to buy one on ebay, or maybe download and install just the console  [http://www.bleepingcomputer.com/tutorials/how-to-install-the-windows-xp-recovery-console/](http://www.bleepingcomputer.com/tutorials/how-to-install-the-windows-xp-recovery-console/)  . But can I have that many options for booting up? I already have Lubuntu, Lubuntu options, memory test (came with the computer), and windows; Would a fith option be to many? I thought I heard that four was the limit.), or I can try to use a system restore point; there's at least one  almost every day for the past few months. But would using the system  restore point get rid of Lubuntu? If so that's not super helpful.

---

### Post by UltimateCat on 2013-06-15
In the future if you have to re-install Win's; you can shrink the Windows partition (about 1/2) in Windows first and than proceed to install Linux.
It's considerably easier; I think:-

Here's an idea of what it looks like. I'm running Fedora along-side Win's 7:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    38637567    19317760   27  Hidden NTFS WinRE
/dev/sda2   *    38637568    39354367      358400    7  HPFS/NTFS/exFAT
/dev/sda3        39354368   525322287   242983960    7  HPFS/NTFS/exFAT
/dev/sda4       525324288   976773167   225724440    5  Extended
/dev/sda5       525326336   526350335      512000   83  Linux
/dev/sda6       526352384   976773119   225210368   8e  Linux LVM



```

If you want to view all of the partitions on your machine you can run this as 'root'
```
fdisk -l

```

Hope that helps some-

---

### Post by coffeecat on 2013-06-16
> **simplical complex said:**
> After fixing the grub I tried booting into windows again, and now after the white rectangle blinks for a while it displays
"No system disk or
Disk I/O error
press a key to restart
DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER"

<snip>

Maybe this was caused by resizing/moving around partitions with gparted in preparation to installing Lubuntu.

<snip>

So I see two options, I can try to fix it with the window recovery  console (again I'm not sure if I can find my install cd, but I might be  able to buy one on ebay, or maybe download and install just the console  [http://www.bleepingcomputer.com/tutorials/how-to-install-the-windows-xp-recovery-console/](http://www.bleepingcomputer.com/tutorials/how-to-install-the-windows-xp-recovery-console/)  . 

I think you need to try the XP recovery console. Although there is nothing particularly untoward in the boot script output, it's possible there is a problem with your Windows XP partition boot sector, especially if you moved the beginning of the Windows partition when you resized it. What I would try is fixboot from the Windows XP recovery console. **Don't** run fixmbr. That will simply overwrite the 440 bytes of grub code in the mbr with Windows code and make matters worse. You need the grub code in the mbr to point to the grub menu in order to be able to boot Lubuntu and chain load Windows. If you write Windows mbr code, you won't be able to boot Lubuntu.

However, the instructions you link are to install the recovery console onto your hard drive for which you need the Windows XP CD. And this needs to be a Microsoft XP CD, not the manufacturer's restore disk that came with many pre-installed macines. You don't need to install the recovery console on the hard drive in your situation. Hopefully, all you need to do is to run fixboot from the recovery console after booting up with the XP CD.

I notice that there is a freeware BootFix utility in the Hiren's CD which *might* do the same job as Microsoft's fixboot. Emphasis on might - I have no experience of this at all. If you can get hold of a Microsoft XP CD, that would be better.

---

### Post by simplical complex on 2013-06-16
> **coffeecat said:**
> I think you need to try the XP recovery console. Although there is nothing particularly untoward in the boot script output, it's possible there is a problem with your Windows XP partition boot sector, especially if you moved the beginning of the Windows partition when you resized it. What I would try is fixboot from the Windows XP recovery console. **Don't** run fixmbr. That will simply overwrite the 440 bytes of grub code in the mbr with Windows code and make matters worse
Thanks, I was a little unsure about which commands would be appropiate. I shrunk the C partition, and then moved the windows backup partition next to it.

> However, the instructions you link are to install the recovery console onto your hard drive for which you need the Windows XP CD.
Dang I didn't notice that, I thought it was something downloadable.

> And this needs to be a Microsoft XP CD, not the manufacturer's restore disk that came with many pre-installed macines ... I notice that there is a freeware BootFix utility in the Hiren's CD which *might* do the same job as Microsoft's fixboot. Emphasis on might - I have no experience of this at all. If you can get hold of a Microsoft XP CD, that would be better.
I just ordered one for $5 (hopefully the right one), and we'll see how it goes in 3-5 business days.
[http://www.amazon.com/Windows-Recovery-VERSIONS-ULTRA-EDITION/dp/B009TUYB16/ref=sr_1_1?ie=UTF8&qid=1371389107&sr=8-1&keywords=windows+xp+cd](http://www.amazon.com/Windows-Recovery-VERSIONS-ULTRA-EDITION/dp/B009TUYB16/ref=sr_1_1?ie=UTF8&qid=1371389107&sr=8-1&keywords=windows+xp+cd)

Thanks for the help everyone!

---

