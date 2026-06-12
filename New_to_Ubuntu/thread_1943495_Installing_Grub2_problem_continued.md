---
title: "Installing Grub2 problem continued"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-19
Have completed reinstall of grub using the suggested LiveCD method. I discovered during the process that using / as mount point is BAD! Which maybe be the reason I get the Error Message NO BOOTLOADER FOUND when I try to install Grub2.
Question: Is it possible to change the mount point to /home without having to reinstall everything again?
Am using Ubuntu Lucid on a single HD, & WindowsXP on a separate HD.

---

### Post by idoitprone on 2012-03-19
> **Bumpalot said:**
> Have completed reinstall of grub using the suggested LiveCD method. I discovered during the process that using / as mount point is BAD! Which maybe be the reason I get the Error Message NO BOOTLOADER FOUND when I try to install Grub2.
Question: Is it possible to change the mount point to /home without having to reinstall everything again?
Am using Ubuntu Lucid on a single HD, & WindowsXP on a separate HD.


hmmmmmmm it seems that you install ubuntu ok, but reinstall grub badly.

/ should be the mount point

please run the boot script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I cannot help you further since i have class soon and i;m dizzy

---

### Post by ajgreeny on 2012-03-19
> **Bumpalot said:**
> Have completed reinstall of grub using the suggested LiveCD method. I discovered during the process that using / as mount point is BAD! Which maybe be the reason I get the Error Message NO BOOTLOADER FOUND when I try to install Grub2.
Question: Is it possible to change the mount point to /home without having to reinstall everything again?
Am using Ubuntu Lucid on a single HD, & WindowsXP on a separate HD.
Using / (root) as mountpoint is not bad; you can not do anything if you do not allocate a partition to mountpoint / as that is the actual operating system partition.  However, I am not sure why you should have needed any of that when re-installing grub.

Can you tell us in more detail what exactly you did and what is now happening.  It may be that you tried to install grub to a partition and not the mbr of a disk, ie it should be on /dev/sda and not on /dev/sda#.  I have reinstalled grub in the past with ease, so I know that it can work; I wonder what you did that is causing the problem.

More information please.

---

### Post by Bumpalot on 2012-03-19
Where I got the info that installing grub on / is this Terminal section from my grub install:
"Setting up grub-pc (1.98-1ubuntu13) ...
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done"
The main reason I reinstalled grub was that I cannot start Grub2 customizer - I get the popup msg "No Bootloader found
Do you want to select another root partition?"
Selected NO. This is what I am trying to rectify.
See my previous thread #  for details SOLVED Grub2 problem -about 2 hrs ago.
My drive is /dev/sdd, mounted on / which may be the problem, so I would like to know if I can change the mount point to /home without re-installation.
I guess I should have set MBR to /home.
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdd1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdd1 and looks at sector 891078656 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 1 for /boot/grub.
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   625,137,344   625,137,282   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   956,966,911   956,964,864  83 Linux
/dev/sdd2         956,968,958   976,773,119    19,804,162   5 Extended
/dev/sdd5         956,968,960   976,773,119    19,804,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        06948A49948A3B67                       ntfs       Pagefile
/dev/sdb1        0EBC8528BC850B81                       ntfs       
/dev/sdd1        364e7c25-ae53-4a14-abfc-2f64396c0299   ext3       
/dev/sdd5        2ddbc5e5-b123-487c-84c8-ff9d123bd397   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext3       (rw,errors=remount-ro)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    linux    /boot/vmlinuz-2.6.32-39-generic root=UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-39-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    echo    'Loading Linux 2.6.32-39-generic ...'
    linux    /boot/vmlinuz-2.6.32-39-generic root=UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-39-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 364e7c25-ae53-4a14-abfc-2f64396c0299
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/30_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0EBC8528BC850B81
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=364e7c25-ae53-4a14-abfc-2f64396c0299 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2ddbc5e5-b123-487c-84c8-ff9d123bd397 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 424.899440765 = 456.232300544  boot/grub/core.img                             1
 424.933532715 = 456.268906496  boot/grub/grub.cfg                             1
 424.958713531 = 456.295944192  boot/initrd.img-2.6.32-28-generic              4
 424.985420227 = 456.324620288  boot/initrd.img-2.6.32-38-generic              5
 424.899524689 = 456.232390656  boot/initrd.img-2.6.32-39-generic              7
 424.945152283 = 456.281382912  boot/vmlinuz-2.6.32-28-generic                 2
 424.882514954 = 456.214126592  boot/vmlinuz-2.6.32-38-generic                 2
 424.888378143 = 456.220422144  boot/vmlinuz-2.6.32-39-generic                 2
 424.899524689 = 456.232390656  initrd.img                                     7
 424.985420227 = 456.324620288  initrd.img.old                                 5
 424.888378143 = 456.220422144  vmlinuz                                        2
 424.882514954 = 456.214126592  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdd2

