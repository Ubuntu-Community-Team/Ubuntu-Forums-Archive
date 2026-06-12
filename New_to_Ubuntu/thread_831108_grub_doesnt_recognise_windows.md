---
title: "grub doesnt recognise windows"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by bagguley on 2008-06-16
Much to mu disgust Ive has to put WinXP back onto my computer. I now have a 10 GB windows partition and a 50GB Ubuntu partition.

One problem, grub isnt recognising Windows. my menu.lst file is as follows
> 
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
# kopt=root=UUID=84b10088-3170-4c17-a50d-35d915cb0087 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=84b10088-3170-4c17-a50d-35d915cb0087 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=84b10088-3170-4c17-a50d-35d915cb0087 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

Can anyone help please?

---

### Post by ChildOfMana on 2008-06-16
comment out 'hiddenmenu' and set your timeout to, say, 5 (to give you chance to see the menu), save the file and re-boot.

Does Windows appear in the list now?

If so can you select it and does it boot okay?

---

### Post by bagguley on 2008-06-16
yes I can see it and no it doesnt. The error message I get is 'Invalid device request'

---

### Post by rraj.be on 2008-06-16
In the last line you could see that windows too pointing to linux partition

see here.

```

title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1
```

```



root (hd0,1)
```

Change it to 

```
root (hd0,x)
```

where x is windows partition number

and it should be this.

just change it to

```
root (hd0,0)
```

---

### Post by bagguley on 2008-06-16
Right, done that. Still get the reply
> 
Error 12: Invalid device request

If it helps my partition table is 

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e204

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         884     7100698+   f  W95 Ext'd (LBA)
/dev/sda2   *         885        7296    51504390   83  Linux
/dev/sda5               2         702     5630782+   b  W95 FAT32
/dev/sda6             703         884     1461883+  82  Linux swap / Solaris


---

### Post by rraj.be on 2008-06-16
i cant guess your hard disk number.

\Better reinstall your GRUB.

To Reinstall do the folowing

```
Boot into live cd.
```

Type the following in terminal
```

sudo grub

find /boot/grub/stage1
```

if it returned like

```
(hdx,y)
```

then type

```
root (hdx,y)

setup (hdx)

quit

sudo reboot

```

This will reinstall GUB and i hope your windows will be linked correctly.

---

### Post by bagguley on 2008-06-16
Yup tried that

Once again ```
Error 12 : Invalid device request
```

---

### Post by rraj.be on 2008-06-16
i have to refer a bit.

Because  Error 12 is some what undefined.

The fix is to replace (hd0,1) with hd(0,x)

i will get you what that x is in very short.

just a min

---

### Post by rraj.be on 2008-06-16
replace roor (hd0,) in microsofts entry by

```
root (hd0,4)
```

---

### Post by bagguley on 2008-06-16
Sorry mate, still coming up 

```
Error 12: Invalid device request
```

---

### Post by rraj.be on 2008-06-16
see here what they say for GRUB Error 12:

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by rraj.be on 2008-06-16
hey try this super GRUB.

it might help you

```
[supergrub.forjamari.linex.org]("supergrub.forjamari.linex.org")
```

---

### Post by bagguley on 2008-06-16
Not that specific is it......Thankyou for your help anyhow. May just have to low level format folowed by fresh installs

---

### Post by cariboo on 2008-06-16
From looking at your fdisk listing your partitioning looks kind of strange, you don't have a primary partition, and all your partitions are in an extended partition, and if i'm seeing right you don't have an ntfs partition of any sort, are you running XP on a fat32 drive? If you are going to redo your hard drive I would suggest just using primary partitions, you can create up to four on a single hdd. The best idea would be to install XP have it create partition that is 50% of the drive then install Ubuntu and let it use the remaining space

---

