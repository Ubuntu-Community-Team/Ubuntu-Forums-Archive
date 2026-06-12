---
title: "Help with Ubuntu 12.04 install."
date: 2012-07-04
forum: New to Ubuntu
---

### Post by Deeplove on 2012-07-04
Hi all. I'm totally new to Linux and wanted to give it a try. I downloaded Ubuntu 12.04 onto my Flash Drive, tried it out and liked it. So I went ahead and installed it. Now, I have Windows 7 on my main HDD. I have a 2nd HDD that was formatted and wanted to install it on that. I don't want to mess with my main HDD. So I did the process and selected the whole HDD for Ubuntu. Everything finished and asked to restart.

Now, my PC won't ask me if I want to Boot from Windows 7 or Ubuntu. It just goes straight to Windows login. I reset and I select my 2nd HDD with Ubuntu manually. Well, I select the first option to load up Ubuntu and it goes into a blank purple screen and nothing happens after that. Am I doing something completely wrong?

Any help is greatly appreciated.

---

### Post by papibe on 2012-07-04
Hi Deeplove. Welcome to the forums!

It looks like grub (the program that shows the boot options) was not installed in the main disk (the one that is set on the BIOS to boot up from).

I would recommend using the CD/USB installer as a Live CD,  and repair your boot disk using the tool Boot-Repair. Take a look at this [guide]("https://help.ubuntu.com/community/Boot-Repair") for details.

I hope it helps, and tell us how it goes.
Regards.

---

### Post by Deeplove on 2012-07-04
Well, I did what it said on the instructions. I ran it through Live USB. I get the screen now where I can select the both Ubuntu and Windows 7. It doesn't go to Windows 7 directly anymore. What happens now is that when I select Ubuntu, it stops at a black screen and then it stops. I'm not able to ESC out or anything. 

It gave me a link to write down after the repair thing finished.

---

### Post by Quackers on 2012-07-04
What graphics card does your system use? You may have a small graphics problem which a boot option may get round.

---

### Post by Deeplove on 2012-07-04
Amd hd 6850

---

### Post by Quackers on 2012-07-04
You may have success with the nomodeset boot option then.
Have a look at the thread below which gives instructions for its use. Please refer to the section headed 
"How to temporarily set kernel boot options on an installed OS (not wubi)"
and follow the instructions there.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Let us know how that goes please.

---

### Post by Deeplove on 2012-07-04
Will do. BRB.

@Quackers. At the endo of the line I have $vt_handoff. Do I replace that with nomodeset?

Ok, I tried both ways. Removed $vt_handoff and left it. I keep getting the error message. Let me type this down here.

gave up waiting for root device. common problems:
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait lond enough?)
- check root= (did the system wait for the right device?)
- missing modules (cat /proc/modules; is /dev)
alert! /dev/disk/by-uuid/2fad8524-c385-493d-bf7f-5c0e3b8efadb does not exist.
Dropping to a shell

busybox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter "help" for a list of built in commands.

(initramfs)

---

### Post by Quackers on 2012-07-04
sorry, I didn't see your edit.
Is there a line that ends with "quiet splash? If so leave a space after quiet splash and type in nomodeset and then ctrl + x to boot.
If not leave a space after vt handoff and type in nomodeset and press ctrl + x to boot.

---

### Post by Deeplove on 2012-07-04
Edit. Sorry about that.

---

### Post by Quackers on 2012-07-04
Did you try it by leaving the vt handoff then after a space typing in nomodeset

---

### Post by Deeplove on 2012-07-04
Yep. Tried both ways. 

I'm sorry I'm bothering you all with my noobiness. 

:(

---

### Post by Quackers on 2012-07-04
I've not forgotten you, I'm making some enquiries :-)

---

### Post by Quackers on 2012-07-04
Deeplove, please run the Boot Repair tool again and this time make a note of the URL at the end of the run (should be a pastebin address).
Then go to that site (using a live cd/usb and select try ubuntu, if necessary) then post the whole contents of the text file you see there.
Please post those contents in code tags. To do that you need to click on New Reply (not quick reply) and then click on the # icon in the top line and then paste those contents in between the 2 code tags (where the cursor is).

