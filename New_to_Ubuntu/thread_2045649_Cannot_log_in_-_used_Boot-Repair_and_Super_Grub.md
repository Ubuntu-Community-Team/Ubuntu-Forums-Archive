---
title: "Cannot log in - used Boot-Repair and Super Grub"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by FitBoot on 2012-08-21
Hi,
Can someone please help me as I'm just about at mt last straw.

Trying to dual boot XP and Lubuntu (both installed). Trying to log in I get only black screen with blinking cursor.

Ran Boot-Repair and recvd the following report in the link it sent me. Instructed that I could now reboot, but it send me straight to GrubRescue prompt:

The report I recvd:
	
 	      **Paste from boot-repair at Tue, 21 Aug 2012 20:00:32 +0100**
```

          Boot Info Script 0.61-git Boot-Repair log      [4 July 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 7 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda1 starts at sector 16063. According to the info in 
                       the boot sector, sda1 has 57657221 sectors, but 
                       according to the info from fdisk, it has 78140161 
                       sectors.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Windows XP: FAT32
    Boot sector info: 
    Operating System:  
    Boot files:        /etc/fstab

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *         16,063    78,156,224    78,140,162   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   194,627,474   194,627,412  83 Linux
/dev/sdb2         194,627,475   290,135,286    95,507,812  83 Linux
/dev/sdb3         290,136,062   390,721,535   100,585,474   5 Extended
/dev/sdb5         290,136,064   338,182,938    48,046,875  83 Linux
/dev/sdb6         389,679,104   390,721,535     1,042,432  82 Linux swap / Solaris
/dev/sdb7         338,184,192   389,672,959    51,488,768  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AE10CB0010CACE91                       ntfs       FITBOOTDESK
/dev/sdb1        cc7fc9b7-778e-47ce-a9a5-6cf3a6c4a745   ext4       
/dev/sdb2        41718850-1b8f-41d0-acc2-c553faa63aa0   ext2       
/dev/sdb5        cd6c8257-0003-4056-aba2-b1a1afd740e4   ext4       
/dev/sdb6        2e638e7c-f24c-48c5-a5cc-7bdf89506338   swap       
/dev/sdb7        89fad4ba-9b40-4450-adc8-bad71dd55738   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=cd6c8257-0003-4056-aba2-b1a1afd740e4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2e638e7c-f24c-48c5-a5cc-7bdf89506338 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/initrd.img-3.2.0-23-generic               2
            ?? = ??             boot/vmlinuz-3.2.0-23-generic                  2
            ?? = ??             vmlinuz                                        2

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set default="Microsoft Windows XP Professional (on /dev/sda1)"
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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set=root 89fad4ba-9b40-4450-adc8-bad71dd55738
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos7)'
  search --no-floppy --fs-uuid --set=root 89fad4ba-9b40-4450-adc8-bad71dd55738
  set locale_dir=($root)/boot/grub/locale
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 89fad4ba-9b40-4450-adc8-bad71dd55738
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=89fad4ba-9b40-4450-adc8-bad71dd55738 ro acpi=off nomodeset  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 89fad4ba-9b40-4450-adc8-bad71dd55738
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=89fad4ba-9b40-4450-adc8-bad71dd55738 ro recovery nomodeset acpi=off nomodeset
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 89fad4ba-9b40-4450-adc8-bad71dd55738
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 89fad4ba-9b40-4450-adc8-bad71dd55738
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root AE10CB0010CACE91
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root cd6c8257-0003-4056-aba2-b1a1afd740e4
	linux /vmlinuz root=/dev/sdb5
	initrd /initrd.img
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root cd6c8257-0003-4056-aba2-b1a1afd740e4
	linux /vmlinuz root=/dev/sdb5
	initrd /initrd.img
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root cd6c8257-0003-4056-aba2-b1a1afd740e4
	linux /boot/vmlinuz-3.2.0-23-generic root=/dev/sdb5
	initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root cd6c8257-0003-4056-aba2-b1a1afd740e4
	linux /vmlinuz root=/dev/sdb5
	initrd /initrd.img
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root cd6c8257-0003-4056-aba2-b1a1afd740e4
	linux /vmlinuz root=/dev/sdb5
	initrd /initrd.img
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=89fad4ba-9b40-4450-adc8-bad71dd55738 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2e638e7c-f24c-48c5-a5cc-7bdf89506338 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-23-generic               2
            ?? = ??             boot/vmlinuz-3.2.0-23-generic                  1
            ?? = ??             vmlinuz                                        1

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[5694]) leaked on lvscan invocation. Parent PID 13642: bash
File descriptor 8 (pipe:[5694]) leaked on lvscan invocation. Parent PID 13642: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-21__11h56 ===================
boot-repair version : 3.18-0ppa41~lucid
boot-sav version : 3.191-0ppa49~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
File descriptor 7 (pipe:[5694]) leaked on lvs invocation. Parent PID 3203: /bin/sh
File descriptor 8 (pipe:[5694]) leaked on lvs invocation. Parent PID 3203: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 17.07.2012 , squeeze , Debian , i686)

=================== os-prober:
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sdb5:Ubuntu 12.04 LTS (12.04):Ubuntu:linux
/dev/sdb7:Ubuntu 12.04 LTS (12.04):Ubuntu1:linux

=================== blkid:
/dev/sda1: LABEL="FITBOOTDESK" UUID="AE10CB0010CACE91" TYPE="ntfs"
/dev/sdb1: UUID="cc7fc9b7-778e-47ce-a9a5-6cf3a6c4a745" TYPE="ext4"
/dev/sdb2: UUID="41718850-1b8f-41d0-acc2-c553faa63aa0" TYPE="ext2"
/dev/sdb5: UUID="cd6c8257-0003-4056-aba2-b1a1afd740e4" TYPE="ext4"
/dev/sdb6: UUID="2e638e7c-f24c-48c5-a5cc-7bdf89506338" TYPE="swap"
/dev/sdb7: UUID="89fad4ba-9b40-4450-adc8-bad71dd55738" TYPE="ext4"
/dev/loop0: TYPE="squashfs"


2 disks with OS, 3 OS : 2 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
=================== No kernel in /mnt/boot-sav/sdb1/boot:
grub


=================== No kernel in /mnt/boot-sav/sdb2/boot:





=================== sdb7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Microsoft Windows XP Professional (on /dev/sda1)"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=off nomodeset"

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





=================== sdb7/etc/grub.d/ :
drwxr-xr-x  2 root root        4096 Aug 16 14:47 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 18:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 17:53 05_debian_theme
-rwxr-xr-x 1 root root 7399 Apr 17 18:16 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 18:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 18:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 18:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 18:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 18:16 README




=================== dmesg | grep EFI :
BIOS is probably not EFI-compatible, and probably not setup in EFI-mode for this live-session.




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	ntldr,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda1.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sdb1.
sdb2	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	fstab-without-usr,	not-sep-usr,	/mnt/boot-sav/sdb2.
sdb5	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	nogrubinstall,	with--usr,	fstab-without-usr,	not-sep-usr,	/mnt/boot-sav/sdb5.
sdb7	: sdb,	not-sepboot,	grubenv-ok	grub2,	grub-pc,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	/mnt/boot-sav/sdb7.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	63 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD400BB-00DE (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      8224kB  40.0GB  40.0GB  primary  ntfs         boot


Model: ATA WDC WD2000JB-00G (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  99.6GB  99.6GB  primary   ext4            boot
2      99.6GB  149GB   48.9GB  primary   ext2
3      149GB   200GB   51.5GB  extended
5      149GB   173GB   24.6GB  logical   ext4
7      173GB   200GB   26.4GB  logical   ext4
6      200GB   200GB   534MB   logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)
/dev/sdb2 on /mnt/boot-sav/sdb2 type ext2 (rw)
/dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)
/dev/sdb7 on /mnt/boot-sav/sdb7 type ext4 (rw)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  admmidi agpgart amidi block bsg btrfs-control bus cdrom char console core cpu_dma_latency disk dmmidi dri dvd fd fd0 full fuse hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem midi net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sdb sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb vga_arbiter xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sda1: WINDOWS window Information Volume System ref~tmp~.txt RECYCLER Edition HD FilesMediaImpression Program Files Program ntldr NTDETECT.COM MSDOS.SYS linuxmint IO.SYS hiberfil.sys Settings and Documents Desktop CONFIG.SYS Config.Msi boot-sav boot.ini AUTOEXEC.BAT

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    252M  8.2M  243M   4% /
tmpfs        tmpfs    252M     0  252M   0% /lib/init/rw
udev         tmpfs    246M  216K  246M   1% /dev
tmpfs        tmpfs    252M     0  252M   0% /dev/shm
/dev/sr0   iso9660    346M  346M     0 100% /live/image
tmpfs        tmpfs    252M  8.2M  243M   4% /live/cow
tmpfs        tmpfs    252M     0  252M   0% /live
tmpfs        tmpfs    252M  8.0K  252M   1% /tmp
/dev/sda1  fuseblk     28G   11G   17G  40% /mnt/boot-sav/sda1
/dev/sdb1     ext4     92G  190M   87G   1% /mnt/boot-sav/sdb1
/dev/sdb2     ext2     45G  4.9M   43G   1% /mnt/boot-sav/sdb2
/dev/sdb5     ext4     23G  773M   21G   4% /mnt/boot-sav/sdb5
/dev/sdb7     ext4     25G  1.8G   22G   8% /mnt/boot-sav/sdb7

=================== fdisk -l:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02950294

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39070081    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002af6d

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12115    97313706   83  Linux
/dev/sdb2           12116       18061    47753906   83  Linux
/dev/sdb3           18061       24322    50292737    5  Extended
/dev/sdb5           18061       21051    24023437+  83  Linux
/dev/sdb6           24257       24322      521216   82  Linux swap / Solaris
/dev/sdb7           21051       24257    25744384   83  Linux

Partition table entries are not in disk order


User choice: Is sdb (200GB) a removable disk? no

=================== Recommended repair
recommendedrepair
This setting will reinstall the grub2 of sdb7 into the MBRs of all disks (except USB without OS).
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot



Reinstall the GRUB of sdb7 into all MBRs of disks with OS or not-USB

Reinstall the GRUB of sdb7 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0
chroot /mnt/boot-sav/sdb7 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb5

Reinstall the GRUB of sdb7 into the MBR of sdb
grub-install (GRUB) 1.99-21ubuntu3
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0
chroot /mnt/boot-sav/sdb7 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb5
Unhide GRUB boot menu in sdb7/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (200GB) disk!
paste.debian ko, using paste.ubuntu

```
    