00000000  8d 1a 30 c3 00 00 00 01  0f 1b 7e 1f 68 d1 a3 0c  |..0.......~.h...|
00000010  36 8d 1a 34 61 86 d1 a3  46 8c 30 da 34 68 d1 86  |6..4a...F.0.4h..|
00000020  1b 46 8d 1a 30 c3 68 d1  a3 46 18 6d 1a 34 68 c3  |.F..0.h..F.m.4h.|
00000030  0d a3 46 8d 18 61 b4 68  d1 a3 0c 36 8d 1a 34 61  |..F..a.h...6..4a|
00000040  86 d1 a3 46 8c 30 da 34  68 d1 86 1b 46 8d 1a 30  |...F.0.4h...F..0|
00000050  c3 68 d1 a3 46 18 6d 1a  34 68 c3 0d a3 46 8d 18  |.h..F.m.4h...F..|
00000060  61 b4 68 d1 a3 0c 36 8d  1a 34 61 86 d1 a3 46 8c  |a.h...6..4a...F.|
00000070  30 da 34 68 d1 86 1b 46  8d 1a 30 c3 68 d1 a3 46  |0.4h...F..0.h..F|
00000080  18 6d 1a 34 68 c3 0d a3  46 8d 18 61 b4 68 d1 a3  |.m.4h...F..a.h..|
00000090  0c 36 8d 1a 34 61 86 d1  a3 46 8c 30 da 34 68 d1  |.6..4a...F.0.4h.|
000000a0  86 1b 46 8d 1a 30 c3 68  d1 a3 46 18 6d 1a 34 68  |..F..0.h..F.m.4h|
000000b0  c3 0d a3 46 8d 18 61 b4  68 d1 a3 0c 36 8d 1a 34  |...F..a.h...6..4|
000000c0  61 86 d1 a3 46 8c 30 da  34 68 d1 86 1b 46 8d 1a  |a...F.0.4h...F..|
000000d0  30 c3 68 d1 a3 46 18 6d  1a 34 68 c3 0d a3 46 8d  |0.h..F.m.4h...F.|
000000e0  18 61 b4 68 d1 a3 0c 36  8d 1a 34 61 86 d1 a3 46  |.a.h...6..4a...F|
000000f0  8c 30 da 34 68 d1 86 1b  46 8d 1a 30 c3 00 00 00  |.0.4h...F..0....|
00000100  01 10 1b 7e 1f 68 d1 a3  0c 36 8d 1a 34 61 86 d1  |...~.h...6..4a..|
00000110  a3 46 8c 30 da 34 68 d1  86 1b 46 8d 1a 30 c3 68  |.F.0.4h...F..0.h|
00000120  d1 a3 46 18 6d 1a 34 68  c3 0d a3 46 8d 18 61 b4  |..F.m.4h...F..a.|
00000130  68 d1 a3 0c 36 8d 1a 34  61 86 d1 a3 46 8c 30 da  |h...6..4a...F.0.|
00000140  34 68 d1 86 1b 46 8d 1a  30 c3 68 d1 a3 46 18 6d  |4h...F..0.h..F.m|
00000150  1a 34 68 c3 0d a3 46 8d  18 61 b4 68 d1 a3 0c 36  |.4h...F..a.h...6|
00000160  8d 1a 34 61 86 d1 a3 46  8c 30 da 34 68 d1 86 1b  |..4a...F.0.4h...|
00000170  46 8d 1a 30 c3 68 d1 a3  46 18 6d 1a 34 68 c3 0d  |F..0.h..F.m.4h..|
00000180  a3 46 8d 18 61 b4 68 d1  a3 0c 36 8d 1a 34 61 86  |.F..a.h...6..4a.|
00000190  d1 a3 46 8c 30 da 34 68  d1 86 1b 46 8d 1a 30 c3  |..F.0.4h...F..0.|
000001a0  68 d1 a3 46 18 6d 1a 34  68 c3 0d a3 46 8d 18 61  |h..F.m.4h...F..a|
000001b0  b4 68 d1 a3 0c 36 8d 1a  34 61 86 d1 a3 46 00 fe  |.h...6..4a...F..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 2e 01 00 00  |...........0....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sde 

Hope this sheds some light on my predicament! Thanks so much for your interest & help.

---

### Post by critin on 2012-03-19
> **ajgreeny said:**
> Using / (root) as mountpoint is not bad; you can not do anything if you do not allocate a partition to mountpoint / as that is the actual operating system partition.  However, I am not sure why you should have needed any of that when re-installing grub.