It will also be useful if you will identify what hardware you are installing on.

---

### Post by Deeplove on 2012-07-05
Dang. You lost me there. Alright, let me see if I understand the # option. I copied my address last night. When I open up the Ubuntu Pastebin, there is a lot of information on there. Now, when I use the # button, that creates a window in the post where you can scroll down correct? Do I have to copy the whole pastebin or certain parts of it?

As for the hardware you're asking, is it just the internal HDD or the whole PC?

One last question. How safe is the ubuntu pastebin? Does it contain info that could affect my security on the PC? I wouldn't want to give that info out unless I was sure it's safe.

:D

---

### Post by Quackers on 2012-07-05
Ubuntu pastebin is safe.
The major components of your hardware is enough, motherboard, hard drives, graphics etc.
If you copy all of the pastebin text and then click on New Reply you get a new window. Click on the # symbol and you'll get something like [ code] then a flashing cursor, then [ /code]
right click on the cursor and select paste and the pastebin text will appear. Then click on submit post.
If you can't get that to work just post the URL of the pastebin link.

---

### Post by Deeplove on 2012-07-05
I got called in for work. When I get back I'll post it up. Sorry about that.

---

### Post by Quackers on 2012-07-05
No problem. In your own time :-)

---

### Post by Deeplove on 2012-07-05
[http://paste.ubuntu.com/1075790/](http://paste.ubuntu.com/1075790/)

 ```
  Boot Info Script 0.61-git Boot-Repair log      [4 July 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 15654 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,465,145,343 1,465,143,296   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   382,337,023   382,334,976  83 Linux
/dev/sdb2         382,339,070   390,721,535     8,382,466   5 Extended
/dev/sdb5         382,339,072   390,721,535     8,382,464  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     4,013,709     4,013,647   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6A04E0C904E098F9                       ntfs       Seagate 750GB Main
/dev/sdb1        2fad8524-ce85-493d-bf7f-5c0e3b8efadb   ext4       
/dev/sdb5        8ce0db77-6c26-4d31-bd36-a09106c8f607   swap       
/dev/sdc1        1EF9-4138                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /mnt/boot-sav/sdb1/dev   none       (rw,bind)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt/boot-sav/sdb1       ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 2fad8524-ce85-493d-bf7f-5c0e3b8efadb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 2fad8524-ce85-493d-bf7f-5c0e3b8efadb
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 2fad8524-ce85-493d-bf7f-5c0e3b8efadb
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=2fad8524-ce85-493d-bf7f-5c0e3b8efadb ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 2fad8524-ce85-493d-bf7f-5c0e3b8efadb
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=2fad8524-ce85-493d-bf7f-5c0e3b8efadb ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 2fad8524-ce85-493d-bf7f-5c0e3b8efadb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 2fad8524-ce85-493d-bf7f-5c0e3b8efadb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 6A04E0C904E098F9
	chainloader +1
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2fad8524-ce85-493d-bf7f-5c0e3b8efadb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8ce0db77-6c26-4d31-bd36-a09106c8f607 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 172.149494171 = 184.844111872  boot/grub/core.img                             1
 172.148132324 = 184.842649600  boot/grub/grub.cfg                             1
 172.190444946 = 184.888082432  boot/initrd.img-3.2.0-26-generic               1
 172.147289276 = 184.841744384  boot/vmlinuz-3.2.0-26-generic                  1
 172.190444946 = 184.888082432  initrd.img                                     1
 172.147289276 = 184.841744384  vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-07-05__02h39 ===================
boot-repair version : 3.18-0ppa35~precise
boot-sav version : 3.19-0ppa91~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 307 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , x86_64)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Seagate 750GB Main" UUID="6A04E0C904E098F9" TYPE="ntfs"
/dev/sdb1: UUID="2fad8524-ce85-493d-bf7f-5c0e3b8efadb" TYPE="ext4"
/dev/sdb5: UUID="8ce0db77-6c26-4d31-bd36-a09106c8f607" TYPE="swap"
/dev/sdc1: LABEL="PENDRIVE" UUID="1EF9-4138" TYPE="vfat"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sdb1/etc/default/grub :

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





=================== sdb1/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 25 16:07 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 18:20 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 17:57 05_debian_theme
-rwxr-xr-x 1 root root 7399 Apr 17 18:20 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 18:20 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 18:20 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 18:20 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 18:20 41_custom
-rw-r--r-- 1 root root  483 Apr 17 18:20 README




=================== sdb1recordfail=1/grub/grubenv :
recordfail=1




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	grubenv-ng	grub2,	grub-pc,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	/mnt/boot-sav/sdb1.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes

=================== parted -l:

Model: ATA ST3750528AS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  750GB  750GB  primary  ntfs         boot


Model: ATA ST3200827AS (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  196GB  196GB   primary   ext4            boot
2      196GB   200GB  4292MB  extended
5      196GB   200GB  4292MB  logical   linux-swap(v1)


Model: SanDisk U3 Cruzer Micro (scsi)
Disk /dev/sdc: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  2055MB  2055MB  primary  fat32        boot, lba


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb5 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 vga_arbiter zero
/dev/mapper:  control
/mnt/boot-sav/sda1:  09786f30351da9155a7a 1bf5fcd9af7ccb5c11d8dd8b 382d047879f4191ffa 3f1a8de7074f47d615667c141b36fc72 61a0eb1df09446d6100f AMD ASUS.000 ASUS.SYS ATI bfdf6000d92c5d28f6775437c4082ffe Boot bootmgr boot-sav BOOTSECT.BAK Config.Msi ddc81aadeea516479bf7a8954ee8 Documents and Settings dvmexp dvmexp.idx e025a1e0595584b8e3 eula.1028.txt eula.1031.txt eula.1033.txt eula.1036.txt eula.1040.txt eula.1041.txt eula.1042.txt eula.2052.txt eula.3082.txt Fraps globdata.ini HDMI.log hiberfil.sys install.exe install.ini install.res.1028.dll install.res.1031.dll install.res.1033.dll install.res.1036.dll install.res.1040.dll install.res.1041.dll install.res.1042.dll install.res.2052.dll install.res.3082.dll LU4.log msdia80.dll MSOCache N360_BACKUP pagefile.sys PerfLogs ProgramData Program Files Program Files (x86) Recovery $Recycle.Bin Riot Games splash.idx System Volume Information temp user.js Users VC_RED.cab vcredist.bmp VC_RED.MSI version Windows

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.0G  134M  1.8G   7% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      791M  764K  790M   1% /run
/dev/sdc1      vfat       2.0G  698M  1.3G  36% /cdrom
/dev/loop0     squashfs   664M  664M     0 100% /rofs
tmpfs          tmpfs      2.0G   36K  2.0G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      2.0G   76K  2.0G   1% /run/shm
/dev/sda1      fuseblk    699G  154G  546G  22% /mnt/boot-sav/sda1
/dev/sdb1      ext4       183G  5.2G  168G   3% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc15c3cdf

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1465145343   732571648    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003f29d

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   382337023   191167488   83  Linux
/dev/sdb2       382339070   390721535     4191233    5  Extended
/dev/sdb5       382339072   390721535     4191232   82  Linux swap / Solaris

Disk /dev/sdc: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     4013709     2006823+   c  W95 FAT32 (LBA)


User choice: Is sdb (200GB) a removable disk? no

=================== Recommended repair
recommendedrepair
This setting will reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
Additional repair will be performed: unhide-bootmenu


Reinstall the GRUB of sdb1 into all MBRs of disks with OS or not-USB
Already mounted /dev/sdb1 on /mnt/boot-sav/sdb1
Reinstall the GRUB of sdb1 into the MBR of sda
chroot /mnt/boot-sav/sdb1 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
grub-install (GRUB) 1.99-21ubuntu3
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0
Reinstall the GRUB of sdb1 into the MBR of sdb
chroot /mnt/boot-sav/sdb1 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
grub-install (GRUB) 1.99-21ubuntu3
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0
umount: /mnt/boot-sav/sdb1/dev: device is busy.
(In some cases useful info about processes that use
the device is found by lsof(8) or fuser(1))
Unhide GRUB boot menu in sdb1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (200GB) disk!
pastebinit  packages needed
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: unable to re-open stdin: No such file or directory
```

---

### Post by Quackers on 2012-07-06
Thanks elfy :-)
Deeplove, can I just clarify some things please?
Your bios is set to boot from the second hard drive first?
Your current boot process stops at a black screen?
No "alert - /dev/disk error with a long string of numbers any more?

