---
title: "[SOLVED] hardy 8.04  new linux update wiped out vista grub entry"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by wenbill on 2008-11-28
Hello, I have two hard drives. My first drive has Vista and my second drive has Ubuntu 8.04 installed which was upgraded to Ubuntu Stuudio. When I installed Ubuntu it overote my Vista boot loader with a grub menu option. This has worked well until I just updated some linux header files from update manager today 11/28. Now Vista is gone as an option in my Grub menu list. I can no longer get use of my first hard drive other than a boot drive for ubuntu.

  If anyone can help, I would appreciate it.

---

### Post by Michael.Godawski on 2008-11-28
Can you please post the content of your menu.lst
```

cat /boot/grub/menu.lst
```

Also post the output of this command:
```

sudo fdisk -l
```

---

### Post by wenbill on 2008-11-28
# This is a divider, added to separate the menu items below from the 
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-li
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-li
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

wendell@wendell-desktop:~$

Above is the first line of code.

 below s the sudo fdisk code.

wendell@wendell-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entr
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default ent
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editin
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
# kopt=root=UUID=4cc67559-1641-44a2-adaf-e1b18a51d007 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash all_generic_ide

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=4cc67559-1641-44a2-adaf-
18a51d007 ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-22-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=4cc67559-1641-44a2-adaf-
18a51d007 ro single
initrd		/boot/initrd.img-2.6.24-22-rt

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4cc67559-1641-44a2-
f-e1b18a51d007 ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=4cc67559-1641-44a2-
f-e1b18a51d007 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=4cc67559-1641-44a2-adaf-
18a51d007 ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=4cc67559-1641-44a2-adaf-
18a51d007 ro single
initrd		/boot/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4cc67559-1641-44a2-
f-e1b18a51d007 ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4cc67559-1641-44a2-
f-e1b18a51d007 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=4cc67559-1641-44a2-adaf-
18a51d007 ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=4cc67559-1641-44a2-adaf-
18a51d007 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4cc67559-1641-44a2-
f-e1b18a51d007 ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4cc67559-1641-44a2-
f-e1b18a51d007 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

wendell@wendell-desktop:~$ # This is a divider, added to separate th
e menu items below from the 
wendell@wendell-desktop:~$ # ones.
wendell@wendell-desktop:~$ titleOther operating systems:
bash: titleOther: command not found
wendell@wendell-desktop:~$ root
bash: root: command not found
wendell@wendell-desktop:~$ 
wendell@wendell-desktop:~$ 
wendell@wendell-desktop:~$ # This entry automatically added by the D
ebian installer for a non-li
wendell@wendell-desktop:~$ # on /dev/sda1
wendell@wendell-desktop:~$ titleDell Utility Partition
bash: titleDell: command not found
wendell@wendell-desktop:~$ rootflags (hd0,0)
bash: syntax error near unexpected token `hd0,0'
wendell@wendell-desktop:~$ savedefault
bash: savedefault: command not found
wendell@wendell-desktop:~$ makeactive
bash: makeactive: command not found
wendell@wendell-desktop:~$ chainloader+1
bash: chainloader+1: command not found
wendell@wendell-desktop:~$ 
wendell@wendell-desktop:~$ 
wendell@wendell-desktop:~$ # This entry automatically added by the D
ebian installer for a non-li
wendell@wendell-desktop:~$ # on /dev/sda3
wendell@wendell-desktop:~$ titleWindows Vista/Longhorn (loader)
bash: syntax error near unexpected token `('
wendell@wendell-desktop:~$ rootflags (hd0,2)
bash: syntax error near unexpected token `hd0,2'
wendell@wendell-desktop:~$ savedefault
bash: savedefault: command not found
wendell@wendell-desktop:~$ makeactive
bash: makeactive: command not found
wendell@wendell-desktop:~$ chainloader+1
bash: chainloader+1: command not found
wendell@wendell-desktop:~$ 
wendell@wendell-desktop:~$ wendell@wendell-desktop:~$ 
bash: wendell@wendell-desktop:~$: command not found
wendell@wendell-desktop:~$ 
wendell@wendell-desktop:~$

---

### Post by Michael.Godawski on 2008-11-28
Perhaps this thread will help you:


[LIST]
[*][http://ubuntuforums.org/showthread.php?t=964933](http://ubuntuforums.org/showthread.php?t=964933)
[/LIST]

---

### Post by caljohnsmith on 2008-11-28
Wenbill, how about trying again:
```
sudo fdisk -l
```
And note the "-l" is a lowercase L, not a one. If you can post that, it will help clarify your setup.

---

### Post by wenbill on 2008-11-28
Okay sorry for the alarm. everything seems to be okay. Although I don't see a Vista entry like I did prior to the update, If I hold  the down arrow key down it takes me to other operating systems and then to Vista option. Every time I have accepted a kernel update It keeps the old options, so the list of kernel options, including th rt options is getting long. The out put from Michael's requested command mentioning dividers made me think I was overlooking something simple. Thanks; will mark solved.

---

### Post by gn2 on 2008-11-28
If you want you can place Vista at the top of the Grub boot list.

To do so, one way is to press Alt+F2 and run ```
gksudo gedit /boot/grub/menu.lst
``` to open menu.lst in a graphical text editor, then cut and paste the Vista entry above the automagic kernels line, so that it looks something like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title Windows Vista/Longhorn (loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
```

You can also "comment out" the entries for the older kernels by placing # in front of them so that they look like this:

```
#title Ubuntu 8.04.1, kernel 2.6.24-22-generic
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.24-22-generic #root=UUID=4cc67559-1641-44a2-
#f-e1b18a51d007 ro quiet splash all_generic_ide
#initrd /boot/initrd.img-2.6.24-22-generic
#quiet
```

Doing so will remove them from the Grub screen, shortening the list.
You could remove most of them so you don't have to scroll down so far to get to the Vista entry.
Remember to leave at least one entry available, dont # them all..... 

Choices, choices.. :-)

---

