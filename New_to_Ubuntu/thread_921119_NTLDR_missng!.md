---
title: "NTLDR missng!"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by bdk09 on 2008-09-15
Hey everyone! As you can tell I'm new to ubuntu as I'm posting in these forums. Since I'm a complete noob I've ran into a problem trying to boot my XP, Vista and Ubuntu. 

When I boot up I get to the GRUB menu and try to load my windows and I get the message "NTLDR Missng:CTRL+ALT+DELTE to reboot." I tried to install over top of the Vista bootloader.(When you click advanced when installing ubuntu I selected to install grub over vista bootloader!!!)

XP and Vista are on the same drive(300gb) with 2 different primary partitions.
Ubuntu is installed on a seperate HD(80gb WD)

My bios priority for the drives are:
300gb(windows)
500gb(backup)
80gb(ubuntu)

That's the order when I installed ubuntu. Heres some other info that might help you:


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=4ed02f9b-1811-476c-b035-c3d32e6a7c6f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4ed02f9b-1811-476c-b035-c3d32e6a7c6f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4ed02f9b-1811-476c-b035-c3d32e6a7c6f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



Also:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33ee5916

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x950c45b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   348153119   174076528+   7  HPFS/NTFS
/dev/sdb2       348153120   625121279   138484080    f  W95 Ext'd (LBA)
/dev/sdb5       348153183   625121279   138484048+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   149790059    74894998+  83  Linux
/dev/sdc2       149790060   156248189     3229065    5  Extended
/dev/sdc5       149790123   156248189     3229033+  82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625137344   312568641    7  HPFS/NTFS



Any help would be great, please try to keep in mind I'm really new and I tried to do as much research as possible!

Thanks in advance!

---

### Post by rsclark3 on 2008-09-15
Each time I install Ubuntu on a second partition with Windows XP or Vista, I need to perform a repair on XP or Vista.  Using the original disk or an OEM disk, go to the recovery option to repair windows.  It will recreate the boot files and allow windows to boot again.  I'm sure there are elegant or less offensive ways to do this but it's the one I remember and can repeat without using another computer to follow instructions.

---

### Post by Crafty Kisses on 2008-09-15
Which filesystem drive has C? If it's NTFS then Ubuntu has nothing to do with the NTLDR missing error. Ubuntu doesn't support NTFS write access. If the C drive is formatted as a FAT32 filesystem, did you edit/delete anything in the C drive (/dev/hda1 or sda1)?

---

### Post by bdk09 on 2008-09-15
How do I go about doing that rsclark?

---

### Post by PocketDog on 2008-09-15
If you have an XP installation disc boot from it and go to the recovery console. Enter FIXBOOT at the command prompt.

---

### Post by bdk09 on 2008-09-15
Okay, well I did that, now I don't have grub anymore. How can I get this triple boot working with XP and vista on 1 HD and ubuntu on the other? I searched some and most triple booting is with partitioning 1 hard drive and not using the setup I have.

---

### Post by PocketDog on 2008-09-15
XP had to be fixed, so it's fixed :-p Fixing grub is no trouble at all, I thought this may be the next step. Just tootle on over here [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and all will be well

---

### Post by bdk09 on 2008-09-15
okay, thanks. I'm going to give it a go!

---

### Post by bdk09 on 2008-09-15
Okay, well I followed those directions and I still can't triple boot.

If I set my HD with ubuntu on it, my first HD in boot priority it will boot into ubuntu. Then when I set my HD with vista and XP first it will boot windows.

How can I get grub to manage 2 HDs with 3 different OSES?

---

### Post by caljohnsmith on 2008-09-16
Probably what happened is you installed Grub to the MBR of the Windows HDD, and not your Ubuntu HDD. Try these steps first:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
This is similar to what you may have done before, but it is important that the "X" in (hdX) agree with the (hdX,Y); for instance, if you get (hd1,0) for the find command above, you would use "setup (hd1)". That will ensure you install Grub to MBR of the Ubuntu HDD. Make sure Ubuntu is first in the BIOS boot order, reboot, and let me know what happens. We can take it from there.

---

### Post by bdk09 on 2008-09-17
Hey, thanks for the help. I got it all figured out now. Just had to make a couple edits to Grub and now I'm triple booting! :)

---