---

### Post by Deeplove on 2012-07-06
IIRC the 2nd HDD that has Ubuntu doesn't shot up on my selection for boot up. My USB, main HDD and optical drive comes up but not the 2nd HDD.

/dev/disk/by-uuid/2fad8524-ce85-493d-bf7f-5c0e3b8efadb 
Does not exist

That's what the black screen says.

---

### Post by Quackers on 2012-07-06
Deeplove can you try this for me please?
On booting the system keep tapping the shift key to bring up the grub menu.
The top item in that menu should be your Ubuntu installation and it will be highlighted.
Press the "e" key and the new screen will appear.
Using the arrow keys navigate to the end of the kernel line which currently ends with $vt handoff
Leave a space after $vt handoff and type this in please ```
nomodeset rootdelay=30
``` leaving a space between the two parameters. 
Then press ctrl + x to boot.

The rootdelay parameter will give grub more time to find the disk.

---

### Post by Deeplove on 2012-07-06
Alright, tried that out also and nothing. I'm running Ubuntu off my flash drive right now. I'm really stumped. I tried reinstalling it again manually and still nothing. I'm just about ready to give up but don't want to.

---

### Post by Quackers on 2012-07-07
It might help if you are a little more decsriptive than just saying nothing happened :-)
What exactly happened when you tried the above kernel changes? Did it just go to a black screen? A purple screen? Did you still get the /dev/disk alert?

