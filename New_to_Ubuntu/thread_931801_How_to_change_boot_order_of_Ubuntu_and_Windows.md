---
title: "How to change boot order of Ubuntu and Windows???"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by mksboysal on 2008-09-27
I am a new Ubuntu user. 

What I have experienced so far, sure will help new users like me: 

Can anyone create a small boot update that at the boot menu you will have an option to choose which OS to use. For example 

press 1 Ubuntu
press 2 Windows XP
press 3 Windows Vista etc.  

There is instructions how to create such orde[ here]("http://mathijs.jurresip.nl/2007/09/25/how-to-change-boot-order-of-ubuntu-and-windows/")   

However is not clear (to me)  in detail how to add this new command line. 

Do you replace:(title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)

WITH ->

title Microsoft Windows XP Home Edition
root (hd0,0)      


OR: Do you add this line of command: 

title Microsoft Windows XP Home Edition
root (hd0,0)   

On top of 

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)

I wish this boot order of Ubuntu and Windows would be part of Ubuntu OS
where OS boot option menu will come up. 

If you wish to comment on what I have said here, I thank you in advance.

Mksboysal.>>

---

### Post by Xiong Chiamiov on 2008-09-27
Do you currently have Windows and Ubuntu installed?  If so, then we can help you rearrange your GRUB menu so that Windows is on top.  AFAIK, you can't have numbers for the menu; you have to use the arrow keys to scroll through them (well, unless you want to write your own bootloader).

---

### Post by bumanie on 2008-09-27
Those instructions aren't going to allow you to set up a 
press 1 Ubuntu
press 2 Windows XP
press 3 Windows Vista etc. scenario - it allows you put vista/xp first on the grub menu. You can do that an easier way with a GUI tool called startupmanager > sudo apt-get install startupmanagerYou will find it under system  --> StartUp-manager

---

### Post by fooman on 2008-09-27
there is an app in the repositories called startup manager that can make the changes for you.

open synaptic...system > administration > synaptic package manager.

when it opens, click search and type startupmanager in the box.  install startupmanager.  when it finishes, close synaptic.

go to system > administration > startup-manager

under the boot options tab, click the "use timeout in bootloader menu", and change the "timeout in seconds" to 5 seconds.  at the bottom, under "misc." make sure "show bootloader menu" and "show boot splash" are checked.

close startup-manager (give a minute to write the changes)...reboot.

---

### Post by kansasnoob on 2008-09-27
> **fooman said:**
> there is an app in the repositories called startup manager that can make the changes for you.

open synaptic...system > administration > synaptic package manager.

when it opens, click search and type startupmanager in the box.  install startupmanager.  when it finishes, close synaptic.

go to system > administration > startup-manager

under the boot options tab, click the "use timeout in bootloader menu", and change the "timeout in seconds" to 5 seconds.  at the bottom, under "misc." make sure "show bootloader menu" and "show boot splash" are checked.

close startup-manager (give a minute to write the changes)...reboot.

+1 ......... well I prefer 10 seconds:)

[ATTACH]86599[/ATTACH]

---

### Post by mksboysal on 2008-09-27
Fooman, thanks so much. You gave me a perfect instructions... Everything worked the way you said, above.  (I have yet to reboot the os) However, so far so good... Later I'll come back here and let you know further what happened...
Thanks again...

mksboysal.

---

### Post by mksboysal on 2008-09-28
Hey guys, 

Could anyone examine this code here, for me please... 
(Apparently it's not working, on the boot menu Windows XP appears
but when press ENTER says bad command or something like that)
and windows XP won't open up. 

Here is the code that I entered into "menu.lst (/boot/groub...

## ## End Default Options ##

title           Microsoft Windows XP Home Edition
root            (hd0,0)
makeactive
chainloader	+1
#  

Thank you all
Mksboysal.

---

### Post by bumanie on 2008-09-28
Post the output of > sudo fdisk -lu and > cat /boot/grub/menu.lst We need to see you partition setup etc. to know whether that is correct or not.

---

### Post by jemate18 on 2008-09-28
I think mapping keys for "1" ubuntu, "2" Windows

aint possible, but rearraging the order of entries in /boot/grub/menu.lst will do what you want... except that you'll have to use arrow keys instead of number keys

---

### Post by mksboysal on 2008-09-28
Thanks Bumanie, 



> **bumanie said:**
> Post the output of  and  We need to see you partition setup etc. to know whether that is correct or not.

Result for: sudo fdisk -lu    see below:



Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x975b4298

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   114286409    57143173+  83  Linux
/dev/sda2       114286410   117290564     1502077+   5  Extended
/dev/sda5       114286473   117290564     1502046   82  Linux swap / 
Solaris
home@home-laptop:~$ 


And result for: cat /boot/grub/menu.lst    see also below

home@home-laptop:~$ cat /boot/grub/menu.lst 
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
# kopt=root=UUID=51e16cb4-531f-4a63-aab7-66dcdaaf15ea ro

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
# defoptions=splash vga=792 quiet

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

title           Microsoft Windows XP Home Edition
root            (hd0,0)
makeactive
chainloader	+1
#
                 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51e16cb4-531f-4a63-aab7-66dcdaaf15ea ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=51e16cb4-531f-4a63-aab7-66dcdaaf15ea ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
home@home-laptop:~$

---

