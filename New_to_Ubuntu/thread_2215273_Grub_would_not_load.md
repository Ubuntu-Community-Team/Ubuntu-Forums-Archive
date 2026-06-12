---
title: "Grub would not load"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by leke2 on 2014-04-05
Hello everyone,

At first, I would like to thank you for view this thread. I have been having an issue with my grub2 and I have tried to repair this problem boot-repair from a live-cd, but instead it think it worsened the problem. Before running boot-repair, my machine just shows only "grub" with a blinking underscore, but I was not able to press any other key except ctrl+alt+del to reboot. So after running the bootrepair live-cd, no grub was showing and my computer just reboots itself continuously until I force shutdown.

So I was planing to purge the grub and re-install it, but I was advised by the "HOWTO" I read to run a bootinfoscript and paste the result here to seek help. The 'RESULT.txt' file is pasted below.

NOTE: I am a N00B and I really in an hurry to fix my machine.



```
                   Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    865153024 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 72 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD


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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda4: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Kali GNU/Linux 1.0
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


sda6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda7: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda8: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 58856 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   976,773,167   976,773,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    31,459,327    31,457,280 Data partition (Windows/Linux)
/dev/sda2      31,459,328    31,664,127       204,800 Data partition (Windows/Linux)
/dev/sda3      31,664,128   683,600,504   651,936,377 Data partition (Windows/Linux)
/dev/sda4     683,601,920   865,153,015   181,551,096 Data partition (Windows/Linux)
/dev/sda5     865,155,072   964,747,263    99,592,192 Data partition (Windows/Linux)
/dev/sda6     964,749,312   969,056,239     4,306,928 Swap partition (Linux)
/dev/sda7     969,058,304   976,771,055     7,712,752 Swap partition (Linux)
/dev/sda8     865,153,024   865,155,071         2,048 BIOS Boot partition


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 7742 MB, 7742685184 bytes
39 heads, 39 sectors/track, 9942 cylinders, total 15122432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          8,064    15,122,431    15,114,368   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        6CEAA79AEAA75ED8                       ntfs       PQSERVICE
/dev/sda2        F22AA8182AA7D83D                       ntfs       SYSTEM RESERVED
/dev/sda3        5E1C021E1C01F1B7                       ntfs       Windows7
/dev/sda4        e97282ba-73de-4584-961a-13506d5d1ad4   ext4       Ubuntu
/dev/sda5        05dea4ed-8761-4959-b287-39327b6ba435   ext4       kali
/dev/sda6        bf8672bc-ebf1-49f0-a8a3-0b8335e84b52   swap       kaliSwap
/dev/sda7        4e8a9184-95b2-4bcc-b51a-4b810ce4622b   swap       ubuntuSwap
/dev/sda8        ac33da7b-d8fe-4823-b5dd-de2289565af6   ext2       grubBoot
/dev/sdb1        1BE2-392C                              vfat       UUI


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/lubuntu/Ubuntu    ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda5        /media/lubuntu/kali      ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




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
insmod part_gpt
insmod ext2
set root='hd0,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
else
  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
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
  set timeout=10
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e97282ba-73de-4584-961a-13506d5d1ad4' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
	else
	  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
	fi
	linux	/boot/vmlinuz-3.5.0-37-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b  quiet splash acpi_backlight=vendor $vt_handoff
	initrd	/boot/initrd.img-3.5.0-37-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e97282ba-73de-4584-961a-13506d5d1ad4' {
	menuentry 'Ubuntu, with Linux 3.5.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-37-generic-advanced-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-37-generic ...'
		linux	/boot/vmlinuz-3.5.0-37-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b  quiet splash acpi_backlight=vendor $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-37-generic-recovery-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-37-generic ...'
		linux	/boot/vmlinuz-3.5.0-37-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-37-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-generic-advanced-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-27-generic ...'
		linux	/boot/vmlinuz-3.5.0-27-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b  quiet splash acpi_backlight=vendor $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-27-generic-recovery-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-27-generic ...'
		linux	/boot/vmlinuz-3.5.0-27-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-26-generic-advanced-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-26-generic ...'
		linux	/boot/vmlinuz-3.5.0-26-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b  quiet splash acpi_backlight=vendor $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-26-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-26-generic-recovery-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-26-generic ...'
		linux	/boot/vmlinuz-3.5.0-26-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-26-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-advanced-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-25-generic ...'
		linux	/boot/vmlinuz-3.5.0-25-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b  quiet splash acpi_backlight=vendor $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-recovery-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-25-generic ...'
		linux	/boot/vmlinuz-3.5.0-25-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b  quiet splash acpi_backlight=vendor $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-e97282ba-73de-4584-961a-13506d5d1ad4' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  e97282ba-73de-4584-961a-13506d5d1ad4
		else
		  search --no-floppy --fs-uuid --set=root e97282ba-73de-4584-961a-13506d5d1ad4
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset resume=UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-6CEAA79AEAA75ED8' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  6CEAA79AEAA75ED8
	else
	  search --no-floppy --fs-uuid --set=root 6CEAA79AEAA75ED8
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-F22AA8182AA7D83D' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  F22AA8182AA7D83D
	else
	  search --no-floppy --fs-uuid --set=root F22AA8182AA7D83D
	fi
	chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-5E1C021E1C01F1B7' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  5E1C021E1C01F1B7
	else
	  search --no-floppy --fs-uuid --set=root 5E1C021E1C01F1B7
	fi
	chainloader +1
}
menuentry 'Debian GNU/Linux (Kali Linux 1.0)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-05dea4ed-8761-4959-b287-39327b6ba435' {
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  05dea4ed-8761-4959-b287-39327b6ba435
	else
	  search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
	fi
	linux /boot/vmlinuz-3.7-trunk-686-pae root=UUID=05dea4ed-8761-4959-b287-39327b6ba435 ro quiet splash acpi_osi=Linux
	initrd /boot/initrd.img-3.7-trunk-686-pae
}
submenu 'Advanced options for Debian GNU/Linux (Kali Linux 1.0)' $menuentry_id_option 'osprober-gnulinux-advanced-05dea4ed-8761-4959-b287-39327b6ba435' {
	menuentry 'Debian GNU/Linux, with Linux 3.7-trunk-686-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7-trunk-686-pae--05dea4ed-8761-4959-b287-39327b6ba435' {
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  05dea4ed-8761-4959-b287-39327b6ba435
		else
		  search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
		fi
		linux /boot/vmlinuz-3.7-trunk-686-pae root=UUID=05dea4ed-8761-4959-b287-39327b6ba435 ro quiet splash acpi_osi=Linux
		initrd /boot/initrd.img-3.7-trunk-686-pae
	}
	menuentry 'Debian GNU/Linux, with Linux 3.7-trunk-686-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7-trunk-686-pae-root=UUID=05dea4ed-8761-4959-b287-39327b6ba435 ro single-05dea4ed-8761-4959-b287-39327b6ba435' {
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  05dea4ed-8761-4959-b287-39327b6ba435
		else
		  search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
		fi
		linux /boot/vmlinuz-3.7-trunk-686-pae root=UUID=05dea4ed-8761-4959-b287-39327b6ba435 ro single
		initrd /boot/initrd.img-3.7-trunk-686-pae
	}
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
# / was on /dev/sda5 during installation
UUID=e97282ba-73de-4584-961a-13506d5d1ad4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=7b470dc4-3153-424b-94e3-9bf2cc4be337 none            swap    sw              0       0
UUID=4e8a9184-95b2-4bcc-b51a-4b810ce4622b none swap sw 0 0
#UUID=ac33da7b-d8fe-4823-b5dd-de2289565af6	/boot	ext2	defaults	0	2
--------------------------------------------------------------------------------


=================== sda4: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 388.117694855 = 416.738201600  boot/grub/grub.cfg                             1
 329.033744812 = 353.297293312  boot/initrd.img-3.5.0-17-generic               3
 328.993804932 = 353.254408192  boot/initrd.img-3.5.0-25-generic               3
 329.038242340 = 353.302122496  boot/initrd.img-3.5.0-26-generic               3
 329.047363281 = 353.311916032  boot/initrd.img-3.5.0-27-generic               2
 329.042835236 = 353.307054080  boot/initrd.img-3.5.0-37-generic               2
 388.226165771 = 416.854671360  boot/vmlinuz-3.5.0-17-generic                  1
 388.230991364 = 416.859852800  boot/vmlinuz-3.5.0-25-generic                  1
 388.235805511 = 416.865021952  boot/vmlinuz-3.5.0-26-generic                  1
 388.284114838 = 416.916893696  boot/vmlinuz-3.5.0-27-generic                  1
 328.743099213 = 352.985214976  boot/vmlinuz-3.5.0-37-generic                  3


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
  load_env
fi
set default="4"
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


function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}


insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt5)'
  search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=10
play 480 440 1
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
insmod png
if background_image /usr/share/images/desktop-base/kali-grub.png; then
  set color_normal=white/black
  set color_highlight=black/white
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 3.7-trunk-686-pae' --class debian --class gnu-linux --class gnu --class os {
	load_video
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
	echo	'Loading Linux 3.7-trunk-686-pae ...'
	linux	/boot/vmlinuz-3.7-trunk-686-pae root=UUID=05dea4ed-8761-4959-b287-39327b6ba435 ro  quiet splash acpi_osi=Linux
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.7-trunk-686-pae
}
menuentry 'Debian GNU/Linux, with Linux 3.7-trunk-686-pae (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	load_video
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set=root 05dea4ed-8761-4959-b287-39327b6ba435
	echo	'Loading Linux 3.7-trunk-686-pae ...'
	linux	/boot/vmlinuz-3.7-trunk-686-pae root=UUID=05dea4ed-8761-4959-b287-39327b6ba435 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.7-trunk-686-pae
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_otheros ###


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
menuentry "Windows Vista (loader)" {
	set root=(hd0,msdos1)
	search --no-floppy --fs-uuid --set 6CEAA79AEAA75ED8
	chainloader +1
}


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
menuentry "Windows Vista (loader)" {
	set root=(hd0,msdos2)
	search --no-floppy --fs-uuid --set F22AA8182AA7D83D
	chainloader +1
}


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
menuentry "Windows Vista (loader)" {
	set root=(hd0,msdos3)
	search --no-floppy --fs-uuid --set EE048F49048F142D
	chainloader +1
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-26-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro quiet splash acpi_backlight=vendor $vt_handoff 
	initrd /boot/initrd.img-3.5.0-26-generic
}




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu, with Linux 3.5.0-26-generic (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-26-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro quiet splash acpi_backlight=vendor $vt_handoff 
	initrd /boot/initrd.img-3.5.0-26-generic
}




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu, with Linux 3.5.0-26-generic (recovery mode) (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-26-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset 
	initrd /boot/initrd.img-3.5.0-26-generic
}




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu, with Linux 3.5.0-25-generic (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-25-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro quiet splash acpi_backlight=vendor $vt_handoff 
	initrd /boot/initrd.img-3.5.0-25-generic
}




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu, with Linux 3.5.0-25-generic (recovery mode) (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-25-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset 
	initrd /boot/initrd.img-3.5.0-25-generic
}




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-17-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro quiet splash acpi_backlight=vendor $vt_handoff 
	initrd /boot/initrd.img-3.5.0-17-generic
}




# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sda5)" {
	set root=(hd0,msdos5)
	search --no-floppy --fs-uuid --set e97282ba-73de-4584-961a-13506d5d1ad4
	linux /boot/vmlinuz-3.5.0-17-generic root=UUID=e97282ba-73de-4584-961a-13506d5d1ad4 ro recovery nomodeset 
	initrd /boot/initrd.img-3.5.0-17-generic
}


### END /etc/grub.d/30_otheros ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# This entry automatically added by the Debian installer for a non-linux OS


### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sda7 during installation
UUID=05dea4ed-8761-4959-b287-39327b6ba435 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=bf8672bc-ebf1-49f0-a8a3-0b8335e84b52 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/usb0     auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------


=================== sda5: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 446.670646667 = 479.608954880  boot/grub/core.img                             1
 446.670654297 = 479.608963072  boot/grub/grub.cfg                             1
 414.405273438 = 444.964274176  boot/initrd.img-3.7-trunk-686-pae              2
 446.668949127 = 479.607132160  boot/vmlinuz-3.7-trunk-686-pae                 1
 446.668949127 = 479.607132160  vmlinuz                                        1


=============================== StdErr Messages: ===============================


  No volume groups found



```

---

### Post by oldfred on 2014-04-05
It looks like you have a Windows install that is configured for BIOS boot which with Windows only works from MBR(msdos) partitioning, not gpt. 
But you have a Ubuntu install and a Kali install and one or the other is to a gpt partitioned drive. You have the bios_grub partition that is required for BIOS boot from a gpt partitioned drive, but have it formatted, which it cannot be. It must be unformatted. Use gparted and remove format, set to unformatted and use boot-Repair to reinstall grub. 

But you will never get Windows to boot in BIOS mode from a gpt drive.
You may be able to convert back to MBR for Windows, but have to totally purge & reinstall grub in both installs to remove gpt references and partition changes will probably change UUIDs and require editing fstab. If new installs would probably be easier to just reinstall.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by leke2 on 2014-04-06
thank you. would get back to you.

---

### Post by leke2 on 2014-04-06
Thank you so much, grub is now functioning, but windows didn't load as you said; so I am planing on moving it to mbr I back it up. Thank you once again.

---

### Post by oldfred on 2014-04-06
I do not have Windows and do not know if any of this really works.

 Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
How UEFI works in Post #76 - skodabenz  thread by Avidanborisov
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

      
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