---

### Post by Deeplove on 2012-07-07
Sorry. I just noticed that I didn post the errors and all. Lol. It was 3am when I went to sleep last night trying to reinstall and get it to work. Well, I'm at work now and will get home around 9pm eastern just to jump on the PC again. I took pictures of the error. 

The same error. 

gave up waiting for root device. common problems:
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait lond enough?)
- check root= (did the system wait for the right device?)
- missing modules (cat /proc/modules; is /dev)
alert! /dev/disk/by-uuid/2fad8524-c385-493d-bf7f-5c0e3b8efadb does not exist.
Dropping to a shell

busybox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter "help" for a list of built in commands.

(initramfs)

Now, I do have the 2hdd booting up first so I get the selection screen every time I boot now. When I get home I'll be able to get more info for you.

---

### Post by Quackers on 2012-07-07
Ok thanks Deeplove.
I can see no reason why your disk is not being found by grub. I have asked another member to take a look at things and see if he can make any further suggestions or spot anything I may have missed.

---

### Post by madjr on 2012-07-07
if everything else fails, you can try wubi:

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

this is how am running it on one of my computers.

but of course the install to own partition is usually optimum route to try first.

---

### Post by kansasnoob on 2012-07-07
I know a lot of this is probably a repeat of a repeat but bear with me :)

I think you're using a live USB to install, but even if it is a live CD/DVD let's get real basic. When you first boot the live device and the two small emblems appear at the bottom of the screen please press a key. That should display the ability to select the desired language followed by the full live boot menu.

From that menu please select "Check disc for defects". That'll take a few minutes to complete. Let's **make sure it says no errors found**. If so then boot to the live DE and post the output of these commands:

```
cat /proc/cpuinfo
```

```
lspci | grep VGA
```

```
free -m
```

That just provides some rather specific hardware info, but also post a new boot info summary - no need to run boot repair first but it's always best to start with fresh info ;)

---

