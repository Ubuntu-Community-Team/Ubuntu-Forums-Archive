---
title: "[SOLVED] No grub menu after windows install"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by pete_zahuat on 2008-07-23
I use ubuntu a lot but had to install windows.  Now I have no grub menu and windows automatically installs.  Is there an easy way to fix this problem and restore grub?

---

### Post by neurostu on 2008-07-23
yes you need to download the super grub boot disk to reinstall grub.

when you installed windows, it overwrote grub with the windows MBR...

If you reinstall grub it will allow you to select either windows or ubuntu upon boot time.

---

### Post by LittleLORDevil on 2008-07-23
I believe you can use the Alternate disc and skip to the end to install GRUB

---

### Post by jordanmthomas on 2008-07-23
Boot off your Ubuntu LiveCD and run
```
sudo grub 
```
Then,
```

root (hd0,?) (? being where your controlling distro is)
setup (hd0)
quit
```


Also, 5 seconds in google:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lizzard on 2008-07-23
Take a look at this [article.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by appi2012 on 2008-07-23
I would go with the live cd solution. To find out which partition your ubuntu install is in, type:
```
sudo grub
```
```
find /boot/grub/stage1
```

---

### Post by pete_zahuat on 2008-07-23
I used the super grub boot disc and got ubuntu running again. Now xp doesn't show up on grub.  Any ideas on how to get it on grub?

---

### Post by appi2012 on 2008-07-23
Run ubuntu and open the file /boot/grub/menu.lst, and post the contents here. Also, post what typing:
```
sudo fdisk -l
```
in a terminal returns.

Through those two pieces of information, I'll be able to find what your grub menu looks like, and also which partition windows is in.

---

### Post by pete_zahuat on 2008-07-23
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
# kopt=root=UUID=d433f33a-326c-428e-8e14-9ea900aad983 ro

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
# defoptions=quiet splash vga=792

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d433f33a-326c-428e-8e14-9ea900aad983 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d433f33a-326c-428e-8e14-9ea900aad983 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               3        3857    30965287+  83  Linux
/dev/sda2   *        3858        4771     7341705    c  W95 FAT32 (LBA)
/dev/sda3            4772        4864      747022+   5  Extended
/dev/sda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

---

### Post by appi2012 on 2008-07-23
Press alt+f2 and then type: ```
gksudo gedit /boot/grub/menu.lst
```

Add this to the end of the file:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Then save the file. That should fix it!

---

