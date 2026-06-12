---
title: "Dual boot fails"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by AncientPC on 2008-08-10
Just bought a Thinkpad T61 for my wife and it arrives with Vista pre-installed.  The thing about Thinkpads is that it doesn't have restore CDs, only a restore partition.

I installed Ubuntu v8.10 and resized the disk to what it looks like below.  Unfortunately in the bootloader regardless if I boot to either hd0,0 or hd0,1 it only will boot to Lenovo's Repair and Restore, I can't get back into Vista.  Any suggestions?

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb6b8246

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         856     6873088   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         857       10595    78223320    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10595       12161    12579840    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           10595       11509     7340728+  83  Linux
/dev/sda6           11509       11901     3144928+  83  Linux
/dev/sda7           11901       12161     2094088+  82  Linux swap / Solaris
```

---

### Post by Yuki_Nagato on 2008-08-10
Have you run the Repair and Restore yet?  If at all possible, we want to restore Vista (even at the expense of nuking Ubuntu,) because we cannot reinstall it.

Try booting with the Ubuntu disk.  We might be able to find something out if we can see your GRUB files.

If Ubuntu boots up, get into your system, and then run

```
cat /boot/grub/config.lst
```

and shoot us the output.

---

### Post by bpowell2005 on 2008-08-10
> **AncientPC said:**
> Just bought a Thinkpad T61 for my wife and it arrives with Vista pre-installed.  The thing about Thinkpads is that it doesn't have restore CDs, only a restore partition.

I installed Ubuntu v8.10 and resized the disk to what it looks like below.  Unfortunately in the bootloader regardless if I boot to either hd0,0 or hd0,1 it only will boot to Lenovo's Repair and Restore, I can't get back into Vista.  Any suggestions?



It looks like your windows partition is on hd0,2...looks like there is a boot partition (hd0,0) then the recovery partition (hd0,1) and then windows (hd0,2)...Can you try that?

---

### Post by AncientPC on 2008-08-10
Ubuntu works fine, but the OS is primarily for me and as a backup OS for the wife.  She still wants to work with Windows. *shrugs*

I assume you mean menu.lst since I don't have config.lst, so here it is:
```
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
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=fff5f7c9-134c-4d43-a5e1-0a3b5c1db82a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fff5f7c9-134c-4d43-a5e1-0a3b5c1db82a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fff5f7c9-134c-4d43-a5e1-0a3b5c1db82a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Lenovo Thinkpad Restore & Repair
root		(hd0,0)
makeactive
chainloader	+1


```

> **bpowell2005 said:**
> It looks like your windows partition is on hd0,2...looks like there is a boot partition (hd0,0) then the recovery partition (hd0,1) and then windows (hd0,2)...Can you try that?



Let me give that a try.

---

### Post by AncientPC on 2008-08-10
> **bpowell2005 said:**
> It looks like your windows partition is on hd0,2...looks like there is a boot partition (hd0,0) then the recovery partition (hd0,1) and then windows (hd0,2)...Can you try that?

hd0,0 boots to recovery
hd0,1 boots to recovery
hd0,2 non-existent
hd0,3 non-existent
hd0,4 boots to Ubuntu

---

### Post by hofa on 2008-08-10
Your menu.lst looks just fine =/

Can you access your Windows partition from Ubuntu?

---

### Post by AncientPC on 2008-08-10
> **hofa said:**
> Your menu.lst looks just fine =/

Can you access your Windows partition from Ubuntu?

Yes, both recovery and Vista partition mount just fine from within Ubuntu, but within gparted and fdisk they flag the partitions with an error that they do not end on a cylinder boundary.

Then again the extended partition (that contains /, /home, and swap) does not end on a cylinder boundary and it works just fine. :(

---