### Post by kansasnoob on 2012-07-07
> **Quackers said:**
> Ok thanks Deeplove.
I can see no reason why your disk is not being found by grub. I have asked another member to take a look at things and see if he can make any further suggestions or spot anything I may have missed.

I'm not that other member but I'm curious and it's too hot to do anything outside ;)

---

### Post by kedarlasane on 2012-07-07
To install Ubuntu is very simple than to install windows.At one time it is hard to install linux on our system but now it is very user friendly.Just install Ubuntu disk in which you burned your .ISO image which you downloaded from [ubuntu .org]("http://www.ubuntu%20.org") .Then Follow the instruction displayed by your screen Finally you gotta a OS on your system.Any problems or questions will be asked here related to installing ubuntu
-------------------------------------------------------------------------------------------------------------------
**Kedar**
[http://www.tuljabhavani.in]("http://www.tuljabhavani.in/")

---

### Post by drs305 on 2012-07-07
I think you are now getting the Grub menu at boot? If so, please try the following to see if GRUB can see all the files before Ubuntu or Windows boots:

Press 'c' to get to the grub prompt, then:
```

ls (hd1,5)/  # Does it see the normal Ubuntu folders, and *vmlinuz* and *initrd.img*
ls (hd1,5)/boot #  *vmlinuz-3.2.0-26-generic* & *initrd.img-3.2.0-26-generic*
ls (hd1,5)/boot/grub # Lots of *.mod files
```

**Added:**
```
ls (hd1,5)/etc/fstab
```

If you are getting the grub menu it should be seeing the grub.cfg file, but I'm curious if it's finding all the others.

Everything looks normal in the boot info script results as far as I saw. It' possible GRUB and BIOS aren't seeing one or more files before an OS boots. The files would be seen after an OS takes over, which is why we are searching the disk before the boot.

---

### Post by Deeplove on 2012-07-07
```
         Boot Info Script 0.61-git Boot-Repair log      [4 July 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 15654 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,465,145,343 1,465,143,296   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   390,719,487   390,717,440  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     4,013,709     4,013,647   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6A04E0C904E098F9                       ntfs       Seagate 750GB Main
/dev/sdb1        e74aec81-4f76-4d6b-8b10-d5a471c7429e   ext4       
/dev/sdc1        1EF9-4138                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /mnt/boot-sav/sdb1/dev   none       (rw,bind)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt/boot-sav/sdb1       ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root e74aec81-4f76-4d6b-8b10-d5a471c7429e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root e74aec81-4f76-4d6b-8b10-d5a471c7429e
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root e74aec81-4f76-4d6b-8b10-d5a471c7429e
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=e74aec81-4f76-4d6b-8b10-d5a471c7429e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root e74aec81-4f76-4d6b-8b10-d5a471c7429e
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=e74aec81-4f76-4d6b-8b10-d5a471c7429e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root e74aec81-4f76-4d6b-8b10-d5a471c7429e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root e74aec81-4f76-4d6b-8b10-d5a471c7429e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 6A04E0C904E098F9
	chainloader +1
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e74aec81-4f76-4d6b-8b10-d5a471c7429e /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.135818481 = 15.178219520   boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
  14.144500732 = 15.187542016   boot/initrd.img-3.2.0-26-generic               1
  14.134498596 = 15.176802304   boot/vmlinuz-3.2.0-26-generic                  1
  14.144500732 = 15.187542016   initrd.img                                     1
  14.134498596 = 15.176802304   vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-07-07__02h42 ===================
boot-repair version : 3.18-0ppa39~precise
boot-sav version : 3.19-0ppa99~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 309 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , x86_64)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Seagate 750GB Main" UUID="6A04E0C904E098F9" TYPE="ntfs"
/dev/sdb1: UUID="e74aec81-4f76-4d6b-8b10-d5a471c7429e" TYPE="ext4"
/dev/sdc1: LABEL="PENDRIVE" UUID="1EF9-4138" TYPE="vfat"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.



=================== sdb1/etc/default/grub :

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





=================== sdb1/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 25 16:07 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 18:20 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 17:57 05_debian_theme
-rwxr-xr-x 1 root root 7399 Apr 17 18:20 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 18:20 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 18:20 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 18:20 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 18:20 41_custom
-rw-r--r-- 1 root root  483 Apr 17 18:20 README




=================== sdb1recordfail=1/grub/grubenv :
recordfail=1




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	grubenv-ng	grub2,	grub-pc,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	/mnt/boot-sav/sdb1.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes

=================== parted -l:

Model: ATA ST3750528AS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  750GB  750GB  primary  ntfs         boot


Model: ATA ST3200827AS (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  200GB  200GB  primary  ext4         boot


Model: SanDisk U3 Cruzer Micro (scsi)
Disk /dev/sdc: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  2055MB  2055MB  primary  fat32        boot, lba


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 vga_arbiter zero
/dev/mapper:  control
/mnt/boot-sav/sda1:  09786f30351da9155a7a 1bf5fcd9af7ccb5c11d8dd8b 382d047879f4191ffa 3f1a8de7074f47d615667c141b36fc72 61a0eb1df09446d6100f AMD ASUS.000 ASUS.SYS ATI bfdf6000d92c5d28f6775437c4082ffe Boot bootmgr boot-sav BOOTSECT.BAK Config.Msi ddc81aadeea516479bf7a8954ee8 Documents and Settings dvmexp dvmexp.idx e025a1e0595584b8e3 eula.1028.txt eula.1031.txt eula.1033.txt eula.1036.txt eula.1040.txt eula.1041.txt eula.1042.txt eula.2052.txt eula.3082.txt Fraps globdata.ini HDMI.log hiberfil.sys install.exe install.ini install.res.1028.dll install.res.1031.dll install.res.1033.dll install.res.1036.dll install.res.1040.dll install.res.1041.dll install.res.1042.dll install.res.2052.dll install.res.3082.dll LU4.log msdia80.dll MSOCache N360_BACKUP pagefile.sys PerfLogs ProgramData Program Files Program Files (x86) Recovery $Recycle.Bin Riot Games splash.idx System Volume Information temp user.js Users VC_RED.cab vcredist.bmp VC_RED.MSI version Windows

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.0G  170M  1.8G   9% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      791M  756K  790M   1% /run
/dev/sdc1      vfat       2.0G  698M  1.3G  36% /cdrom
/dev/loop0     squashfs   664M  664M     0 100% /rofs
tmpfs          tmpfs      2.0G   32K  2.0G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      2.0G   80K  2.0G   1% /run/shm
/dev/sda1      fuseblk    699G  150G  550G  22% /mnt/boot-sav/sda1
/dev/sdb1      ext4       187G  5.2G  172G   3% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc15c3cdf

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1465145343   732571648    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003f29d

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   390719487   195358720   83  Linux

Disk /dev/sdc: 2055 MB, 2055019520 bytes
16 heads, 63 sectors/track, 3981 cylinders, total 4013710 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     4013709     2006823+   c  W95 FAT32 (LBA)


User choice: Is sdb (200GB) a removable disk? no

=================== Recommended repair
recommendedrepair
This setting will reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
Additional repair will be performed: unhide-bootmenu


Reinstall the GRUB of sdb1 into all MBRs of disks with OS or not-USB
Already mounted /dev/sdb1 on /mnt/boot-sav/sdb1
Reinstall the GRUB of sdb1 into the MBR of sda
chroot /mnt/boot-sav/sdb1 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
grub-install (GRUB) 1.99-21ubuntu3
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0
Reinstall the GRUB of sdb1 into the MBR of sdb
chroot /mnt/boot-sav/sdb1 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
grub-install (GRUB) 1.99-21ubuntu3
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0
umount: /mnt/boot-sav/sdb1/dev: device is busy.
(In some cases useful info about processes that use
the device is found by lsof(8) or fuser(1))
Unhide GRUB boot menu in sdb1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (200GB) disk!
pastebinit  packages needed
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: unable to re-open stdin: No such file or directory
 
```

I believe that's the last one I got. I'm able to boot off the grub thing. But once I select the first option to boot off that's when I get the error I usually get. I'll be home later on and will post the issues. Sorry, I'm at work now.

---

### Post by kansasnoob on 2012-07-07
I'm particularly curious about this:

> pastebinit  packages needed
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: **unable to re-open stdin: No such file or directory**

If the installation media is failing to provide the proper grub packages we need to know why :confused:

OTOH we could use wget and dpkg to install the proper grub packages through a chroot but that seems ridiculous with a fresh install :(

Does anything I say make sense?

---

### Post by Deeplove on 2012-07-07
Dang forgot to post my rig also. 

Phenom iix2 555 be
Asus m4a785td v evo mobo
4gb ram
Amd hd 6850
550w psu
HDD 750gb win7
HDD 200gb Ubuntu 

Yes. Fresh install of Ubuntu on the 200gb HDD. That's what I want.

---

### Post by Deeplove on 2012-07-08
> **drs305 said:**
> I think you are now getting the Grub menu at boot? If so, please try the following to see if GRUB can see all the files before Ubuntu or Windows boots:

Press 'c' to get to the grub prompt, then:
```

ls (hd1,5)/  # Does it see the normal Ubuntu folders, and *vmlinuz* and *initrd.img*
ls (hd1,5)/boot #  *vmlinuz-3.2.0-26-generic* & *initrd.img-3.2.0-26-generic*
ls (hd1,5)/boot/grub # Lots of *.mod files
```

**Added:**
```
ls (hd1,5)/etc/fstab
```

If you are getting the grub menu it should be seeing the grub.cfg file, but I'm curious if it's finding all the others.

Everything looks normal in the boot info script results as far as I saw. It' possible GRUB and BIOS aren't seeing one or more files before an OS boots. The files would be seen after an OS takes over, which is why we are searching the disk before the boot.


Don't know what I need to do, buy pressing c gets me to gnu grub version 1.99-21ubuntu3 screen. Minimal bash editing.


> **madjr said:**
> if everything else fails, you can try wubi:

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

this is how am running it on one of my computers.

but of course the install to own partition is usually optimum route to try first.

If I do it this way, then I'd have to reformat my 2nd HDD right? I don't want to use my main HDD which has Win7.


> **kansasnoob said:**
> I know a lot of this is probably a repeat of a repeat but bear with me :)

I think you're using a live USB to install, but even if it is a live CD/DVD let's get real basic. When you first boot the live device and the two small emblems appear at the bottom of the screen please press a key. That should display the ability to select the desired language followed by the full live boot menu.

From that menu please select "Check disc for defects". That'll take a few minutes to complete. Let's **make sure it says no errors found**. If so then boot to the live DE and post the output of these commands:

```
cat /proc/cpuinfo
```

```
lspci | grep VGA
```

```
free -m
```

That just provides some rather specific hardware info, but also post a new boot info summary - no need to run boot repair first but it's always best to start with fresh info ;)

I don't recall seeing two items on the bottom when installing. I have Win7 x64. Did I download the wrong one?


Probably a dumb question but let me try anyways. When I run the live USB to install and when done installing, when I run the Boot Repair...

does it only fix the live USB ubuntu or the HDD ubuntu? 

reason I ask because when I reset the live ubuntu seems to reset everything with it. So where does that boot repair save onto? i hope i'm not confusing you all.

---

### Post by kansasnoob on 2012-07-08
First of all in no way confuse what I said with what drs305 is saying. He knows grub much, much better than I do :)

