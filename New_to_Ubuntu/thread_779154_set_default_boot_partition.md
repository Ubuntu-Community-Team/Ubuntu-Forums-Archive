---
title: "set default boot partition"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by jakupl on 2008-05-02
hello :)
I have two seperate ubuntu partitions... that is, i installed ubuntu two times.
After my second install, it made itself the default boot option.

However I want the other partition to be the default one, the other one is just for testing stuff.


I tried booting on the live cd and changing the boot flag in Gparted, but it made no difference.



This is the menu.lst file for my preferred ubuntu... the one that I want to be made default.

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=fafa96f8-236a-4932-99df-1fcbe6139055 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=hpet=disable quiet

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fafa96f8-236a-4932-99df-1fcbe6139055 hpet=disable
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fafa96f8-236a-4932-99df-1fcbe6139055 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```




And this is my testing one... witch should be made, non-default.

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
# kopt=root=UUID=5e071a90-900b-4232-aea4-06ae8b256e77 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=quiet splash hpet=disable

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5e071a90-900b-4232-aea4-06ae8b256e77 ro quiet splash hpet=disable
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5e071a90-900b-4232-aea4-06ae8b256e77 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fafa96f8-236a-4932-99df-1fcbe6139055 hpet=disable 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fafa96f8-236a-4932-99df-1fcbe6139055 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 8.04, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

thankyou very much :)

---

### Post by otrojake on 2008-05-02
What you want to do is edit the menu.lst file of the partition you don't want to be default--the one with more options.  Wherever it says (hd0,5) change that to (hd0,0) and wherever it says (hd0,0) change that to (hd0,5).  You can edit those files with gedit.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by jakupl on 2008-05-02
> **otrojake said:**
> What you want to do is edit the menu.lst file of the partition you don't want to be default--the one with more options.  Wherever it says (hd0,5) change that to (hd0,0) and wherever it says (hd0,0) change that to (hd0,5).  You can edit those files with gedit.

```
sudo gedit /boot/grub/menu.lst
```

hmmm... That made no difference... :confused:

---

### Post by plucky on 2008-05-02
The easy way is to boot your test system and edit menu.lst with ```
gksudo gedit /boot/grub/menu.lst
``` and search for 
> # array will desync and will not let you boot your system.
default		0

and change the 0 to 4 (I think) so that the default is pointing to the system you want as default.


The harder way is to get the MBR to point to the default system's menu.lst file and then add the test system boot locations to that file.

Use the **Super Grub Disk** or the **Ubuntu Live CD** to change the MBR.

Good Luck

---

### Post by otrojake on 2008-05-03
Another option to try would be booting into any system--it doesn't matter which--and opening up a terminal.  From there type ```
sudo grub
```  In the prompt that comes up type ```
find /boot/grub/stage1
```  There will probably be two entries, one for (hd0,0) and one for (hd0,5).  I'm not 100% sure that's what it will say, but I'm fairly certain.  Either way, go with the lowest number after the comma and type in ```
root (hd0,0)
``` or whatever one is the lowest number and then ```
setup (hd0)
```  Then close out the terminal.  Let me know how that works for you or if you run into any problems.

---

### Post by kirios on 2008-05-03
Boot into the preferred partition, copy the entry for the test partition into menu.lst (on the preferred partition) and run **sudo grub-install (hd0)**.

---

