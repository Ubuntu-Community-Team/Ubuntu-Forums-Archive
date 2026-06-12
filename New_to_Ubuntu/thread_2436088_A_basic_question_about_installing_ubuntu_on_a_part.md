---
title: "A basic question about installing ubuntu on a partitioned hard drive"
date: 2020-01-31
forum: New to Ubuntu
---

### Post by shirs on 2020-01-31
Hi,

I have an intel nuc computer with one hard drive and Windows 7  installed on it (some constrains make higher windows versions not  suitable for my work). I have recently created a new partition and  installed Ubuntu 18.04.3 LTS on it.  I planned on setting boot priorities from setup and didn't think of the  fact that setup does not recognize splitted parts of the same hard  drive. Now I can only start my computer with Ubuntu. I have some programs  installed on my Windows 7 OS which need to work with.

I assume that if I could format the partition on which the Ubuntu is  installed, the computer, when uploading, will recognize the Windows  installation (which is located in a separate partition and was not  touched)
I need to format the partition on which the Ubuntu is located in,  assuming that with no Ubuntu, the computer will startup from windows (am  I right?). I tried to do that uploading the computer from the image usb with the  Ubuntu installation. I can format (i.e.erase) partitions there. The  problem is, that if I format through the Ubuntu installation, I have to  complete installation process and, again, can't upload windows. If I quit the installation right after formatting, the format is  canceled and,again, I am left with Ubuntu only without the windows.

[INDENT]So my question is:   How do I format the Ubuntu partition without installing Ubuntu again  and without erasing the windows 7 installation?   Is there a way to format certain partitions on the computer without  running an operation system that will block the windows installation?


[/INDENT]
Thanks a lot for any help & suggestions

---

### Post by yetimon_64 on 2020-01-31
If you format the ubuntu partition you will end up on a grub rescue screen next boot, you will NOT end up back in Windows by simply removing ubuntu.

When you installed Ubuntu it put grub boot code into the boot records area of the hard drive. Removing Ubuntu will leave it "orphaned" and will stop you booting into anything.

 Be careful and await further help from some of the more experienced helpers with boot issues.

---

### Post by Impavidus on 2020-01-31
Having Ubuntu and Windows side by side on separate partitions of the same hard drive is absolutely no problem. With Windows 7 it's quite reliable. Windows 8 introduced some changes that made it harder. The bios (as this is Windows 7, you probably use bios, but maybe not) will just start whatever bootloader it finds at the start of the hard drive. If that's a Windows bootloader, it will start Windows, if it's a Linux bootloader, it should offer you a choice between Windows (if the Windows installation is recognised) and Ubuntu. So my guess is that during installation of Ubuntu the Windows system was not recognised, which may happen when the filesystem needs repairs. Or you accidentally deleted Windows. 

Best to see some details. Boot your Ubuntu live disk and install [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Create a boot info summary and show us the link. Don't run the recommended repair (yet).

Deleting Ubuntu won't help you, as yetimon_64 explained. Do you have a Windows repair disk? You may need one.

---

### Post by yancek on 2020-01-31
You might read through the pages at the link below which give a very detailed explanation of dual booting Ubuntu and windows 7.  Compare the information at this link to what you did.  One  possibility is that you installed Ubuntu UEFI while windows is not UEFI but a Legacy install.  Running boot repair with the 2nd option using the Create BootInfo Summary as suggested would provide information needed for someone to help.


[https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653](https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653)

Your assumption that the Ubuntu (or any LInux installer) does not recognize partitions on drives is not correct.  If your system is not hibernated, all partitions with various filesystems (including windows) should show.

---

### Post by shirs on 2020-02-01
Thanks for all the advises it really helps a lot.
As all of you suggested I installed the boot repair program and created a bootinfo summery.
Here below is the report as text.
I can also paste here the link to the report but i am not sure.. 
Is it customary to do that or is it considered "not safe"?
I trust the people here and will happily do that if you'll advise me to.
Here is the report and again, many thanks ;-)Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