What he is recommending here is a series of things to try when attempting to boot the installed OS:

> I think you are now getting the Grub menu at boot? If so, please try the following to see if GRUB can see all the files before Ubuntu or Windows boots:

Press 'c' to get to the grub prompt, then:
Code:

ls (hd1,5)/  # Does it see the normal Ubuntu folders, and vmlinuz and initrd.img
ls (hd1,5)/boot #  vmlinuz-3.2.0-26-generic & initrd.img-3.2.0-26-generic
ls (hd1,5)/boot/grub # Lots of *.mod files

Added:
Code:

ls (hd1,5)/etc/fstab

If you are getting the grub menu it should be seeing the grub.cfg file, but I'm curious if it's finding all the others.

Everything looks normal in the boot info script results as far as I saw. It' possible GRUB and BIOS aren't seeing one or more files before an OS boots. The files would be seen after an OS takes over, which is why we are searching the disk before the boot.

I was thinking from a different angle altogether, looking at this purely as a failed installation since in post #22 you said you'd tried another fresh install, so I wanted you to test your live installation media for errors. When you boot the live USB you should very briefly see two small icons at the bottom of the screen (indicating a human and a keyboard). You have about 3 seconds when those appear to press a key which will then cause the language selection screen to appear followed by the boot menu. Then just select Check disc for defects which takes several minutes to complete.