I am working on a Dell Dimension L1000R
2 hard drives, both WD: C: is on 40G, D: (w/ Linux) is on 200G
512 MG RAM

Partitioned 2nd drive, Linux is sdb

Originally tried FixMBR and FixBoot from Win XP install discs repair. That seems to have wiped out the ability to see WinXP for booting at all.

Please, please help me get back to booting up both of my OSs and be very specific as I am an absolute Linux newb (and got quite tired of too many forums with partially correct responses (commands not right for Grub2 or for Ubuntu 12.04 LTS, etc.), or quick skim info without step by step walkthrough.
I really want to give Linux a go, but it's been a couple weeks now and I can't get anywhere.
Thanks in advance,

Charla

---

### Post by oldfred on 2012-08-21
From Windows also do  chkdsk.

Can you select in BIOS which drive to boot from. If so also run fixMBR so you can directly boot Windows from sda.

What video card or chip do you have? Do you get grub2 menu? You show 2 Ubuntus one in sdb5 & the other sdb7 and Windows in  sda1.

If you get grub menu try adding nomodeset to linux line in menu.


How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by YannBuntu on 2012-08-22
In addition to oldfred's comment:
- first boot on a Ubuntu CD, choose "Try Ubuntu", then backup your documents on external disk (or DVDs)
- have you already been able to use Ubuntu on this computer? (if yes, which version?)
- do you have a Windows CD?
- can you disconnect the disk containing Ubuntu ? (if yes, do it, then run Boot-Repair again, then reboot the PC, you will get access to Windows, this is a temporary fix before we find a way for Ubuntu's boot)
- you may need to use a little /boot partition at the start of the disk. See [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