```
============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/BOOT/fbx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   999,620,607   999,618,560   7 NTFS / exFAT / HPFS
/dev/sda2         999,620,608 1,748,719,615   749,099,008   7 NTFS / exFAT / HPFS
/dev/sda3       1,748,721,662 1,953,523,711   204,802,050   5 Extended
/dev/sda5       1,748,721,664 1,779,970,047    31,248,384  82 Linux swap / Solaris
/dev/sda6       1,779,972,096 1,937,899,519   157,927,424  83 Linux
/dev/sda7    *  1,937,901,568 1,953,523,711    15,622,144  ef EFI (FAT-12/16/32)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop15                                             squashfs   
/dev/loop16                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/sda1        12CEEF8ACEEF6487                       ntfs       system
/dev/sda2        340C72FF0C72BB84                       ntfs       DATA
/dev/sda5        8eaadd83-f811-4ea0-a84d-98521a63118d   swap       
/dev/sda6        9160d805-5d49-4766-87c5-764f18dd1fca   ext4       
/dev/sda7        F985-250D                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb  1 19:05 ata-Samsung_SSD_860_EVO_M.2_1TB_S415NB0K808716A-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Feb  1 19:05 wwn-0x5002538e406cd737 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  1 19:05 wwn-0x5002538e406cd737-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  1 19:05 wwn-0x5002538e406cd737-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  1 19:05 wwn-0x5002538e406cd737-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb  1 19:05 wwn-0x5002538e406cd737-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb  1 19:05 wwn-0x5002538e406cd737-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb  1 19:05 wwn-0x5002538e406cd737-part7 -> ../../sda7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/shir/system       fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda2        /media/shir/DATA         fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sda7        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9160d805-5d49-4766-87c5-764f18dd1fca
else
  search --no-floppy --fs-uuid --set=root 9160d805-5d49-4766-87c5-764f18dd1fca
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_IL
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
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
		set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9160d805-5d49-4766-87c5-764f18dd1fca' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9160d805-5d49-4766-87c5-764f18dd1fca
	else
	  search --no-floppy --fs-uuid --set=root 9160d805-5d49-4766-87c5-764f18dd1fca
	fi
        linux	/boot/vmlinuz-5.3.0-28-generic root=UUID=9160d805-5d49-4766-87c5-764f18dd1fca ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-5.3.0-28-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-9160d805-5d49-4766-87c5-764f18dd1fca' {
	menuentry 'Ubuntu, with Linux 5.3.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.3.0-28-generic-advanced-9160d805-5d49-4766-87c5-764f18dd1fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9160d805-5d49-4766-87c5-764f18dd1fca
		else
		  search --no-floppy --fs-uuid --set=root 9160d805-5d49-4766-87c5-764f18dd1fca
		fi
		echo	'Loading Linux 5.3.0-28-generic ...'
	        linux	/boot/vmlinuz-5.3.0-28-generic root=UUID=9160d805-5d49-4766-87c5-764f18dd1fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.3.0-28-generic
	}
	menuentry 'Ubuntu, with Linux 5.3.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.3.0-28-generic-recovery-9160d805-5d49-4766-87c5-764f18dd1fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9160d805-5d49-4766-87c5-764f18dd1fca
		else
		  search --no-floppy --fs-uuid --set=root 9160d805-5d49-4766-87c5-764f18dd1fca
		fi
		echo	'Loading Linux 5.3.0-28-generic ...'
	        linux	/boot/vmlinuz-5.3.0-28-generic root=UUID=9160d805-5d49-4766-87c5-764f18dd1fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.3.0-28-generic
	}
	menuentry 'Ubuntu, with Linux 5.0.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.0.0-23-generic-advanced-9160d805-5d49-4766-87c5-764f18dd1fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9160d805-5d49-4766-87c5-764f18dd1fca
		else
		  search --no-floppy --fs-uuid --set=root 9160d805-5d49-4766-87c5-764f18dd1fca
		fi
		echo	'Loading Linux 5.0.0-23-generic ...'
	        linux	/boot/vmlinuz-5.0.0-23-generic root=UUID=9160d805-5d49-4766-87c5-764f18dd1fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.0.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 5.0.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.0.0-23-generic-recovery-9160d805-5d49-4766-87c5-764f18dd1fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  9160d805-5d49-4766-87c5-764f18dd1fca
		else
		  search --no-floppy --fs-uuid --set=root 9160d805-5d49-4766-87c5-764f18dd1fca
		fi
		echo	'Loading Linux 5.0.0-23-generic ...'
	        linux	/boot/vmlinuz-5.0.0-23-generic root=UUID=9160d805-5d49-4766-87c5-764f18dd1fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.0.0-23-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=9160d805-5d49-4766-87c5-764f18dd1fca /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda7 during installation
UUID=F985-250D  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda5 during installation
UUID=8eaadd83-f811-4ea0-a84d-98521a63118d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 873.289268494 = 937.687212032  boot/grub/grub.cfg                             3
 851.061519623 = 913.820348416  boot/vmlinuz-5.0.0-23-generic                  2
 851.718479156 = 914.525753344  boot/vmlinuz-5.3.0-28-generic                  1
 851.061519623 = 913.820348416  vmlinuz                                        2
 867.154178619 = 931.099709440  boot/initrd.img-5.0.0-23-generic               2
 867.298660278 = 931.254845440  boot/initrd.img-5.3.0-28-generic               2
 867.154178619 = 931.099709440  initrd.img                                     2
 867.154178619 = 931.099709440  initrd.img.old                                 2

========================== sda7/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid 9160d805-5d49-4766-87c5-764f18dd1fca root hd0,msdos6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------


ADDITIONAL INFORMATION :
=================== log of boot-repair 20200201_1905 ===================
boot-repair version : 4ppa66
boot-sav version : 4ppa66
boot-sav-extra version : 4ppa66
glade2script version : 3.2.3~ppa4
boot-repair is executed in installed-session (Ubuntu 18.04.3 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-5.3.0-28-generic root=UUID=9160d805-5d49-4766-87c5-764f18dd1fca ro quiet splash vt.handoff=1

=================== os-prober:
/dev/sda6:The OS now in use - Ubuntu 18.04.3 LTS CurrentSession:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="system" UUID="12CEEF8ACEEF6487" TYPE="ntfs" PARTUUID="ffcd8bf7-01"
/dev/sda2: LABEL="DATA" UUID="340C72FF0C72BB84" TYPE="ntfs" PARTUUID="ffcd8bf7-02"
/dev/sda5: UUID="8eaadd83-f811-4ea0-a84d-98521a63118d" TYPE="swap" PARTUUID="ffcd8bf7-05"
/dev/sda6: UUID="9160d805-5d49-4766-87c5-764f18dd1fca" TYPE="ext4" PARTUUID="ffcd8bf7-06"
/dev/sda7: UUID="F985-250D" TYPE="vfat" PARTUUID="ffcd8bf7-07"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda1.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jan 31 08:59 grub.d
total 80
-rwxr-xr-x 1 root root 10046 Mar 18  2019 00_header
-rwxr-xr-x 1 root root  6258 Mar 18  2019 05_debian_theme
-rwxr-xr-x 1 root root 12693 Mar 18  2019 10_linux
-rwxr-xr-x 1 root root 11298 Mar 18  2019 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Mar 18  2019 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar 18  2019 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar 18  2019 40_custom
-rwxr-xr-x 1 root root   216 Mar 18  2019 41_custom
-rw-r--r-- 1 root root   483 Mar 18  2019 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
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



/boot/efi detected in the fstab of sda6: UUID=F985-250D   (sda7)
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fbx64.efi
/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 000A
Timeout: 1 seconds
BootOrder: 0004,0009,000A,0008,0001,0002,0000,0003
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0002* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0003* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0008* LAN : IBA CL Slot 00FE v0104	BBS(Network,,0x0)..BO
Boot0009* SATA : PORT 3 : Samsung SSD 860 EVO M.2 1TB : PART 0 : Boot Drive	BBS(HD,,0x0)..BO
Boot000A* UEFI : SATA : PORT 3 : Samsung SSD 860 EVO M.2 1TB : PART 2 : OS Bootloader	PciRoot(0x0)/Pci(0x17,0x0)/Sata(3,65535,0)/HD(3,MBR,0xffcd8bf7,0x683b5ffe,0xc350802)/HD(3,MBR,0x0,0x73820800,0xee6000)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
sda6	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-pc grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	notbiosboot, .
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /media/shir/system.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /media/shir/DATA.
sda7	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /boot/efi.

sda	: not-GPT,	BIOSboot-not-needed,	has-correctEFI, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA Samsung SSD 860:;
1:1049kB:512GB:512GB:ntfs::;
2:512GB:895GB:384GB:ntfs::;
3:895GB:1000GB:105GB:::;
5:895GB:911GB:16.0GB:linux-swap(v1)::;
6:911GB:992GB:80.9GB:ext4::;
7:992GB:1000GB:7999MB:fat32::boot, esp;

=================== lsblk:
KNAME  TYPE FSTYPE     SIZE LABEL
loop0  loop squashfs  54.4M
loop1  loop squashfs   3.7M
loop2  loop squashfs 149.9M
loop3  loop squashfs  1008K
loop4  loop squashfs     4M
loop5  loop squashfs  14.8M
loop6  loop squashfs  88.5M
loop7  loop squashfs   239M
loop8  loop squashfs  42.8M
loop9  loop squashfs  54.7M
loop10 loop squashfs  89.1M
loop11 loop squashfs   956K
loop12 loop squashfs   3.7M
loop13 loop squashfs  14.8M
loop14 loop squashfs   4.2M
loop15 loop squashfs  44.9M
loop16 loop squashfs 160.2M
sda    disk          931.5G
sda1   part ntfs     476.7G system
sda2   part ntfs     357.2G DATA
sda3   part              1K
sda5   part swap      14.9G
sda6   part ext4      75.3G
sda7   part vfat       7.5G

KNAME  ROTA RO RM STATE   MOUNTPOINT
loop0     0  1  0         /snap/core18/1066
loop1     0  1  0         /snap/gnome-system-monitor/100
loop2     0  1  0         /snap/gnome-3-28-1804/67
loop3     0  1  0         /snap/gnome-logs/61
loop4     0  1  0         /snap/gnome-calculator/406
loop5     0  1  0         /snap/gnome-characters/296
loop6     0  1  0         /snap/core/7270
loop7     0  1  0         /snap/wps-office/1
loop8     0  1  0         /snap/gtk-common-themes/1313
loop9     0  1  0         /snap/core18/1668
loop10    0  1  0         /snap/core/8268
loop11    0  1  0         /snap/gnome-logs/81
loop12    0  1  0         /snap/gnome-system-monitor/127
loop13    0  1  0         /snap/gnome-characters/399
loop14    0  1  0         /snap/gnome-calculator/544
loop15    0  1  0         /snap/gtk-common-themes/1440
loop16    0  1  0         /snap/gnome-3-28-1804/116
sda       0  0  0 running
sda1      0  0  0         /media/shir/system
sda2      0  0  0         /media/shir/DATA
sda3      0  0  0
sda5      0  0  0         [SWAP]
sda6      0  0  0         /
sda7      0  0  0         /boot/efi


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=16362796k,nr_inodes=4090699,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=3277420k,mode=755)
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15624)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
/var/lib/snapd/snaps/gnome-system-monitor_100.snap on /snap/gnome-system-monitor/100 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_67.snap on /snap/gnome-3-28-1804/67 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_61.snap on /snap/gnome-logs/61 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_296.snap on /snap/gnome-characters/296 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_406.snap on /snap/gnome-calculator/406 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1066.snap on /snap/core18/1066 type squashfs (ro,nodev,relatime,x-gdu.hide)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/core_7270.snap on /snap/core/7270 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/wps-office_1.snap on /snap/wps-office/1 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1313.snap on /snap/gtk-common-themes/1313 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda7 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/121 type tmpfs (rw,nosuid,nodev,relatime,size=3277420k,mode=700,uid=121,gid=125)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=3277420k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/var/lib/snapd/snaps/core18_1668.snap on /snap/core18/1668 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_8268.snap on /snap/core/8268 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_81.snap on /snap/gnome-logs/81 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_127.snap on /snap/gnome-system-monitor/127 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_399.snap on /snap/gnome-characters/399 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_544.snap on /snap/gnome-calculator/544 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1440.snap on /snap/gtk-common-themes/1440 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_116.snap on /snap/gnome-3-28-1804/116 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda2 on /media/shir/DATA type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda1 on /media/shir/system type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity mq power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cec0 char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg kvm lightnvm lirc0 log lp0 mapper mcelog media0 media1 media2 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null parport0 port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 serial sg0 shm snapshot snd stderr stdin stdout udmabuf uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 video1 video2 video3 video4 video5 zero zfs
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff f7 94 3b 00 00 00 00  |...........;....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  87 64 ef ce 8a ef ce 12  |.........d......|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 95 3b  |........?......;|
00000020  00 00 00 00 80 00 80 00  ff 57 a6 2c 00 00 00 00  |.........W.,....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  84 bb 72 0c ff 72 0c 34  |..........r..r.4|
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

=================== hexdump -n512 -C /dev/sda7
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 82 73  |........?......s|
00000020  00 60 ee 00 80 3b 00 00  00 00 00 00 02 00 00 00  |.`...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 0d 25 85 f9 4e  4f 20 4e 41 4d 45 20 20  |..).%..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   16G     0   16G   0% /dev
tmpfs          tmpfs     3.2G  2.2M  3.2G   1% /run
/dev/sda6      ext4       74G   20G   50G  29% /
tmpfs          tmpfs      16G  370M   16G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs      16G     0   16G   0% /sys/fs/cgroup
/dev/loop1     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/100
/dev/loop2     squashfs  150M  150M     0 100% /snap/gnome-3-28-1804/67
/dev/loop3     squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/61
/dev/loop5     squashfs   15M   15M     0 100% /snap/gnome-characters/296
/dev/loop4     squashfs  4.2M  4.2M     0 100% /snap/gnome-calculator/406
/dev/loop0     squashfs   55M   55M     0 100% /snap/core18/1066
/dev/loop6     squashfs   89M   89M     0 100% /snap/core/7270
/dev/loop7     squashfs  240M  240M     0 100% /snap/wps-office/1
/dev/loop8     squashfs   43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/sda7      vfat      7.5G  6.1M  7.5G   1% /boot/efi
tmpfs          tmpfs     3.2G   16K  3.2G   1% /run/user/121
tmpfs          tmpfs     3.2G   40K  3.2G   1% /run/user/1000
/dev/loop9     squashfs   55M   55M     0 100% /snap/core18/1668
/dev/loop10    squashfs   90M   90M     0 100% /snap/core/8268
/dev/loop11    squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop12    squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/127
/dev/loop13    squashfs   15M   15M     0 100% /snap/gnome-characters/399
/dev/loop14    squashfs  4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/loop15    squashfs   45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop16    squashfs  161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/sda2      fuseblk   358G   98M  358G   1% /media/shir/DATA
/dev/sda1      fuseblk   477G  218G  260G  46% /media/shir/system

