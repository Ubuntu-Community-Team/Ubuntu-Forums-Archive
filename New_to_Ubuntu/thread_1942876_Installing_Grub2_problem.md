---
title: "Installing Grub2 problem"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-18
Having problem: I purged Grub2 packages 
sudo apt-get purge grub grub-pc grub-common
Then ran reinstalled
sudo apt-get install grub-common grub-pc
Failed to read how to activate <OK> & somehow closed the Terminal.
Now I am unable to repeat the install:

bump@bumpyputer:~$ sudo apt-get install grub-common grub-pc
[sudo] password for bump: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
 I unlocked the lock fille but get the following:
bump@bumpyputer:~$ sudo apt-get install grub-common grub-pc
[sudo] password for bump: 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I rectify this?

---

### Post by NikTh on 2012-03-18
> **Bumpalot said:**
> 
E: Unable to lock the administration directory (/var/lib/dpkg/),** is another process using it?**

Maybe you have other applications open together? close all other applications. Update manager or synaptic or software center.. and try this again. Only with terminal open.

---

### Post by Bumpalot on 2012-03-18
No other apps open - still get same result.

---

### Post by NikTh on 2012-03-18
After unlocking the lock file did you run ```
sudo dpkg --configure -a
``` ?

---

### Post by Bumpalot on 2012-03-18
bump@bumpyputer:~$ sudo dpkg --configure -a
[sudo] password for bump: 
dpkg: status database area is locked by another process
bump@bumpyputer:~$

---

### Post by Bumpalot on 2012-03-18
MORE INFO
I took the chance & rebooted the system. Boot menu was present & booted successfully.
bump@bumpyputer:~$ sudo apt-get purge grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 8,290kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 218757 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for python-support ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Processing triggers for python-support ...
bump@bumpyputer:~$ dir
 
bump@bumpyputer:~$ sudo update-grub
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

Ran Grub Customizer
Msg: No Bootloader found
Do you want to select another root partition?
Selected NO

Can you figure what is wrong here??
Thanks in advance for your help.

---

### Post by NikTh on 2012-03-18
Maybe you have installed grub on another disk ? I can't figure out what happened but this script surely can. --> [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) . Run it and post results.

---

### Post by Bumpalot on 2012-03-19
Thanks for the link. Here is the result.
                  ```
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
                       sdd1 and looks at sector 891033792 of the same hard 
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

 424.878047943 = 456.209330176  boot/grub/core.img                             1
 424.969806671 = 456.307855360  boot/grub/grub.cfg                             1
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
```

---

### Post by oldfred on 2012-03-19
Added code tags to make script easier to read.

I do not understand why it still has any grub. When you purge you should immediately reinstall. But if you just purge you should not be able to boot nor have grub?

You have to chroot only if you cannot boot:
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

It looks like you have grub2's boot loader installed to every MBR of every drive. Some versions do not show drive, so booting from partition 1 can only be sdd1.
I usually suggest just having it in the same drive as your Ubuntu install and booting from that drive in BIOS.

Another way to reinstall and you want any reinstalls or repairs to go into sdd.
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Bumpalot on 2012-03-19
This is the result of subsequent actions I have taken. I will mark this as Solved even though it is not solved & start a new thread to obtain further help.
Thanks for your extensive suggestions previously guys.

---

