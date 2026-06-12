---
title: "Update has modified GRUB"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by dover19 on 2008-07-28
I use both Ubuntu and WinXP at work, and I just performed an update in Ubuntu 7.10 and when I rebooted I didn't have the option of booting up in WinXP (and WinXP was my default choice before).

---

### Post by compiledkernel on 2008-07-28
Its rather old post, but still somewhat valid. 

Try this. 

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by kool_kat_os on 2008-07-28
go to terminal and type in:

```
sudo gedit /boot/grub/menu.lst
```

and post the contents of the file

---

### Post by kool_kat_os on 2008-07-28
or try what compiledkernel said....:)

---

### Post by dover19 on 2008-07-28
> **kool_kat_os said:**
> go to terminal and type in:

```
sudo gedit /boot/grub/menu.lst
```

and post the contents of the file

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
# kopt=root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by kool_kat_os on 2008-07-28
> **dover19 said:**
> ```
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
# kopt=root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

ya....your windows partition isnt listed in there...did you try that link?

---

### Post by dover19 on 2008-07-28
> **compiledkernel said:**
> Its rather old post, but still somewhat valid. 

Try this. 

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Hmmm....that just says restore GRUB, but will it detect my WinXP and put it in list of choices? Because that's not technically a RESTORE, it just creates a new one right?

---

### Post by kool_kat_os on 2008-07-28
> **dover19 said:**
> Hmmm....that just says restore GRUB, but will it detect my WinXP and put it in list of choices? Because that's not technically a RESTORE, it just creates a new one right?

well...its like restoring it to when it was installed i think

---

### Post by dover19 on 2008-07-28
I know, I can tell it isn't listed, I'm just wonder why the f*** ubuntu had to screw around with this file lol, and how do I get it back to what it used to be. I've played around in this file before because I had to make Windows my default choice and I was instructed into opening up this file and copy pasting it so that it's placed before Ubuntu.

---

### Post by kansasnoob on 2008-07-28
I would just go to Administration > Partition Editor (aka: gparted), NOT to make any changes, but just to determine what partition Windows is located on. Like sda1 or sda 2, etc. You must know this!

Then go to terminal and:

```
sudo gedit /boot/grub/menu.lst
```

Then enter all of the following:

title Windows XP
root (hd0,x)
makeactive
chainloader +1 

But NOTE: "root (hd0,x)" assumes that you have only one hard drive, that's the "0" in "(hd0,x)", and the "x" in "(hd0,x)" needs to be the valid partition number minus "one". YES ........ minus one! GRUB begins numbering with 0 (zero), so sda1 on a single hard drive = root (hd0,0).

Clear as mud:confused:

You could post a screenshot of Gparted, and tell me if you have only one hard drive.

---

### Post by dover19 on 2008-07-28
> **kansasnoob said:**
> I would just go to Administration > Partition Editor (aka: gparted), NOT to make any changes, but just to determine what partition Windows is located on. Like sda1 or sda 2, etc. You must know this!

Then go to terminal and:

```
sudo gedit /boot/grub/menu.lst
```

Then enter all of the following:

title Windows XP
root (hd0,x)
makeactive
chainloader +1 

But NOTE: "root (hd0,x)" assumes that you have only one hard drive, that's the "0" in "(hd0,x)", and the "x" in "(hd0,x)" needs to be the valid partition number minus "one". YES ........ minus one! GRUB begins numbering with 0 (zero), so sda1 on a single hard drive = root (hd0,0).

Clear as mud:confused:

You could post a screenshot of Gparted, and tell me if you have only one hard drive.

Sweet, this is exactly what I wanted to know; How to modify the grub file myself and with these instructions it worked out perfectly!

Thanks

---

