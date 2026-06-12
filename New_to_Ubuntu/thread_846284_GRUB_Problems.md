---
title: "GRUB Problems"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by john.hall on 2008-07-01
I'm having some trouble getting Grub to work as I want.  I have an 80 GB drive with WinXP Pro on it.  I have another drive with WinXP Home and Ubuntu 8.04.  Most of this should be obvious from the fdisk -l output:

```

root@joha-desktop:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4f6e4f6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10336    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004b2e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       44619   358402086    7  HPFS/NTFS
/dev/sdb2           44620       45105     3903795   82  Linux swap / Solaris
/dev/sdb3           45106       60801   126078120   83  Linux

```

And here is my menu.lst file:

```

root@joha-desktop:/boot/grub# cat menu.lst
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
timeout		3

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
# kopt=root=UUID=7399a4a2-6d9e-4374-b477-b0e79c82ec96 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7399a4a2-6d9e-4374-b477-b0e79c82ec96 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7399a4a2-6d9e-4374-b477-b0e79c82ec96 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
chainloader	+1

```
I've modified it since the 8.04 install.  I'll talk about that in a moment.

There are two things that have been troubling me.  Note that these things did not occur with 7.10.  The only happened when I reformatted the 7.10 partition and installed 8.04.

After installing 8.04, the hard drive numbers were swapped (no idea why).  So I had to edit menu.lst to get rid of the lines
```

map		(hd0) (hd1)
map		(hd1) (hd0)

```
in the XP Home entry and change everything from hd0 to hd1 and hd1 to hd0.  I'm not really sure what the map does, but it was causing a problem similar to what I am having now.  The main thing is that it did not work at first, I messed around a little, and then it worked for a while.

Today I go to reboot my machine.  I select XP Home, but XP Pro boots.  I reboot and select XP Pro and XP Pro boots.  I reboot and select Ubuntu and it says no partition.  So I edit the command to say "root (hd1,2)" (it had changed to hd0,2).  I have no idea why it had changed (Well, when I booted to XP Pro the first time, when I selected XP Home, I got a STOP error.  But I disconnected my iPod and the error went away on the next boot.  I don't THINK that caused the problem.)  I boot Ubuntu and look around and have no clue why I can't boot XP Home, so here I am.  
Question 1: How do I get XP Home to boot?
Question 2: Why did it change all the hd1 to hd0 and vice versa?  Why didn't everything stay the way I had it before?

---

### Post by nick_h on 2008-07-01
> Why did it change all the hd1 to hd0 and vice versa? Why didn't everything stay the way I had it before?
Did you change the boot sequence in the BIOS?

> How do I get XP Home to boot?
Windows likes to be on the first drive.  To run it from the second drive you need the two map commands to make the Windows drive look like the first one.

---

### Post by john.hall on 2008-07-01
> **nick_h said:**
> Did you change the boot sequence in the BIOS?

Not since the install of 8.04.

> **nick_h said:**
> Windows likes to be on the first drive.  To run it from the second drive you need the two map commands to make the Windows drive look like the first one.
I added the map lines back, and I can boot it now.  But it worked a couple days ago when I tried it without the map lines.  It's possible that I was unable to boot XP Pro at that time, and I just didn't know.

---

### Post by nick_h on 2008-07-01
Obviously your drive order changed - I don't know why.  I would expect you to need the map commands for the Windows on the second drive.

---