=================== fdisk -l:
Disk /dev/loop0: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 88.5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 239 MiB, 250630144 bytes, 489512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xffcd8bf7

Device     Boot      Start        End   Sectors   Size Id Type
/dev/sda1             2048  999620607 999618560 476.7G  7 HPFS/NTFS/exFAT
/dev/sda2        999620608 1748719615 749099008 357.2G  7 HPFS/NTFS/exFAT
/dev/sda3       1748721662 1953523711 204802050  97.7G  5 Extended
/dev/sda5       1748721664 1779970047  31248384  14.9G 82 Linux swap / Solaris
/dev/sda6       1779972096 1937899519 157927424  75.3G 83 Linux
/dev/sda7  *    1937901568 1953523711  15622144   7.5G ef EFI (FAT-12/16/32)


Disk /dev/loop8: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 54.7 MiB, 57294848 bytes, 111904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 89.1 MiB, 93417472 bytes, 182456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 44.9 MiB, 47063040 bytes, 91920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 160.2 MiB, 167931904 bytes, 327992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub2 of sda6 into the MBR of sda.
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair


The boot files of [The OS now in use - Ubuntu 18.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2020-02-01
You cannot install Ubuntu in newer UEFI boot mode with Windows in old BIOS boot mode on same drive. And really should always install Ubuntu in same boot mode even if multiple drives.

Windows only boots in BIOS mode from MBR drives and must have boot flag on primary NTFS partition with its boot files, your sda1.
Windows only boots in UEFI mode from gpt partitioned drives, but you cannot easily convert.

Ubuntu lets you install in UEFI boot mode to the old MBR partitioned drive, but really should not.
UEFI requires boot flag on ESP and you can only have one boot flag per drive, so cannot have Windows boot flag on its NTFS partition and UEFI's boot flag on ESP.

Use gparted to move boot flag back to sda1.
Boot Windows and make sure it is ok. Grub only boots working Windows.
Make sure you have Windows repair flash drive.

Then use Boot-Repair or manually uninstall grub UEFI version and install grub's BIOS boot version grub-pc. 
In Boot-Repair you have to use advanced mode and be sure to always boot live installer in BIOS boot mode.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Long term better to have Windows in UEFI boot mode on gpt drive but that is major redo of entire system.

---

### Post by shirs on 2020-02-01
> **oldfred said:**
> You cannot install Ubuntu in newer UEFI boot mode with Windows in old BIOS boot mode on same drive. And really should always install Ubuntu in same boot mode even if multiple drives.

Windows only boots in BIOS mode from MBR drives and must have boot flag on primary NTFS partition with its boot files, your sda1.
Windows only boots in UEFI mode from gpt partitioned drives, but you cannot easily convert.

Ubuntu lets you install in UEFI boot mode to the old MBR partitioned drive, but really should not.
UEFI requires boot flag on ESP and you can only have one boot flag per drive, so cannot have Windows boot flag on its NTFS partition and UEFI's boot flag on ESP.

Use gparted to move boot flag back to sda1.
Boot Windows and make sure it is ok. Grub only boots working Windows.
Make sure you have Windows repair flash drive.

Then use Boot-Repair or manually uninstall grub UEFI version and install grub's BIOS boot version grub-pc. 
In Boot-Repair you have to use advanced mode and be sure to always boot live installer in BIOS boot mode.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Long term better to have Windows in UEFI boot mode on gpt drive but that is major redo of entire system.
--------------------------------------------------------------------------------------------------------------------------------------------------
Thanks a lot for the instructions :wink:[URL="http://paste.ubuntu.com/p/cMCHJDzsRw/"]
[/URL]
I tried to follow them but my PC still uploads with Ubuntu only.
The report is here: [http://paste.ubuntu.com/p/cMCHJDzsRw/](http://paste.ubuntu.com/p/cMCHJDzsRw/)[URL="http://paste.ubuntu.com/p/cMCHJDzsRw/"]
[/URL]I would be grateful if any of you could have a look. 
Maybe I should uncheck the esp when managing sda7 with GParted? 
(I have attached screenshot)

Thanks!

---

### Post by yancek on 2020-02-01
You have an msdos drive so you need Legacy/CSM enabled in the BIOS so it does not boot EFI.  Grub won't boot a legacy windows from an EFI Grub which you can see as windows is not detected when boot repair ran udate-grub.

---

### Post by oldfred on 2020-02-01
When you had the Windows BIOS boot loader in the MBR, did it boot Windows in BIOS mode?
You cannot have system set to boot in UEFI mode, it must be legacy/CSM/BIOS.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

It looks like you now have grub installed to MBR.
but you are booting live installer in UEFI mode.
The default setting in UEFI is only for installed systems.
You should get two boot options for Ubuntu live installer, one clearly UEFI and other BIOS. Mine shows [noparse]UEFI:PMAP[/noparse] and PMAP. Most use name or label of flash drive where mine shows PMAP.

---

### Post by shirs on 2020-02-02
> **oldfred said:**
> When you had the Windows BIOS boot loader in the MBR, did it boot Windows in BIOS mode?
You cannot have system set to boot in UEFI mode, it must be legacy/CSM/BIOS.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

It looks like you now have grub installed to MBR.
but you are booting live installer in UEFI mode.
The default setting in UEFI is only for installed systems.
You should get two boot options for Ubuntu live installer, one clearly UEFI and other BIOS. Mine shows [noparse]UEFI:PMAP[/noparse] and PMAP. Most use name or label of flash drive where mine shows PMAP.
----------------------------------------------------------------------------------------------------------------------------

So, how do I get these two boot options?
For now, when I view GParted, 
I have on my sda7 partition (which, I think, is the one Ubuntu boots from) - "esp" flag
Should I change it to something else?
The options are:
boot, diag, hidden, irst, lba,lvm,palo,prep,raid

Thanks again :wink: ](*,)

---

### Post by yancek on 2020-02-02
MBR is the master boot record which has been in use for 35+ years.  EFI is a new method.  You now have Grub code in the MBR and can boot Ubuntu so use GParted to uncheck the boot and esp boxes for sda7.  Your last boot repair shows that the windows boot flag is set on sda1 so that's a step in the right direction.

The two options referred to are when you boot the computer and access the BIOS firmware, the same way you changed boot priority to boot the Ubuntu install usb.  You should see the manufacturer name of the usb (Sandisk, Toshiba, Lexar or whatever it is) and one entry will have UEFI and one will not.  Use the one that does not.  Once you have done this, run sudo update-grub again from Ubuntu and watch the output for a windows entry.

My experience is that a Linux install (Ubuntu) in Legacy mode will not boot a windows EFI install and an EFI install of Linux (Ubuntu) will not boot a Legacy install of windows.

---

### Post by oldfred on 2020-02-02
You should not have any boot flags on sda7. Uncheck them all.

From the link below in my signature.
Acronyms:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

The MBR - Master Boot Record is how BIOS based systems boot. It also refers to the partitioning of a drive using the MBR.
How BIOS/MBR computers boot.
Multibooters, Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

---

### Post by shirs on 2020-02-02
So I managed to do it!! :guitar::cool:\\:D/
Turns out that after applying all of your suggestions there was not much left to do..
I just had to enter BIOS and uncheck EFI mode upboot (which I accidently left checked)
and check Legacy mode (which I think was not checked)
and thats it.
In the following boot, both windows 7 and Ubuntu 18.04.3 appeared

Thank you all!!:KS

---

### Post by shirs on 2020-02-02
Thank you for the links!!
Thanks to you, The windows is showing now together with the Ubuntu.
But I will still go over these links since everything here is so new to me.

Thanks again!!

---

