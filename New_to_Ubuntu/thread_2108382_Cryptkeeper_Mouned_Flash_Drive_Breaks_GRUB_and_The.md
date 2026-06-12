---
title: "Cryptkeeper Mouned Flash Drive Breaks GRUB and Then Some"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-01-24
I have no Grub RESCUE Mode available at boot time. This happened when the EVGA video card was removed for a defective port. While EVGA was RMA-ing it. I used the on-board video. I had to change something, I cannot remember what, something to do with 800x600 or some other value. When new EVGA card was re-installed, I could not have the RESCUE mode or any other option as pulling down to an option in GRUB blanks the screen. I could not re-set the resolution. I posted about this at the GRUB#IRC, but never hear back.

This is the order of events leading to this post as best as a non-tech person can explain them. This is a non-kernel modified Precise Pangolin ver. 12.04 LTS.

1 - A SiliconDust HD HomeRun (tv) tuner card was added to this system. The MythTV software that forms the user interface (can watch and hear TV) has been anything but easy to config.

2 - As part of configging the MythTV software, something broke very badly. When I would run (call) MythTV Frontend (the gui) the app "broke" and once called, would bring up a screen about what country and language for Myth to use. But that locked in a loop that could not be stopped except for ALT SysRq R E I S U B K. That combination of keys restarts the OS. I was working to find a solution to this problem last night.

3 - As part of a forced re-boot, GRUB or FSTAB, I'm not knowledegable in those areas, put an error message during BOOT time. The Xubuntu 12.04 came up on screen then threw a message about 

/LEXAR 

cannot be mounted. Do you want to (S)kip, (M)ount or (M)anually I choose skip a time or two in forced re-boot I also chose Mount a time or two. Then, because the error message said the /LEXAR was not mounted (maybe it read not present or available) I pulled it out and tried a reboot. Then I shut the 'puter down for the night. LEXAR is a USB Flash, Thumb, or Jump Drive of 4 gig. It's installed in FSTAB, I believe, because it's an encrypted drive (actually folder(s) on this drive.

4 - This morning after two forced re-boots, the BOOT time hangs. It does not present the Skip Mount Manual options. It seems it's stopped early in the boottime process, but I'm saying this from looking at it, not from some measure

5 - I'm not at this forum in LiveCD mode.

6 - How can I do: sudo grub-update while I'm in LiveCD? What do I look for to fix this mess? Is it possible to run sudo aptitude purge mythtv-backend and the other Myth apps while in LiveCD mode?

7 - Current /etc/fstab is:

[SIZE="1"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=a19439e8-8efd-460b-8014-4a442c19628c	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=36cdd55c-9079-4455-8627-c3b8bfda3a45	/home	ext3	defaults,user_xattr	0	2
#Entry for /dev/sda1 :
UUID=A2CC8BA6CC8B7379	/media/System_Reserved	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=12BCECA0BCEC7F99	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0ac46a28-6e61-4dc4-b144-a792803ff60b	none	swap	sw	0	0
#Entry for /dev/sdb1 :
UUID=8874-D051	/LEXAR	vfat	uid=1000,gid=1000,umask=022	0	2[/SIZE]



A few minutes later I added the Results.txt of bootinfoscript. Sorry for the length of it.

                  Boot Info Script 0.61      [1 April 2012]

[SIZE="1"]
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   143,566,847   143,360,000   7 NTFS / exFAT / HPFS
/dev/sda3    *    143,572,905   174,176,729    30,603,825  83 Linux
/dev/sda4         174,176,791   781,417,664   607,240,874   5 Extended
/dev/sda5         174,176,793   764,420,894   590,244,102  83 Linux
/dev/sda6         764,420,958   781,417,664    16,996,707  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  62     7,700,151     7,700,090   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1010 MB, 1010826752 bytes
228 heads, 40 sectors/track, 216 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  40     1,969,919     1,969,880  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8021 MB, 8021606400 bytes
61 heads, 45 sectors/track, 5707 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048    15,667,199    15,665,152   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A2CC8BA6CC8B7379                       ntfs       System Reserved
/dev/sda2        12BCECA0BCEC7F99                       ntfs       
/dev/sda3        a19439e8-8efd-460b-8014-4a442c19628c   ext3       
/dev/sda5        36cdd55c-9079-4455-8627-c3b8bfda3a45   ext3       
/dev/sda6        0ac46a28-6e61-4dc4-b144-a792803ff60b   swap       swap
/dev/sdb1        8874-D051                              vfat       LEXAR
/dev/sdc1        5c9a6ed1-2994-4549-b87c-735f94f1cb55   ext3       1-gig-non-win
/dev/sdd1        5C98-CCE3                              vfat       8-GIG
/dev/sde         34A3-FD9E                              vfat       256-MEG
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
  set locale_dir=($root)/boot/grub/locale
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-36-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-36-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-36-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-36-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-36-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-36-generic ...'
	linux	/boot/vmlinuz-3.2.0-36-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-35-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-35-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-35-generic ...'
	linux	/boot/vmlinuz-3.2.0-35-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-34-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-34-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-34-generic ...'
	linux	/boot/vmlinuz-3.2.0-34-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-33-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-33-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-33-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-33-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-33-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-33-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-33-generic ...'
	linux	/boot/vmlinuz-3.2.0-33-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-32-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-32-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-32-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-32-generic ...'
	linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-31-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-31-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-31-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-31-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-31-generic ...'
	linux	/boot/vmlinuz-3.2.0-31-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-30-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-30-generic ...'
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-27-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-27-generic ...'
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-26-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-25-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-25-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-25-generic-pae root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 3.2.0-25-generic ...'
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro  vga=769  quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a19439e8-8efd-460b-8014-4a442c19628c ro recovery nomodeset  vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a19439e8-8efd-460b-8014-4a442c19628c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root A2CC8BA6CC8B7379
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=a19439e8-8efd-460b-8014-4a442c19628c	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=36cdd55c-9079-4455-8627-c3b8bfda3a45	/home	ext3	defaults,user_xattr	0	2
#Entry for /dev/sda1 :
UUID=A2CC8BA6CC8B7379	/media/System_Reserved	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=12BCECA0BCEC7F99	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=0ac46a28-6e61-4dc4-b144-a792803ff60b	none	swap	sw	0	0
#Entry for /dev/sdb1 :
UUID=8874-D051	/LEXAR	vfat	uid=1000,gid=1000,umask=022	0	2


--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-28-generic              6
               =                boot/initrd.img-3.2.0-25-generic              35
               =                boot/initrd.img-3.2.0-25-generic-pae          11
               =                boot/initrd.img-3.2.0-26-generic              18
               =                boot/initrd.img-3.2.0-26-generic-pae          160
               =                boot/initrd.img-3.2.0-27-generic              78
               =                boot/initrd.img-3.2.0-27-generic-pae           7
               =                boot/initrd.img-3.2.0-29-generic              205
               =                boot/initrd.img-3.2.0-29-generic-pae          90
               =                boot/initrd.img-3.2.0-30-generic              130
               =                boot/initrd.img-3.2.0-30-generic-pae          15
               =                boot/initrd.img-3.2.0-31-generic              39
               =                boot/initrd.img-3.2.0-31-generic-pae          235
               =                boot/initrd.img-3.2.0-32-generic              132
               =                boot/initrd.img-3.2.0-32-generic-pae          319
               =                boot/initrd.img-3.2.0-33-generic              21
               =                boot/initrd.img-3.2.0-33-generic-pae          57
               =                boot/initrd.img-3.2.0-34-generic              40
               =                boot/initrd.img-3.2.0-34-generic-pae          14
               =                boot/initrd.img-3.2.0-35-generic              10
               =                boot/initrd.img-3.2.0-35-generic-pae          20
               =                boot/initrd.img-3.2.0-36-generic              327
               =                boot/initrd.img-3.2.0-36-generic-pae          302
               =                boot/vmlinuz-2.6.35-28-generic                100
               =                boot/vmlinuz-3.2.0-25-generic                 18
               =                boot/vmlinuz-3.2.0-25-generic-pae             20
               =                boot/vmlinuz-3.2.0-26-generic                  4
               =                boot/vmlinuz-3.2.0-26-generic-pae             96
               =                boot/vmlinuz-3.2.0-27-generic                 247
               =                boot/vmlinuz-3.2.0-27-generic-pae             26
               =                boot/vmlinuz-3.2.0-29-generic                 541
               =                boot/vmlinuz-3.2.0-29-generic-pae             64
               =                boot/vmlinuz-3.2.0-30-generic                  3
               =                boot/vmlinuz-3.2.0-30-generic-pae              4
               =                boot/vmlinuz-3.2.0-31-generic                  6
               =                boot/vmlinuz-3.2.0-31-generic-pae              6
               =                boot/vmlinuz-3.2.0-32-generic                  3
               =                boot/vmlinuz-3.2.0-32-generic-pae              6
               =                boot/vmlinuz-3.2.0-33-generic                 386
               =                boot/vmlinuz-3.2.0-33-generic-pae              4
               =                boot/vmlinuz-3.2.0-34-generic                 19
               =                boot/vmlinuz-3.2.0-34-generic-pae             31
               =                boot/vmlinuz-3.2.0-35-generic                 14
               =                boot/vmlinuz-3.2.0-35-generic-pae              4
               =                boot/vmlinuz-3.2.0-36-generic                 17
               =                boot/vmlinuz-3.2.0-36-generic-pae              4
               =                vmlinuz                                        4
               =                vmlinuz.old                                   17

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  a2 ce b0 ca bc a8 9b 42  58 d0 40 22 e0 e5 24 89  |.......BX.@"..$.|
00000010  ec 8b a6 22 a1 1b 8e db  0b 6e 1b a5 99 a0 c3 ea  |...".....n......|
00000020  da ba cd 21 d9 04 51 b8  21 9e 66 7d f5 ad 2d 29  |...!..Q.!.f}..-)|
00000030  3a d4 e4 49 ce 97 aa 96  8c e4 b7 8a 22 91 0f aa  |:..I........"...|
00000040  e7 2f b5 73 3b 1e 9c 46  85 5c f9 97 fd f7 3f 0f  |./.s;..F.\....?.|
00000050  78 d3 f5 b8 c7 02 46 91  d6 f0 94 47 ee 8a 3d 26  |x.....F....G..=&|
00000060  08 ff 4f 25 7f a8 cd f7  2b bb a4 45 3a 5f 49 33  |..O%....+..E:_I3|
00000070  18 1d bb 77 26 30 8a 26  1f 0a 96 1b 01 fd 10 c8  |...w&0.&........|
00000080  9e bd 91 42 b2 1f 83 c1  ad b3 ea b2 f0 b3 af b5  |...B............|
00000090  6c a8 8a 27 09 7b 0c c4  07 49 5c 3e 95 13 d6 f5  |l..'.{...I\>....|
000000a0  3a 93 04 99 e4 a9 ff 78  ae 7c 5a 4d a0 84 43 64  |:......x.|ZM..Cd|
000000b0  4b 7d 62 a0 cf 9c 86 90  c4 fa d0 7f ad b8 2d 96  |K}b...........-.|
000000c0  fd e4 20 f9 59 22 60 43  ed 65 88 e9 2a de 08 0c  |.. .Y"`C.e..*...|
000000d0  b1 02 0b 23 e3 27 58 f1  c7 49 1e 88 c8 33 c4 19  |...#.'X..I...3..|
000000e0  9a 0e 65 38 91 98 d9 19  0d 03 00 c2 f7 5a 56 27  |..e8.........ZV'|
000000f0  59 75 23 65 0b 23 6a e0  22 30 f5 7f 77 28 34 c6  |Yu#e.#j."0..w(4.|
00000100  f1 1e 72 86 ed dc 17 5a  11 d3 34 02 7a 08 36 04  |..r....Z..4.z.6.|
00000110  86 bf e8 82 05 59 e1 1b  4a cc b6 fc 5b cd f4 de  |.....Y..J...[...|
00000120  2d b4 2f a8 a8 39 b8 45  7a d6 dd 28 52 8c 7f 1f  |-./..9.Ez..(R...|
00000130  a3 94 a4 b5 f7 8b 5e d7  87 52 d1 cd d2 d2 8c cc  |......^..R......|
00000140  bc 14 d6 0e ba b2 45 d0  be 89 56 7d 88 c1 af cd  |......E...V}....|
00000150  f6 7f ad b0 3b c6 f2 22  5a 8f 17 6d 82 2b 2a e4  |....;.."Z..m.+*.|
00000160  09 65 ef b4 17 be 9f 08  05 92 3c 91 a8 a9 a1 ab  |.e........<.....|
00000170  c0 6f 17 44 eb 69 e2 0e  76 c3 ae d0 91 ba f9 86  |.o.D.i..v.......|
00000180  80 50 ea d6 d1 d1 3c 93  5e 8f eb 42 d2 69 5d b8  |.P....<.^..B.i].|
00000190  b5 8f 62 97 f2 b6 f2 97  af ed 48 bf 39 36 ae dd  |..b.......H.96..|
000001a0  7a 1f 14 d8 6a 16 10 59  03 01 fc 96 b2 50 6e 1d  |z...j..Y.....Pn.|
000001b0  f6 ef b4 48 22 90 7f df  49 93 39 6f 32 f9 00 fe  |...H"...I.9o2...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 06 69 2e 23 00 fe  |...........i.#..|
000001d0  ff ff 05 fe ff ff 08 69  2e 23 a2 59 03 01 00 00  |.......i.#.Y....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in[/SIZE]

---

### Post by Mark_in_Hollywood on 2013-02-05
See here:


[http://ubuntuforums.org/showthread.php?t=2109070](http://ubuntuforums.org/showthread.php?t=2109070)


and here:


[http://ubuntuforums.org/showthread.php?t=2111329](http://ubuntuforums.org/showthread.php?t=2111329)


for what happened and a solution.

---

