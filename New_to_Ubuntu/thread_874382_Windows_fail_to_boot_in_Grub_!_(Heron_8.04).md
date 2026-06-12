---
title: "Windows fail to boot in Grub ! (Heron 8.04)"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by maximatron on 2008-07-29
Hi!

 I'm pretty new to Ubuntu and unfortunately, I'm facing a complicated issue :(

 First I couldn't use the LiveCD to install Ubuntu but the Alternate CD; problem is, when the Grub loader starts, I can't see my Windows partition! I've done some research that led me to modify the menu.lst file in /boot/grub with this kind of line :

```
title 		Windows Vista
root		(hd0,5)
rootnoverify	(hd0)
chainloader +1
```

But that gets me :

```
Invalid or Unsupported Executable Format.

Press any key to continue...
```

Here is my partition table (fdisk -l) :

```
Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           2       30401   244188000    f  W95 Etendu (LBA)
/dev/sda5               2       25532   205077726    7  HPFS/NTFS
/dev/sda6           30153       30401     2000061   82  Linux swap / Solaris
/dev/sda7           25533       30152    37110118+  83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
```

Anyone can help me out on this ?

Thanks for any help!
Max.

---

### Post by Pro-reason on 2008-07-29
Can you please post the entirety of your */boot/grub/menu.lst* file?

Also, enter this command in the terminal:

```

sudo blkid
```

---

### Post by maximatron on 2008-07-29
> **Pro-reason said:**
> Can you please post the entirety of your */boot/grub/menu.lst* file?

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
# kopt=root=UUID=75316b85-4adb-4075-8611-f20fe26598d3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=75316b85-4adb-4075-8611-f20fe26598d3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=75316b85-4adb-4075-8611-f20fe26598d3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

title 		Windows Vista
root		(hd0,5)
rootnoverify	(hd0)
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST
```

> **Pro-reason said:**
> Also, enter this command in the terminal:

```

sudo blkid
```

```

/dev/sda5: UUID="2A0C92D10C929801" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="0a1bff45-7e98-4f8e-81bd-92e9c181371a" 
/dev/sda7: UUID="75316b85-4adb-4075-8611-f20fe26598d3" TYPE="ext3" 

```

Here!
Thanks for the fast reply..!

---

### Post by Yuki_Nagato on 2008-07-29
Did you install Windows on a Logical or Extended partition?

Any number beyond sda 4 (the last Primary Partition) is a Logical partition.  Frankly, Windows does not play nice.  It demands to be installed on the sda 1 spot.  That is why we fool it with "rootnoverify."  But I do not think that works unless Windows has been installed onto a Primary Partition.

But try re-installing at a later time.  GRUB runs the numbers starting from 0.  So instead, call root at 

```
root (hd0,4)
```

That may fix the problem.

---

### Post by maximatron on 2008-07-29
Yuki,

 Thanks for the reply; I tried (hd0,4) and instead of getting the error message, oddly, it starts GRUB again...


Edit : I don't know if that may be a problem, but fdisk gives me a message that you can see in my orignial post, which translate roughly in english as 'The entries in the partition table does not follow the order of the disk' -- could that be the problem?

---

