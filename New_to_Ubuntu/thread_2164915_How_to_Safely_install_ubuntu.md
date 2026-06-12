---
title: "How to Safely install ubuntu"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-08-02
Hello!

I have a new HP laptop preinstalled with Windows 8. I checked and it does have UEFI. I would like to install Ubuntu alongside it, but I don't want to end up with an unusable system, as I can't get a new one.

I have heard that the windows partitioner is more reliable than Gparted. However, I also have heard that regular Backups are advised. What is the simplest and most efficient way to backup my whole system?

I have read that a special EFI partition is needed. How do you make an EFI partition?

And the most important question of all, How can I safely install ubuntu?

---

### Post by w1ll1am on 2013-08-02
The safest thing to do would probably be WUBI but I am sure that isn't what you want. 

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

1. First I would recommend turning off FastBoot in windows 8 look here

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

2. Then I would run a defrag in Windows.

3. Then use Clonezilla to do a complete drive image if you have the room to store it somewhere like a USB hard drive. If not continue at your own risk.

4. Then boot into a live Ubuntu session and use GParted to shrink and/or move your Windows partition.

5. Then reboot Windows and let it do a chkdsk which I think it will do by default if not you shouldn't have to worry about it.

6. Then install Ubuntu in the extra space you made in step 4 also look here for some help

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If anything fails then boot back into Clonzilla and restore the image you made.

---

### Post by deadflowr on 2013-08-02
Unfortunately, a WUBI install with Windows8 is not recommended at all, and might not even work.

For some guidance on how to install with UFEI look at oldfred's thread on the subject
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by w1ll1am on 2013-08-02
> **deadflowr said:**
> Unfortunately, a WUBI install with Windows8 is not recommended at all, and might not even work.

For some guidance on how to install with UFEI look at oldfred's thread on the subject
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Thanks for the update I was not aware WUBI did't work with Windows 8.

---

### Post by Jonathan Precise on 2013-08-03
Tried installing it, but it just boot windows again. Boot repair didn't repair the system. Here is the output:

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 21July2013]



============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.


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
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/HP/boot/bootmgfw.efi /EFI/HP/boot/bootmgr.efi 
                       /EFI/HP/boot/memtest.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/HP/EFI/Boot/bootx64.efi


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD


sda6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda7: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


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
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,353,727       532,480 EFI System partition
/dev/sda3       1,353,728     1,615,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,615,872   620,515,327   618,899,456 Data partition (Windows/Linux)
/dev/sda5     927,715,328   976,773,119    49,057,792 Data partition (Windows/Linux)
/dev/sda6     620,515,328   921,571,327   301,056,000 Data partition (Windows/Linux)
/dev/sda7     921,571,328   927,715,327     6,144,000 Swap partition (Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        2EF23F8AF23F54F5                       ntfs       WINRE
/dev/sda2        92D5-36E6                              vfat       
/dev/sda4        9C9E28929E2866CC                       ntfs       
/dev/sda5        08763C00763BED56                       ntfs       RECOVERY
/dev/sda6        1ceb24e6-fcf4-45cf-8c4d-44f0a8949941   ext4       
/dev/sda7        7e71dbf6-ceb1-4552-a3ac-b7736f50db8b   swap       
/dev/sr0                                                iso9660    Ubuntu 13.04 amd64


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




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
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
else
  search --no-floppy --fs-uuid --set=root 1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1ceb24e6-fcf4-45cf-8c4d-44f0a8949941' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
	else
	  search --no-floppy --fs-uuid --set=root 1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
	fi
	linux	/boot/vmlinuz-3.8.0-27-generic root=UUID=1ceb24e6-fcf4-45cf-8c4d-44f0a8949941 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.8.0-27-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1ceb24e6-fcf4-45cf-8c4d-44f0a8949941' {
	menuentry 'Ubuntu, with Linux 3.8.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-27-generic-advanced-1ceb24e6-fcf4-45cf-8c4d-44f0a8949941' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		else
		  search --no-floppy --fs-uuid --set=root 1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		fi
		echo	'Loading Linux 3.8.0-27-generic ...'
		linux	/boot/vmlinuz-3.8.0-27-generic root=UUID=1ceb24e6-fcf4-45cf-8c4d-44f0a8949941 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-27-generic-recovery-1ceb24e6-fcf4-45cf-8c4d-44f0a8949941' {
	recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		else
		  search --no-floppy --fs-uuid --set=root 1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		fi
		echo	'Loading Linux 3.8.0-27-generic ...'
		linux	/boot/vmlinuz-3.8.0-27-generic root=UUID=1ceb24e6-fcf4-45cf-8c4d-44f0a8949941 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-1ceb24e6-fcf4-45cf-8c4d-44f0a8949941' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		else
		  search --no-floppy --fs-uuid --set=root 1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=1ceb24e6-fcf4-45cf-8c4d-44f0a8949941 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-1ceb24e6-fcf4-45cf-8c4d-44f0a8949941' {
	recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		else
		  search --no-floppy --fs-uuid --set=root 1ceb24e6-fcf4-45cf-8c4d-44f0a8949941
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=1ceb24e6-fcf4-45cf-8c4d-44f0a8949941 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/25_custom ###


menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}


menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}


menuentry "EFI/HP/BIOSUpdate/CryptRSA32.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/BIOSUpdate/CryptRSA32.efi
}


menuentry "EFI/HP/BIOSUpdate/CryptRSA.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/BIOSUpdate/CryptRSA.efi
}


menuentry "EFI/HP/BIOSUpdate/HpBiosUpdate32.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/BIOSUpdate/HpBiosUpdate32.efi
}


menuentry "EFI/HP/BIOSUpdate/HpBiosUpdate.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/BIOSUpdate/HpBiosUpdate.efi
}


menuentry "EFI/HP/boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/boot/bootmgfw.efi
}


menuentry "EFI/HP/SystemDiags/CryptRSA32.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/SystemDiags/CryptRSA32.efi
}


menuentry "EFI/HP/SystemDiags/CryptRSA.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/SystemDiags/CryptRSA.efi
}


menuentry "EFI/HP/SystemDiags/SystemDiags32.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/SystemDiags/SystemDiags32.efi
}


menuentry "EFI/HP/SystemDiags/SystemDiags.efi" {
search --fs-uuid --no-floppy --set=root 92D5-36E6
chainloader (${root})/EFI/HP/SystemDiags/SystemDiags.efi
}
### END /etc/grub.d/25_custom ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-9C9E28929E2866CC' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  9C9E28929E2866CC
	else
	  search --no-floppy --fs-uuid --set=root 9C9E28929E2866CC
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows Recovery Environment (loader) (on /dev/sda5)' --class windows --class os $menuentry_id_option 'osprober-chain-08763C00763BED56' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  08763C00763BED56
	else
	  search --no-floppy --fs-uuid --set=root 08763C00763BED56
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
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
UUID=1ceb24e6-fcf4-45cf-8c4d-44f0a8949941 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=92D5-36E6  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda7 during installation
UUID=7e71dbf6-ceb1-4552-a3ac-b7736f50db8b none            swap    sw              0       0
UUID=92D5-36E6	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------


=================== sda6: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 356.020839691 = 382.274465792  boot/grub/grub.cfg                             1
 296.518661499 = 318.384488448  boot/vmlinuz-3.8.0-19-generic                  2
 297.030384064 = 318.933946368  boot/vmlinuz-3.8.0-27-generic                  1
 296.518661499 = 318.384488448  vmlinuz                                        2
 297.304771423 = 319.228567552  boot/initrd.img-3.8.0-19-generic               1
 297.618614197 = 319.565553664  boot/initrd.img-3.8.0-27-generic               1
 297.304771423 = 319.228567552  initrd.img                                     1


=============================== StdErr Messages: ===============================


File descriptor 8 (/proc/4911/mounts) leaked on lvscan invocation. Parent PID 21220: bash
File descriptor 16 (/usr/share/icons/ubuntu-mono-dark/places/16/user-home.svg) leaked on lvscan invocation. Parent PID 21220: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-08-03__18h55 ===================
boot-repair version : 3.199~ppa9~raring
boot-sav version : 3.199~ppa9~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa9~raring
boot-repair is executed in live-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




=================== os-prober:
/dev/sda4:Windows 8 (loader):Windows:chain
/dev/sda5:Windows Recovery Environment (loader):Windows1:chain
/dev/sda6:Ubuntu 13.04 (13.04):Ubuntu:linux


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="WINRE" UUID="2EF23F8AF23F54F5" TYPE="ntfs"
/dev/sda2: UUID="92D5-36E6" TYPE="vfat"
/dev/sda4: UUID="9C9E28929E2866CC" TYPE="ntfs"
/dev/sda5: LABEL="RECOVERY" UUID="08763C00763BED56" TYPE="ntfs"
/dev/sda6: UUID="1ceb24e6-fcf4-45cf-8c4d-44f0a8949941" TYPE="ext4"
/dev/sda7: UUID="7e71dbf6-ceb1-4552-a3ac-b7736f50db8b" TYPE="swap"
/dev/sr0: LABEL="Ubuntu 13.04 amd64" TYPE="iso9660"




1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.




WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.




WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== No kernel in /mnt/boot-sav/sda2/boot:
boot.sdi




Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda5/EFI/Boot/bootx64.efi


=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 24 17:05 grub.d
total 72
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root  1688 Dec  5  2012 20_memtest86+
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README








