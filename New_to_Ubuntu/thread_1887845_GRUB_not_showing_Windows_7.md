---
title: "GRUB not showing Windows 7"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by BJones007 on 2011-11-28
I recently did a dual boot with Windows 7 and was unable to login to Ubuntu afterwards cos apparently the Windows boot MGR took precedence. After running the LiveUSB i reinstalled GRUB and is now back on Ubuntu, but whenever I restart Windows 7 is not in the boot menu. I ran the command ```
 sudo fdisk -l 
```

 and got this 

```
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a0d38ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    14683409     7341673+  12  Compaq diagnostics
/dev/sda2        14684160   164157439    74736640   83  Linux
/dev/sda3   *   164161536   306628607    71233536    7  HPFS/NTFS/exFAT
/dev/sda4       306630654   312580095     2974721    5  Extended
/dev/sda5       306630656   312580095     2974720   82  Linux swap / Solaris 
```

I also ran ```
 sudo os-prober 
```

and got ```
 /dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda3:Windows 7 (loader):Windows1:chain 
```


and now I'm not sure what else to do. I had a previous installation of Ubuntu on the partition /dev/sda3 and in GRUB it's still there. Help please.

---

### Post by crazy bird on 2011-11-28
Try this commando in a terminal:**sudo update-grub**.

---

### Post by BJones007 on 2011-11-28
> **crazy bird said:**
> Try this commando in a terminal:**sudo update-grub**.
I tried that as well, but it didn't fix the problem

---

### Post by bluexrider on 2011-11-28
use gparted and change your boot flag from sda3 to sda2 then run 
sudo update-grub

---

### Post by Miljet on 2011-11-28
Something doesn't sound right here.  You say that you had another version of Ubuntu on sda3, but that partition now seems to hold Win 7.  I have a hunch that you mistakenly installed Grub to sda2 instead of sda, and what you are seeing is the old Grub that is installed in the MBR of the disk.

I think you should run the Boot Info Script and post the results here. You can find it here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by BJones007 on 2011-11-28
I'm not sure if I shoulda left sup'm out so I pasted the entire thing 

```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    14,683,409    14,683,347  12 Compaq diagnostics
/dev/sda2          14,684,160   164,157,439   149,473,280  83 Linux
/dev/sda3    *    164,161,536   306,628,607   142,467,072   7 NTFS / exFAT / HPFS
/dev/sda4         306,630,654   312,580,095     5,949,442   5 Extended
/dev/sda5         306,630,656   312,580,095     5,949,440  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E66849FD6849CD4D                       ntfs       PQSERVICE
/dev/sda2        214f8c70-3789-447d-bbac-5db9ae7f3a2b   ext4       Ubuntu
/dev/sda3        4C24000879C0FEBC                       ntfs       Windows 7
/dev/sda5        2ebf551b-79b4-4c7e-9ef5-6681621202d8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=214f8c70-3789-447d-bbac-5db9ae7f3a2b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-12-generic
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro quiet splash 
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro  single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 11.10, kernel 2.6.38-11-generic
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro quiet splash 
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro  single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.10, kernel 2.6.38-10-generic
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-2.6.38-10-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro quiet splash 
initrd		/boot/initrd.img-2.6.38-10-generic

title		Ubuntu 11.10, kernel 2.6.38-10-generic (recovery mode)
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-2.6.38-10-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro  single
initrd		/boot/initrd.img-2.6.38-10-generic

title		Ubuntu 11.10, kernel 2.6.38-8-generic
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.10, kernel 2.6.38-8-generic (recovery mode)
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/grub/core.img

title		Ubuntu 11.10, memtest86+
uuid		214f8c70-3789-447d-bbac-5db9ae7f3a2b
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 214f8c70-3789-447d-bbac-5db9ae7f3a2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 214f8c70-3789-447d-bbac-5db9ae7f3a2b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 214f8c70-3789-447d-bbac-5db9ae7f3a2b
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 214f8c70-3789-447d-bbac-5db9ae7f3a2b
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 214f8c70-3789-447d-bbac-5db9ae7f3a2b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 214f8c70-3789-447d-bbac-5db9ae7f3a2b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root E66849FD6849CD4D
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 77c14a19-9da9-4208-a701-4c941bff79b5
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 77c14a19-9da9-4208-a701-4c941bff79b5
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=214f8c70-3789-447d-bbac-5db9ae7f3a2b /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=2ebf551b-79b4-4c7e-9ef5-6681621202d8 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda2/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/initrd.img-2.6.38-10-generic              2
               =                boot/initrd.img-2.6.38-11-generic              3
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-13-generic               4
               =                boot/vmlinuz-2.6.38-10-generic                 2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  2
               =                initrd.img                                     4
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

================= sda2: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

               =                boot/extlinux/chain.c32                        1
               =                boot/extlinux/extlinux.conf                    1

============== sda2: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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
 
```

