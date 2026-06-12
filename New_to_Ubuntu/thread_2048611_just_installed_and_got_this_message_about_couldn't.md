---
title: "just installed and got this message about couldn't install preinstalled packages"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by tbrownarcher on 2012-08-27
I just installed ubuntu 12.04 on my desktop

dell dimension 3000
one gig of memory 
dvd
200 gig hard drive 
Dual boot win xp

the install was erase ubuntu 10.1 and install 12.04 in it's place
but at the end of the install it was unable to put previously installed packages saying that I could install them after the install finished.

However the only way to boot  now is to use the live from the disk i just installed from.

when install was done as usual i got the message to remove the disk and hit enter but i got a message "< grub rescue and then when i shut down and rebooted that message appeared again if i hit enter it just says < grub rescue.  What can i do about this ... I don't want to lose the windows install on the other side. 

Thanks,
Nate

---

### Post by sandyd on 2012-08-27
Please post the output of the following commands (boot info script)

```

wget http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvfz bootinfoscript-061.tar.gz
chmod +x bootinfoscript
./bootinfoscript

```

---

### Post by tbrownarcher on 2012-08-27
ubuntu@ubuntu:~$ wget [http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz](http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz)
--2012-08-27 05:58:54--  [http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz](http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz)
Resolving superb-dca3.dl.sourceforge.net (superb-dca3.dl.sourceforge.net)... 207.228.224.228
Connecting to superb-dca3.dl.sourceforge.net (superb-dca3.dl.sourceforge.net)|207.228.224.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36345 (35K) [application/x-gzip]
Saving to: `bootinfoscript-061.tar.gz'

100%[======================================>] 36,345      20.4K/s   in 1.7s    

2012-08-27 05:58:57 (20.4 KB/s) - `bootinfoscript-061.tar.gz' saved [36345/36345]

ubuntu@ubuntu:~$ tar xvfz bootinfoscript-061.tar.gz
bootinfoscript
CHANGELOG
README
ubuntu@ubuntu:~$ chmod +x bootinfoscript



ubuntu@ubuntu:~$ ./bootinfoscript

Boot Info Script 0.61      [1 April 2012]

Please use "sudo" or become "root" to run this script.

  Run the script as sudoer:

    sudo ./bootinfoscript <outputfile>

  or if your operating system does not use sudo:

    su -
    ./bootinfoscript <outputfile>

For more info, see the help:

    ./bootinfoscript --help

ubuntu@ubuntu:~$ 

As I understand this is the output that you asked for thanks for the help... I need all i can get

thanks,
Nate

---

### Post by sandyd on 2012-08-27
Sorry, should be
```
sudo ./bootinfoscript
```

---

### Post by tbrownarcher on 2012-08-27
> ubuntu@ubuntu:~$ wget [http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/tar](http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/tar) xvfz bootinfoscript-061.tar.gz chmod +x bootinfoscript
--2012-08-27 15:44:50--  [http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/tar](http://superb-dca3.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/tar)
Resolving superb-dca3.dl.sourceforge.net (superb-dca3.dl.sourceforge.net)... 207.228.224.228
Connecting to superb-dca3.dl.sourceforge.net (superb-dca3.dl.sourceforge.net)|207.228.224.228|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/tar?download&failedmirror=superb-dca3.dl.sourceforge.net](http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/tar?download&failedmirror=superb-dca3.dl.sourceforge.net) [following]
--2012-08-27 15:44:52--  [http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/tar?download&failedmirror=superb-dca3.dl.sourceforge.net](http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/tar?download&failedmirror=superb-dca3.dl.sourceforge.net)
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 216.34.181.59
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-08-27 15:44:52 ERROR 404: Not Found.