The other commands I included simply provide some more specific hardware info :)

---

### Post by kansasnoob on 2012-07-08
This shows what I'm talking about:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I just wanted to rule out bad installation media. I've been doing iso-testing since 8.04 and I've more than once encountered bad installation media for no apparent reason ;)

---

### Post by drs305 on 2012-07-08
*kansasnoob's* approach tackles a bad installation. Normally Grub will leave you at a "grub" or "grub rescue" prompt. Having a "GRUB loading" message with nothing else could very well be a bad installation. I thought his advice would fix your issue and I was surprised that purging and reinstalling GRUB didn't fix the problem if that was the case. If the purge/reinstallation was done by pulling the packages off the Internet the packages should have been re-downloaded after the purge and should be correct. If somehow you were able to reinstall GRUB using packages from the CD/USB then you may have simply reinstalled a defective package.

> 	
Don't know what I need to do, buy pressing c gets me to gnu grub version 1.99-21ubuntu3 screen. Minimal bash editing.

The commands I gave you (the "ls" commands) were to be run from the "grub" prompt, which you got when you pressed "c". Grub 2 allows some command line operations for troubleshooting purposes, so when you get to the prompt you run the commands. 

The "ls" commands will search the specific partition/folders for the files to see if GRUB can locate them. There may be a combination of missing files and/or modules that leads to what you are getting, and that is the  purpose of running the commands.

