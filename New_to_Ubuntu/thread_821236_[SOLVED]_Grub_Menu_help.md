---
title: "[SOLVED] Grub Menu help"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by yami280 on 2008-06-07
Umm okay I've seen some screens of the grub menu where when loaded it would automatically load a OS unless you pressed a Function key.  I forgot which one. I donn't mean the countdown taht the Grub menu usually has.  I mean that it would just start with a certain OS automatically.  I was wondering how i would do that.

---

### Post by Bachstelze on 2008-06-07
Just set the countdown to one second ;)

---

### Post by yami280 on 2008-06-07
No I want it to load vista.  If i set it to 1sec it will load the first OS on the list which is ubuntu.

---

### Post by quelx on 2008-06-07
```
sudo nano -w /boot/grub/menu.lst
```
To edit the delay change the **timeout** option (it's in seconds).

To edit the default OS change **default** to the number you want selected when grub loads. 0 is the most recent kernel.  You'll need to scroll down to see the other options, 0 is the first, 1 is the second, and so on.

To see the menu put a **#** before **hiddenmenu**

**CTRL-X** to save and exit.

---

### Post by yami280 on 2008-06-07
thanks i'll try it now

---

### Post by rraj.be on 2008-06-07
Make a copy of your /boot /grub/menulist

sudo cp /boot/grub/menulist.lst /home/menulistbackup.lst.

type  sudo gedit /boot/grub/menu.lst

It will openthe menu list.

It will be some what like this.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#//.........-----------------

something




----------...............//
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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ad8c2f3-c6b6-4f87-bee5-ff951b528dc6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ad8c2f3-c6b6-4f87-bee5-ff951b528dc6 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		  
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```




edit it such that > VISTAL BOOT LOADER IS AT THE TOP ABOVE ALL OTHER DEBIAN MENU ENTRIES.





```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

/..................................//////


something......





..................../////
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

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		  
root		(hd0,1)
savedefault
makeactive
chainloader	+1


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ad8c2f3-c6b6-4f87-bee5-ff951b528dc6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ad8c2f3-c6b6-4f87-bee5-ff951b528dc6 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by dwhitney67 on 2008-06-07
The Grub menu is defined in /boot/grub/menu.lst.  Editing the file will require root-privileges.

A typical file looks like:
```
default		0
timeout		3

# Hides the menu by default (press ESC to see the menu)
hiddenmenu

splashimage=(hd0,0)/grub/splash.xpm.gz


# 2.6.24-18
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=UUID=2a721a42-9f7d-4da0-925d-0ba69f09254e ro quiet splash
initrd		/initrd.img-2.6.24-18-generic
quiet

# 2.6.24-18 (Recovery Mode)
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=UUID=2a721a42-9f7d-4da0-925d-0ba69f09254e ro single
initrd		/initrd.img-2.6.24-18-generic

# 2.6.24-17
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-17-generic root=UUID=2a721a42-9f7d-4da0-925d-0ba69f09254e ro quiet splash
initrd		/initrd.img-2.6.24-17-generic
quiet

...

```

Each section that begins with the "title" keyword is listed in Grub's boot menu.  In the case of the file shown above, the default boot-choice is the first titled section, or number "0".  The second titled section would be number "1", and so on.

As *HymnToLife* hinted at, if you wish to control the timeout period that a user has to press ESC to change the boot option, change the "timeout" section above.  For an instant boot into the default titled section, select a value of 0.  Any number greater than this represents the number of seconds that Grub will give to the user to make a choice.  In the file above, it is set to 3 seconds.

---

### Post by yami280 on 2008-06-07
Thanks pplz I tried it and I got it to work.

---

### Post by yami280 on 2008-06-07
Okay it doesn't work.  This is my menu.lst file.  I need it to make the second Vista OS as default cause the first one is system recovery.  I've tried 6 and 7 but they both go to the first Vista.  anyone help?
```

gfxmenu /boot/grub/message.studio
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
default		6

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
# kopt=root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by rraj.be on 2008-06-07
Which vista do you wan2 boot first ?

Is it i sda1 or sda2.

Just be conform of it.

---

### Post by yami280 on 2008-06-07
> **rraj.be said:**
> Which vista do you wan2 boot first ?

Is it i sda1 or sda2.

Just be conform of it.

Huh? whats sda1 or 2?  I want to boot the second one on the list.  The first one is just system recovery.

---

### Post by rraj.be on 2008-06-07
sda1 is partition 1 of your first hard drive and sda 2 is patition 2 of 1'st H/d


First save your menu.lst in some safe place except any root directory.

Then just post me the section that you want to boot.

---

### Post by yami280 on 2008-06-07
ok i wanna boot this one 
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by rraj.be on 2008-06-07
Take it as my knid advice.

Just back up ur menu.lst file.


Replace your menu.lst  contents with this.


```
gfxmenu /boot/grub/message.studio
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
default		6

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
# kopt=root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# Normal debian kernals

#---------------------------------------------------


title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dbeb52bb-ae91-44bd-abd4-ebef4e27161b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by yami280 on 2008-06-07
Ok thanks I got it to work.

---

### Post by rraj.be on 2008-06-07
Please mark your thread as solved if it's solved.
see my signature to know why it should be marked.

---

### Post by Herman on 2008-06-07
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```You shouldn't put foreign operating system entries anywhere in between the sign shown above, which is there to mark the beginning of the Debian Automagic Kernels list, and the sign posted below, which is there to mark the end of the Debian Automagic Kernels list.
If you do, it will be deleted every time Ubuntu has a kernel update.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
```Regards, Herman :)

---

