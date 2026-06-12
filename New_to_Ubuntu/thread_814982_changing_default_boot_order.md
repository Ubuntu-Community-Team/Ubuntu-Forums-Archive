---
title: "changing default boot order"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ed1380 on 2008-06-01
ive installed ubuntu just to get familiar w/ linux. I'm liking it so far. since xp is still my main os, I'd like to know if there was a way to make grub boot xp after the timeout.

also i have a failed instal of ubuntu that shows up when i try to boot xp. msconfig shows it but all the buttons are grayed out. no big deal cause it defaults of xp but would be nice to remove it
heres an attempt of a picture to help

. . . . . . . . . . . grub
. . . . . . . . . . ./ . .\
. . . . . . . . . .xp . . .ubuntu
. . . . . . . . . / \
. . . . . . . . xp . ubuntu(failed instal)


another thing that would be really great is if i could boot straight to xp, unless i hold down something while booting

thanks

---

### Post by sayakb on 2008-06-01
```
sudo gedit /boot/grub/menu.lst
```There shall be about 4-5 lines below the "Other operating systems" label starting from the "Windows XP/Vista" and going till "chainloader +1" . Just move them above the first ubuntu entry.

---

### Post by mcduck on 2008-06-01
If you move the windows entry, make sure you keep it outside of the are marked as "AUTOMAGIC KERNEL LIST" (or whatever it's called). Everything in that are will be rewritten during kernel updates..

Actually the correct way to change the default OS is much simpler. Just find the line with "default 0" (or some other number) and change the number to the number of your Windows entry in he menu.lst file, starting from 0.

---

### Post by philinux on 2008-06-01
If you install startupmanager you can choose which is the default os and adjust a load of other stuff through it's gui.

---

### Post by ed1380 on 2008-06-01
> **LinuxIsInnovation said:**
> ```
sudo gedit /boot/grub/menu.lst
```There shall be about 4-5 lines below the "Other operating systems" label starting from the "Windows XP/Vista" and going till "chainloader +1" . Just move them above the first ubuntu entry.what do i do with that code? im a complete noob and talk of having to use code in linux is what has kept me away for so long

> **mcduck said:**
> If you move the windows entry, make sure you keep it outside of the are marked as "AUTOMAGIC KERNEL LIST" (or whatever it's called). Everything in that are will be rewritten during kernel updates..

Actually the correct way to change the default OS is much simpler. Just find the line with "default 0" (or some other number) and change the number to the number of your Windows entry in he menu.lst file, starting from 0.is there any way you could explain that a bit more. 
thanks


i tried startup manager and couldnt find where the os selection is

---

### Post by sayakb on 2008-06-01
The best choice will be to install startupmanager as philinux said.
```
sudo apt-get install startupmanager
```
Then goto System->Administration->StartUp-Manager and set the default OS from there.

---

### Post by ed1380 on 2008-06-01
startup manager worked. i got the first thing done. yall have been the most helpful forum ever. so many replies so fast.

i was still wondering if its possible to fix the second boot menu. this is what xp is showing me. ive deleted the wubildr file in c/ and d/ and it still gives me an option to boot ubuntu. check boot path says everything is ok

---

### Post by ed1380 on 2008-06-01
i seem to have another problem. it suspends fine, but never comes back. the pc will turn on but there will be no video signal. the second time it didnt even want to reboot w/ video. i had to keep it unplugged for a few hours.

---

### Post by meierfra. on 2008-06-01
> i was still wondering if its possible to fix the second boot menu. this is what xp is showing me. ive deleted the wubildr file in c/ and d/ and it still gives me an option to boot ubuntu. check boot path says everything is ok


You need to remove the wubi line from boot.ini. To  edit boot.ini check out this link [http://support.microsoft.com/kb/289022]("http://support.microsoft.com/kb/289022")

---

### Post by faust99 on 2008-08-01
Hi friends

I have installed debian on a separate partition but would like to adjust the boot loader so that ubuntu is the default os. However, the debian installation does not seem to show up in /boot/grub/menu.lst. What to do? Here is the the content of the file:

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
# kopt=root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=659bb5a7-cc45-4f70-9633-a30e814231a7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