--2012-08-27 15:44:52--  [http://xvfz/](http://xvfz/)
Resolving xvfz (xvfz)... failed: Name or service not known.
wget: unable to resolve host address `xvfz'
--2012-08-27 15:44:52--  [http://bootinfoscript-061.tar.gz/](http://bootinfoscript-061.tar.gz/)
Resolving bootinfoscript-061.tar.gz (bootinfoscript-061.tar.gz)... failed: Name or service not known.
wget: unable to resolve host address `bootinfoscript-061.tar.gz'
--2012-08-27 15:44:53--  [http://chmod/](http://chmod/)
Resolving chmod (chmod)... failed: Name or service not known.
wget: unable to resolve host address `chmod'
--2012-08-27 15:44:53--  [http://+x/](http://+x/)
Resolving +x (+x)... failed: Name or service not known.
wget: unable to resolve host address `+x'
--2012-08-27 15:44:53--  [http://bootinfoscript/](http://bootinfoscript/)
Resolving bootinfoscript (bootinfoscript)... failed: Name or service not known.
wget: unable to resolve host address `bootinfoscript'
ubuntu@ubuntu:~$ 



I don't think it did anything but maybe i just don't understand ...

the last part is 
> ubuntu@ubuntu:~$ sudo ./bootinfoscript

Boot Info Script 0.61      [1 April 2012]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/".

ubuntu@ubuntu:~$ 




I'm sorry .  I guess you want what's in results.txt here it is it's long



```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   195,784,154   195,784,092   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   620,535,807   620,533,760  83 Linux
/dev/sdb2         620,537,854   625,141,759     4,603,906   5 Extended
/dev/sdb5         620,537,856   625,141,759     4,603,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        065CE6465CE62FDB                       ntfs       
/dev/sdb1        cf60bb29-df76-46f9-8c0d-975823884e9d   ext4       
/dev/sdb5        c2dec68e-b53d-41ed-813e-1cf772f259dd   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
UnsupportedDebug="do not select this" /debug
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=cf60bb29-df76-46f9-8c0d-975823884e9d ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=cf60bb29-df76-46f9-8c0d-975823884e9d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=cf60bb29-df76-46f9-8c0d-975823884e9d ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=cf60bb29-df76-46f9-8c0d-975823884e9d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root cf60bb29-df76-46f9-8c0d-975823884e9d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 065CE6465CE62FDB
	drivemap -s (hd0) ${root}
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
UUID=cf60bb29-df76-46f9-8c0d-975823884e9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c2dec68e-b53d-41ed-813e-1cf772f259dd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-22-generic              2
               =                boot/initrd.img-3.2.0-23-generic-pae           1
               =                boot/vmlinuz-2.6.35-22-generic                 1
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                initrd.img                                     1
               =                vmlinuz                                        1

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

```

---

### Post by sandyd on 2012-08-27
ok, I seem to have figured out your problem - you have two grub installs.

The new one is installed on the secondary HDD, while the old one is still on the primary HDD.

Run this to install grub back into the primary HDD

```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo grub-install --root-directory=/media/sdb1 /dev/sda

```
on a livecd.

---

### Post by tbrownarcher on 2012-08-27
WoW! you can't even imagine how impressed i am.  

I haven't rebooted yet but i'm sure it works if not i will tell you but in the mean time ..... I know i'm new what i want to know is how you diagnosed this and composed a set of commands to fix it..... was there a reasoning process involved or some txt somewhere ?  
Also why would install put the grub on the wrong drive ?  It's all so new to me ....and seems surreal too .... but 

THANKS,
Nate

---

### Post by tbrownarcher on 2012-08-27
Again! WoW! _[COLOR="Lime"]It works.[/COLOR]_  I really would like to know how you knew all that.  I am desperately wanting to know linux.  Because that the console or terminal is the key to repairing things I really want to learn it.  You actually composed a set of commands and that makes me crazy ... how did you do that ?  

I have a linux mint 13 problem where i engaged someone's help and it caused my computer to be unbootable.  Could you help with that ...?  Here is the link to that post .  If you can't or don't want to help with that one i understand ... 

[http://forums.linuxmint.com/viewtopic.php?f=90&t=111035&p=622362#p622362](http://forums.linuxmint.com/viewtopic.php?f=90&t=111035&p=622362#p622362)

since it broke my system or i did no one will answer :>)


Many thanks,
Nate

---

### Post by sandyd on 2012-08-27
> **tbrownarcher said:**
> Again! WoW! _[COLOR="Lime"]It works.[/COLOR]_  I really would like to know how you knew all that.  I am desperately wanting to know linux.  Because that the console or terminal is the key to repairing things I really want to learn it.  You actually composed a set of commands and that makes me crazy ... how did you do that ?  

I have a linux mint 13 problem where i engaged someone's help and it caused my computer to be unbootable.  Could you help with that ...?  Here is the link to that post .  If you can't or don't want to help with that one i understand ... 

[http://forums.linuxmint.com/viewtopic.php?f=90&t=111035&p=622362#p622362](http://forums.linuxmint.com/viewtopic.php?f=90&t=111035&p=622362#p622362)

since it broke my system or i did no one will answer :>)


Many thanks,
Nate
Easy.
```

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

```
That ^^ indicates there are two grub versions and installs. 10.10 has a older version of grub. As a result, I know that the installer installed _its_ grub2 into /dev/sdb, while it is supposed to be in /dev/sda .

Install grub in the right place, and everything will work again.

Not sure about mint/wicd - never used them

---

### Post by tbrownarcher on 2012-08-27
very nice does time in service teach that ois it classes or what is it that teaches that .? whatever it is I need to do it but money stands in my way for classes.  Anyhow it all works now on this computer ..... (don't understand grub. but why instead of all that installin you had me do could you not just point the grub that was there to the right drive and sector?  .... just asking for learning purposes ) I guess for the other computer I will have to do a reinstall.

thanks,
 nate

---