=================== sda6/etc/default/grub :


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






/boot/efi detected in the fstab of sda6: UUID=92D5-36E6   (sda2)
efibootmgr -v
gui-g2slaunch.sh: line 156: efibootmgr: command not found
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/media/ubuntu/9C9E28929E2866CC.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sda6	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.


sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes




=================== parted -l:


Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system     Name                          Flags
1      1049kB  420MB  419MB   ntfs            Basic data partition          hidden, diag
2      420MB   693MB  273MB   fat32           EFI system partition          boot
3      693MB   827MB  134MB                   Microsoft reserved partition  msftres
4      827MB   318GB  317GB   ntfs            Basic data partition
6      318GB   472GB  154GB   ext4
7      472GB   475GB  3146MB  linux-swap(v1)
5      475GB   500GB  25.1GB  ntfs            Basic data partition          hidden






                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


                                                                          
Error: Can't have a partition outside the disk!


=================== parted -lm:


BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA Hitachi HTS54505;
1:1049kB:420MB:419MB:ntfs:Basic data partition:hidden, diag;
2:420MB:693MB:273MB:fat32:EFI system partition:boot;
3:693MB:827MB:134MB::Microsoft reserved partition:msftres;
4:827MB:318GB:317GB:ntfs:Basic data partition:;
6:318GB:472GB:154GB:ext4::;
7:472GB:475GB:3146MB:linux-swap(v1)::;
5:475GB:500GB:25.1GB:ntfs:Basic data partition:hidden;




                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


                                                                          
Error: Can't have a partition outside the disk!




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
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda4 on /media/ubuntu/9C9E28929E2866CC type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 7f 0c 00 00 00 00 00  |................|
00000030  55 85 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  f5 54 3f f2 8a 3f f2 2e  |.........T?..?..|
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
ls /mnt/boot-sav/sda2/1: /*/*/* /*/*
ls /mnt/boot-sav/sda2: boot
EFI  . Please report this message to boot.repair@gmail.com


=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 0c 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e6 36 d5 92 4e  4f 20 4e 41 4d 45 20 20  |..).6..NO NAME  |
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 18 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff a7 e3 24 00 00 00 00  |...........$....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  cc 66 28 9e 92 28 9e 9c  |.........f(..(..|
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


=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 d0 4b 37  |........?.....K7|
00000020  00 00 00 00 80 00 80 00  ff 8f ec 02 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  56 ed 3b 76 00 3c 76 08  |........V.;v.<v.|
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


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.8G  197M  1.6G  12% /
udev           devtmpfs   1.8G   12K  1.8G   1% /dev
tmpfs          tmpfs      355M  872K  354M   1% /run
/dev/sr0       iso9660    785M  785M     0 100% /cdrom
/dev/loop0     squashfs   738M  738M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.8G  1.1M  1.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.8G   76K  1.8G   1% /run/shm
none           tmpfs      100M   44K  100M   1% /run/user
/dev/sda4      fuseblk    296G   51G  246G  17% /media/ubuntu/9C9E28929E2866CC
/dev/sda1      fuseblk    400M  236M  165M  59% /mnt/boot-sav/sda1
/dev/sda2      vfat       256M   91M  166M  36% /mnt/boot-sav/sda2
/dev/sda5      fuseblk     24G   21G  2.9G  88% /mnt/boot-sav/sda5
/dev/sda6      ext4       142G  3.2G  131G   3% /mnt/boot-sav/sda6


=================== fdisk -l:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1e1f4777


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.




EFI detected. Please check the options.
Partition outside the disk detected.


=================== Default settings
Recommended-Repair
This setting would purge (in order to unsign-grub) and reinstall the grub-efi of sda6, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files


=================== Settings chosen by the user
Custom-Repair
This setting will purge (in order to unsign-grub) and reinstall the grub-efi of sda6, using the following options:        sda2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    backup-and-rename-efi-files




/boot/efi added in sda6/fstab
Mount sda2 on /mnt/boot-sav/sda6/boot/efi
ls /mnt/boot-sav/sda6/boot/efi/1: /*/*/* /*/*
ls /mnt/boot-sav/sda6/boot/efi: boot
EFI  . Please report this message to boot.repair@gmail.com
chroot /mnt/boot-sav/sda6 apt-get -y --force-yes update
Purge the GRUB of sda6
grub-efi available


The following NEW packages will be installed:
grub-efi
0 upgraded, 1 newly installed, 0 to remove and 180 not upgraded.
DEBCHECK debOK, grub-efi
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo chroot "/mnt/boot-sav/sda6" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda6" apt-get install -fynsudo chroot "/mnt/boot-sav/sda6" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi
ls: cannot access /media/ubuntu/9C9E28929E2866CC/: No such file or directory


