---
title: "[SOLVED] Extra Lines in boot screen"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by newbeeman on 2008-05-31
I have just upgraded to 8.04,worked fine, then another update recently and now find I have extra lines in the boot up screen, where it lists other OS there are a number lines for Ubuntu.
I could go into edit and delete the extras, but which ones do I delete and does it matter.

---

### Post by shifty_powers on 2008-05-31
what are the extra lines?

```
sudo gedit /etc/apt/sources.list
```

---

### Post by newbeeman on 2008-05-31
> **shifty_powers said:**
> what are the extra lines?

```
sudo gedit /etc/apt/sources.list
```

We need to back up a touch. I'm talking of the boot screen at the very start of Ubuntu, where you can select the Operating System, either Ubuntu or Windows.

---

### Post by shifty_powers on 2008-05-31
yup, so am i ;)

that is the grub boot loader selection screen.

the options it gives you are contained in the file in the sommand i gave you ;)

(gedit is a text editor. running that command will display the co-netnts of your bootloader list, letting us see what he options you have at boot ;))

---

### Post by Joeb454 on 2008-05-31
Can you post the output of ```
cat /boot/grub/menu.lst
``` and use [ CODE][ /CODE] tags :)

---

### Post by shifty_powers on 2008-05-31
doh, doh, doh


bugger


juyst noticed i posted source.list, not menu.list for grub.

teach me not to pay attention...


what joeb posted is honestly what i meant to type... bit of a blond moment ;)

---

### Post by sayakb on 2008-05-31
```
sudo gedit /boot/grub/menu.lst
```

EDIT.. My God, Joeb and shifty_powers beat me on tht.. or am I gettin slower ;)

---

### Post by newbeeman on 2008-05-31
> **shifty_powers said:**
> 
(gedit is a text editor. running that command will display the co-netnts of your bootloader list, letting us see what he options you have at boot ;))

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse

#AUTOMATIX REPOS START

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted multiverse

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted multiverse
#AUTOMATIX REPOS END

I assume this is what you want.
Strange as I removed Automatix as it doesn't seem to be needed in 8.04
It's still listing 7.1 Gusty Gibbon

---

### Post by Joeb454 on 2008-05-31
No, we actually wanted ```
/boot/grub/menu.lst
```

And to shifty_powers & LinuxIsInnovation - you should actually use **gksudo** rather than sudo, for graphical app's :)

---

### Post by shifty_powers on 2008-05-31
> **Joeb454 said:**
> No, we actually wanted ```
/boot/grub/menu.lst
```

And to shifty_powers & LinuxIsInnovation - you should actually use **gksudo** rather than sudo, for graphical app's :)

true, use sudo as a bad habit ;) and i REALLY did mean /boot/menu/grub.lst honest ;)

---

### Post by newbeeman on 2008-05-31
> **Joeb454 said:**
> No, we actually wanted ```
/boot/grub/menu.lst
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
# kopt=root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
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
makeactive
chainloader	+1


OK. As you'll see there are a lot of extra lines after "End Default options"

---

### Post by shifty_powers on 2008-05-31
by the looks of that, you just have the last three kernel's listed.

go into synaptic, search for startup manager, install it.

you can then limit the kernel list to 1, 2 etc....

---

### Post by Joeb454 on 2008-05-31
Do you boot using the top option on your menu.lst? If so replace your menu.lst with this one: ```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
initrd /boot/initrd.img-2.6.24-17-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
initrd /boot/initrd.img-2.6.24-17-generic

#title Ubuntu 8.04, kernel 2.6.24-16-generic
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
#initrd /boot/initrd.img-2.6.24-16-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
#initrd /boot/initrd.img-2.6.24-16-generic

#title Ubuntu 8.04, kernel 2.6.22-14-generic
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
#initrd /boot/initrd.img-2.6.22-14-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
#initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Or use startup manager ;)

---

### Post by newbeeman on 2008-05-31
> **shifty_powers said:**
> by the looks of that, you just have the last three kernel's listed.

go into synaptic, search for startup manager, install it.

you can then limit the kernel list to 1, 2 etc....

Just tried your suggestion. Synaptic won't run. It shows the file load circle but then it stops loading.

---

### Post by shifty_powers on 2008-05-31
interesting.

what happens when you

```
sudo apt-get update
```

in a terminal?

(updates your packages list)

and joeb way will of course work as well ;)

---

### Post by newbeeman on 2008-05-31
> **Joeb454 said:**
> Do you boot using the top option on your menu.lst? If so replace your menu.lst with this one: ```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
initrd /boot/initrd.img-2.6.24-17-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
initrd /boot/initrd.img-2.6.24-17-generic

#title Ubuntu 8.04, kernel 2.6.24-16-generic
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
#initrd /boot/initrd.img-2.6.24-16-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
#initrd /boot/initrd.img-2.6.24-16-generic

#title Ubuntu 8.04, kernel 2.6.22-14-generic
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro quiet splash
#initrd /boot/initrd.img-2.6.22-14-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b2f85d11-5f3e-462a-95af-ab126a1cdfa3 ro single
#initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Or use startup manager ;)


You have totally lost me now. Where and how do I replace mu menu,lst

---

### Post by sayakb on 2008-05-31
Well, do 
```
gksudo gedit /boot/grub/menu.lst
```
Delete everything it has and replace it with this..

---

### Post by newbeeman on 2008-05-31
> **shifty_powers said:**
> interesting.

what happens when you

```
sudo apt-get update
```

in a terminal?

(updates your packages list)

and joeb way will of course work as well ;)

As per your suggestion, got the following error

W: You may want to run apt-get update to correct these problems
david@david-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
I'm not good at terminal entries.

---

### Post by sayakb on 2008-05-31
To avoid hassles.. at a terminal:
```
sudo apt-get install startupmanager
```
Now goto System->Administration->StartUp-Manager and Click Advanced tab.
There, **check** the Limit no of kernels... and select 1 there.

---

### Post by sayakb on 2008-05-31
> **newbeeman said:**
> As per your suggestion, got the following error

W: You may want to run apt-get update to correct these problems
david@david-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
I'm not good at terminal entries.

You need to use sudo apt-get update. Sudo executes the command as root.

EDIT: I've got a feeling that we are confusing you terribly. So just listen to one of us, because all of the above methods are correct. In Linux, you have indefinite alternatives for everything you see ;)

---

### Post by newbeeman on 2008-05-31
> **LinuxIsInnovation said:**
> You need to use sudo apt-get update. Sudo executes the command as root.

EDIT: I've got a feeling that we are confusing you terribly. So just listen to one of us, because all of the above methods are correct. In Linux, you have indefinite alternatives for everything you see ;)

You're correct. Managed to muddle through and I believe we have fixed it. Thanks to all involved.

---

### Post by shifty_powers on 2008-05-31
oh and btw, you can't run apt-get commands when you have synaptic open ;)

did you manage to install startup manager?

---