Can you tell us in more detail what exactly you did and what is now happening.  It may be that you tried to install grub to a partition and not the mbr of a disk, ie it should be on /dev/sda and not on /dev/sda#.  I have reinstalled grub in the past with ease, so I know that it can work; I wonder what you did that is causing the problem.

More information please.

 **ajgreeny** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11778519#post11778519")

I believe there is confusion in whether to install grub to "mount point'  / or disk.

This might help, same poster, same issue. [http://ubuntuforums.org/showthread.php?t=1942876](http://ubuntuforums.org/showthread.php?t=1942876)

Particularly post # 9.

For example, should be installing to sda (HD) not sda/2. (mount point) (Partition) (this may not have happened, but it does get convoluted)

---

### Post by Bumpalot on 2012-03-19
This might help, same poster, same issue. [http://ubuntuforums.org/showthread.php?t=1942876](http://ubuntuforums.org/showthread.php?t=1942876)

Particularly post # 9. - this was my previous post!
This was my previous - post #9!
Does this do any good?
bump@bumpyputer:~$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3500418AS_6VM9YYMB-part1
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
* grub2/linux_cmdline: /dev/sdd1
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10
bump@bumpyputer:~$ 

bump@bumpyputer:~$ sudo dpkg-reconfigure grub-pc
Replacing config file /etc/default/grub with new version
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done
bump@bumpyputer:~$ 
How is this now? - I am really confused!

---

### Post by Bumpalot on 2012-03-19
Sorry - Chose wrong entry to edit - can't find way to delete this!

---

### Post by idoitprone on 2012-03-20
assuming you didnt bork you  ubuntu installation.

tell ur bios to boot ubuntu first
and within ubuntu
type

```
sudo update-grub
```

so now you can boot both grub and windows


one more thing
i recommend taking the pains to rescue the boot loader on these window hdd
by chooseing the hd that has windows and unplugging all other hdd
use a window install or rescue cd

cuz moving hardrive will be a pain since it is linked to a other hdd
```

=> Grub2 (v1.97-1.9:cool: is installed in the** MBR of /dev/sda** and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.9:cool: is installed in the **MBR of /dev/sdb** and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
**sda1**: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

**sdb1**: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
```

---

### Post by ajgreeny on 2012-03-20
You really have got yourself into a bit of a pickle, haven't you?

You have grub 1.97 on the mbr all the disks as far as I can see, yet you were trying to install grub again.  Is this because you can not boot to any of your OSs, which I note you have not actually mentioned so far.  You should be able to change the boot priority in BIOS, or by a key press at POST and get grub appearing from any of the four disks, assuming you have not totally messed up the grub configuration files

If you can boot to ubuntu you should be able to run sudo update-grub which ought to add any OS, including Windows, to the grub menu.

I am still baffled about what exactly you are trying to do, and why.

---

### Post by Bumpalot on 2012-03-20
Thanks for your reply!
The main reason I reinstalled grub was that I cannot start Grub2 customizer - I get the popup msg "No Bootloader found
Do you want to select another root partition?"
Selected NO. This is what I am trying to rectify. What is causing Grub2 customizerto NOT find a bootloader?

---

### Post by NikTh on 2012-03-20
> **Bumpalot said:**
> 
The main reason I reinstalled grub was that I cannot start Grub2 customizer -** I get the popup msg "No Bootloader found**
Do you want to select another root partition?"
Selected NO. This is what I am trying to rectify. What is causing Grub2 customizerto NOT find a bootloader?

Maybe cause you have grub 1.97 and not newer ?_ i am not sure_.

---

### Post by idoitprone on 2012-03-20
> **Bumpalot said:**
> Thanks for your reply!
The main reason I reinstalled grub was that I cannot start Grub2 customizer - I get the popup msg "No Bootloader found
Do you want to select another root partition?"
Selected NO. This is what I am trying to rectify. What is causing Grub2 customizerto NOT find a bootloader?

of course grub customizer cannot find a bootload

/dev/sda is your windows harddrive. You kidda bork it when installing grub

I want you to go your bios and change the boot loader so that you boot /dev/sdd
and rescue your windows individually

---

### Post by oldfred on 2012-03-20
Did you reinstall grub2's boot loader to sdd not sdd1? It looks like you keep reinstalling to a partition and getting the warning and older versions of grub in the MBR. One of those must work or you could not boot at all.

Your grub reinstall was to the 1st partition of which ever drive st3500... is.

grub-pc/install_devices: /dev/disk/by-id/ata-ST3500418AS_6VM9YYMB-[COLOR=Red]part1[/COLOR]

---

