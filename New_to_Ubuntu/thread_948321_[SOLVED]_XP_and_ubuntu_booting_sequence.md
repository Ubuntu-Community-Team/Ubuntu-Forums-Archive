---
title: "[SOLVED] XP and ubuntu booting sequence"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by inearlygaveup on 2008-10-15
Posted 15 Oct 08.
Hi
Can anyone help please (My first issue)
I have installed ubuntu 8.04.1 and really do quite like the system BUT I can see a bit of a learning curve ahead which I am quite looking forward to.

However, I do have a number of issues that I would like help with if possible, the first and most important is to change ubuntu's booting sequence.

Initially I had installed xandros with my XP system and they coexisted nicely. The start up screen gave the option of booting into XP or xandros but defaulted to XP after a number of seconds which was fine.

After installing ubuntu the booting sequence has changed making ubuntu the default, automatically starting it after a number of seconds.

I would really like to revert back to XP being the default start-up programme until such times as I can explain ubuntu to the rest of the family.

If anyone can help I must warn you that I am a relatively new to OS and really do need any instructions as an &#8220;idiots Guide&#8221; type of instruction &#8211; as simple as you can please - the deepest I have ever been inside a PC is the bios.

( I apologise if this question has already been asked if so please point me in the right direction)


Martin

---

### Post by Aero-Z on 2008-10-15
Enter this into console/terminal:
```
cat /boot/grub/menu.lst
```

Post the output here.

---

### Post by inearlygaveup on 2008-10-15
Wow &#8211; Thanks for your quick reply &#8211; is it really as simple as that &#8211; I will give it a try and thanks again.

---

### Post by Aero-Z on 2008-10-15
> **inearlygaveup said:**
> Wow – Thanks for your quick reply – is it really as simple as that – I will give it a try and thanks again.
Nope, it's not as simple as that. From there I could tell you what to change.

---

### Post by inearlygaveup on 2008-10-15
It gave this 
martin@martin-laptop:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: No such file or directory
martin@martin-laptop:~$

---

### Post by Aero-Z on 2008-10-15
> **inearlygaveup said:**
> It gave this 
martin@martin-laptop:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: No such file or directory
martin@martin-laptop:~$
it's .lst (L not number 1)

---

### Post by inearlygaveup on 2008-10-15
I thought this was going to be easy !!!!

It eventually gave this

martin@martin-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=0fdbaf94-108f-42e1-8277-5a4b877e8561 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0fdbaf94-108f-42e1-8277-5a4b877e8561 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0fdbaf94-108f-42e1-8277-5a4b877e8561 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0fdbaf94-108f-42e1-8277-5a4b877e8561 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0fdbaf94-108f-42e1-8277-5a4b877e8561 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Debian GNU/Linux (3.1) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.18-dcc-smp root=/dev/hda6 
savedefault
boot

martin@martin-laptop:~$

---

### Post by Orange_and_Green on 2008-10-15
Hello :)

Please type

```
gksu gedit /boot/grub/menu.lst
```

(again, all lowercase with the .lst being the letter "L")

The first line of the file that doesn't start with a "#" reads "default 0". Change that to "default 6", save, reboot and you're good to go.

Good luck :KS

---

### Post by Aero-Z on 2008-10-15
You need to change the line:
```
default 0
```
The 0 means that the system will boot into the first entry in menu.lst:
```
title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=0fdbaf94-108f-42e1-8277-5a4b877e8561 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet
```
Try changing it to:
```
default 6
```
or 7 or 8, which ever is the right OS you want to boot into by default.
To change it:
```
sudo gedit /boot/grub/menu.lst
```
make the changes, save and reboot your system.

---

### Post by inearlygaveup on 2008-10-15
Thanks - I can't try this just now as I have to go out - will follow your instructions on my return - hope it works - how do I contact you again if I mess it up

Martin

---

### Post by Aero-Z on 2008-10-15
> **inearlygaveup said:**
> Thanks - I can't try this just now as I have to go out - will follow your instructions on my return - hope it works - how do I contact you again if I mess it up

Martin
Keep us informed in this thread.

---

### Post by inearlygaveup on 2008-10-15
Hi and thanks again for your help, that sorted it &#8211; I needed to change it to 7 thanks.


Another question please ( If I need to start a new thread please advise)

On the start up menu I had the following lines.
Ubuntu 8.04.1 Kernel 2.6.24.21 generic
Ubuntu 8.04.1 generic recovery mode
Ubuntu 8.04.1 memtest
Other operating systems
Windows NT/2000/xp
Microsoft windows xp Home Edition
Debian GNU/Linux (3.1) (on./dev/hda6

It has now added the following lines 
Ubuntu 8.04.1 Kernel 2.6.24.19 generic
Ubuntu 8.04.1 generic recovery mode

Any idea why.
Can I remove any!

---