=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug  3 18:58 grub.d
total 4
-rwxr-xr-x 1 root root 1688 Dec  5  2012 20_memtest86+




/boot/efi detected in the fstab of sda6: UUID=92D5-36E6	 (sda2)
Then type: sudo chroot "/mnt/boot-sav/sda6" apt-get install -y --force-yes grub-efi linux
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi
ls: cannot access /media/ubuntu/9C9E28929E2866CC/: No such file or directory


=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug  3 18:59 grub.d
drwxr-xr-x  2 root root    4096 Aug  3 18:58 grub.d.bak
total 68
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README








=================== sda6/etc/default/grub :


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






/boot/efi detected in the fstab of sda6: UUID=92D5-36E6	 (sda2)
Unhide GRUB boot menu in sda6/etc/default/grub
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi
ls: cannot access /media/ubuntu/9C9E28929E2866CC/: No such file or directory


=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug  3 18:59 grub.d
drwxr-xr-x  2 root root    4096 Aug  3 18:58 grub.d.bak
total 68
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README








=================== sda6/etc/default/grub :


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






/boot/efi detected in the fstab of sda6: UUID=92D5-36E6	 (sda2)
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.


chroot /mnt/boot-sav/sda6 efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2002,3001,3000,2001,2003
Boot0001* Windows Boot Manager	HD(2,c8800,82000,8b75edff-3bc2-4ec5-97de-0054cf6077c1)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0002* Internal CD/DVD ROM Drive (UEFI)	ACPI(a0341d0,0)PCI(11,0)ATAPI(1,0,0)CD-ROM(1,6168c,11c0)RC
Boot2001* USB Drive (UEFI)	RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)	RC
Boot3000* Internal Hard Disk or Solid State Disk	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC


Reinstall the grub-efi linux of sda6
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :0
(debug) beglsefi1 ubuntu/grubx64.efi ; ubuntu , /mnt/boot-sav/sda6/boot/efi .
ls /mnt/boot-sav/sda6/boot/efi/1: /*/*/* /*/*
ls /mnt/boot-sav/sda6/boot/efi: boot
EFI  . Please report this message to boot.repair@gmail.com
df /dev/sda2
Save and rename /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi
ls /mnt/boot-sav/sda6/boot/efi/1: /*/*/* /*/*
ls /mnt/boot-sav/sda6/boot/efi: boot
EFI  . Please report this message to boot.repair@gmail.com
Add /mnt/boot-sav/sda6/boot/efi efi entries in /mnt/boot-sav/sda6/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi
sda2//mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi already added
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/BIOSUpdate/CryptRSA32.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/BIOSUpdate/CryptRSA.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/BIOSUpdate/HpBiosUpdate32.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/BIOSUpdate/HpBiosUpdate.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/SystemDiags/CryptRSA32.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/SystemDiags/CryptRSA.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/SystemDiags/SystemDiags32.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/HP/SystemDiags/SystemDiags.efi
sda2//mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi already added
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :0


chroot /mnt/boot-sav/sda6 efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2002,3001,3000,2001,2003
Boot0001* Windows Boot Manager	HD(2,c8800,82000,8b75edff-3bc2-4ec5-97de-0054cf6077c1)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0002* Internal CD/DVD ROM Drive (UEFI)	ACPI(a0341d0,0)PCI(11,0)ATAPI(1,0,0)CD-ROM(1,6168c,11c0)RC
Boot2001* USB Drive (UEFI)	RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)	RC
Boot3000* Internal Hard Disk or Solid State Disk	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC


chroot /mnt/boot-sav/sda6 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Windows 8 (loader) on /dev/sda4
Found Windows Recovery Environment (loader) on /dev/sda5
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.





```

Any ideas?

---

### Post by MrSteve on 2013-08-03
this maybe of help ...

[http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager](http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager)

---

### Post by Vladlenin5000 on 2013-08-03
> **MrSteve said:**
> this maybe of help ...

[http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager](http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager)


Nice, thanks :)
I think the EasyBCD solution might be the one for this weird case.

---

### Post by Jonathan Precise on 2013-08-03
> **MrSteve said:**
> this maybe of help ...

[http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager](http://superuser.com/questions/499617/how-can-i-add-linux-to-the-new-windows-8-boot-manager)

I also tried EasyBCD. However, that works with MBR files, not EFI Files used by UEFI. It just gave me a message that a file (ending with .mbr) could not be loaded. :(

Any other ideas? If not, then I'll find it easier to reinstall ubuntu.

---

### Post by Jonathan Precise on 2013-08-05
Just re-installed Ubuntu, and ran boot-repair. It totally fixed my problem. Thanks for all the help!!!

Thread marked as [SOLVED].

---