---

### Post by Deeplove on 2012-07-08
Oh ok. Now the noob question comes in.

When I'm at that Grub prompt, do I type down the whole ls commands together just like you typed it?

---

### Post by drs305 on 2012-07-08
> **Deeplove said:**
> Oh ok. Now the noob question comes in.

When I'm at that Grub prompt, do I type down the whole ls commands together just like you typed it?

You don't have to include the # symbol and what follows. Anything after the # symbol is a comment and not acted upon. I just put it there to explain what you would look for.

Also, it's possible the system before booting may see the drives differently. So if (hd1,5) doesn't work, try (hd0,5) or if you have externals connected (hd2,5), etc.

---

### Post by Quackers on 2012-07-08
One at a time. Each command will give an output. Check each output for the files drs305 outlined earlier.

---

### Post by Deeplove on 2012-07-09
Well everyone...with the frustration that this install gave me I ended up tossing it. I was too much trouble trying to get it to work. 

But...

I went with Mint and that thing installed instantly. I did the same process and it installed normally. Don't know how much of a difference Mint is to Ubuntu. But it's working. 

I greatly appreciate you all that helped me out. Maybe once I get used to mint I'll give Ubuntu another go at it. But for now Mint has me happy. Messed around with it all weekend long.

Linux is something else. I guess I have to sit down and gather information and get used to it. But I like it. Different. Once again thanks and if someone can change it to resolved then that would be great.

:D

---

### Post by drs305 on 2012-07-09
Congratulations on getting a working Linux OS. Mint is very well liked by many users and in learning Mint you will be 'learning' Ubuntu as well.

If you don't have any other issues regarding the original post, would you please mark the thread SOLVED so helpers no longer feel the need to visit this thread. If you feel the tag is misleading just add a note to the first post that you abandoned Ubuntu and installed Mint...

Happy Mint-ing !

---