---

### Post by lolpenguin on 2011-11-29
Did you install Ubuntu using Wubi? The Windows entry is disabled in GRUB if Wubi is being used. The output of update-grub will indicate it.
```
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
done
```

---

### Post by BJones007 on 2011-11-29
No I didn't use Wubi. Here's what I got after I update-grub: ```
 Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.0.0-13-generic
Found kernel: /boot/vmlinuz-3.0.0-12-generic
Found kernel: /boot/vmlinuz-2.6.38-11-generic
Found kernel: /boot/vmlinuz-2.6.38-10-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
 
```

---

### Post by BJones007 on 2011-11-30
Bump

---

### Post by oldfred on 2011-11-30
Somehow you have grub legacy's menu.lst. It is the one getting updated, but you are booting with grub2 and grub2's grub.cfg is not getting updated.

It would be best to totally uninstall both grub & grub2 and cleanly reinstall grub2. Besure to have Internet connection as it has to download the grub2 package again or you will not be able to reboot.

# uninstall both grub legacy & grub2 reinstall grub2 and to sda, sudo required if not chrooted:
sudo -i
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda



More info here, but if you can boot you do not have to chroot into your system and the above commands should be all you need.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by BJones007 on 2011-11-30
> **oldfred said:**
> Somehow you have grub legacy's menu.lst. It is the one getting updated, but you are booting with grub2 and grub2's grub.cfg is not getting updated.

It would be best to totally uninstall both grub & grub2 and cleanly reinstall grub2. Besure to have Internet connection as it has to download the grub2 package again or you will not be able to reboot.

# uninstall both grub legacy & grub2 reinstall grub2 and to sda, sudo required if not chrooted:
sudo -i
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda



More info here, but if you can boot you do not have to chroot into your system and the above commands should be all you need.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Thanks it actually worked :D

---

### Post by gatech on 2012-03-19
Hey so I am having the same problem except when I update-grub I get:

Found Windows 7 (loader) on /dev/sda2
Skipping Windows 7 (loader) on Wubi system

I have been working on this problem for a few weeks now and am a complete noob at ubuntu. I would appreciate any help.

---

### Post by Toronto11 on 2012-03-21
I was hoping to get some help with a dual boot as well.

I have a hardrive with Ubuntu and one with W7 and all was working well, but I have upgraded the Ubuntu and now when the computer starts it goes right to Ubuntu without giving me the option to select W7.  Previously if I did nothing at bootup Ubuntu would load by default.  This is what I'd like to have again.  

No BIOS options seemed to help.

Thanks.

---

### Post by Mark Phelps on 2012-03-22
> **gatech said:**
> Hey so I am having the same problem except when I update-grub I get:

Found Windows 7 (loader) on /dev/sda2
Skipping Windows 7 (loader) on Wubi system

I have been working on this problem for a few weeks now and am a complete noob at ubuntu. I would appreciate any help.

You're running Wubi -- which boots Ubuntu using a file installed on a Windows NTFS partition.  If you were able to boot from there into Windows, you would have a circular booting problem.

If all you're trying to do is access the Windows files from inside Ubuntu, then look under /host in your filesystem.

---

### Post by Mark Phelps on 2012-03-22
> **Toronto11 said:**
> I was hoping to get some help with a dual boot as well.

I have a hardrive with Ubuntu and one with W7 and all was working well, but I have upgraded the Ubuntu and now when the computer starts it goes right to Ubuntu without giving me the option to select W7.  Previously if I did nothing at bootup Ubuntu would load by default.  This is what I'd like to have again.  

No BIOS options seemed to help.

Thanks.

When you upgraded Ubuntu, it rewrote the default GRUB config file -- wiping out any previous reference to Windows.

Go back into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config file, should find Windows on your PC, and will add entries for it.

When you reboot, you will see a GRUB menu again.

---

