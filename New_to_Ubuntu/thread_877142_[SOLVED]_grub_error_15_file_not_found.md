---
title: "[SOLVED] grub error 15 file not found???"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-01
i installed ubuntu studio to a usb hard drive and when i boot 
it shows both systems but when i click on one or the other i get
that  error what can i do to fix it ??
any help would be greatly appreciated!!!!!
rick:confused:

---

### Post by meindian523 on 2008-08-01
both systems?Please post the results of ```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
``` of your installed Ubuntu from a live CD.

---

### Post by meindian523 on 2008-08-01
Also,where did you install Grub,to the MBR of the internal HDD or the USB HDD?Do you get this error when you boot without the external HDD plugged in or all the time,regardless of whether the USB HDD is plugged in or not?

---

### Post by opscure on 2008-08-01
Check out this post:
[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

---

### Post by rixtr66 on 2008-08-01
meindian523;i installed the grub to the ext.hd.
i only get this message when the hd.is plugged in,
i moved the ext.hd.in front of the internal hd.
in the bios.here are the outputs you asked for:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29648   238147528+  83  Linux
/dev/sdb2           29649       30401     6048472+   5  Extended
/dev/sdb5           29649       30401     6048441   82  Linux swap / Solaris
rick@ubuntu-studio:~$ 
and the next one:
rick@ubuntu-studio:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=74840861-fc5b-418b-bd63-5c58fb657afe ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=74840861-fc5b-418b-bd63-5c58fb657afe ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=74840861-fc5b-418b-bd63-5c58fb657afe ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=74840861-fc5b-418b-bd63-5c58fb657afe ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=74840861-fc5b-418b-bd63-5c58fb657afe ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


rick@ubuntu-studio:~$ 

any help would be great thanx
rick

---

### Post by rixtr66 on 2008-08-01
opscure;thanx for the info,i checked it out and i cant quite follow it
but i'll give it another shot.
rick

---

### Post by rixtr66 on 2008-08-01
still in a bind and i could really,really,really,really,use some help.
please.
rick:confused:

---

### Post by rixtr66 on 2008-08-01
ok i tried to do what was in the grub error file not found post,but it just confused me,and didnt do what i expected,i even tried a super grub disk,and that didnt work.so now i cant access the usb hardive,and i dont know how
to get back to where i started.s.o.s
:confused:rick

---

### Post by phidia on 2008-08-01
Have you made sure that in your bios the 1st boot device is usb drive?

If you're getting the grub error....did you use the desktop/live cd to install ubuntu?
As meindian523 asked before I'm trying to determine where grub was installed-the mbr of the internal or the usb drive?

---

### Post by DivinityX on 2008-08-01
i had this error just yesterday, i fixed it by reinstalling GRUB. It may not work for you but give it a shot, run these codes in terminal...

```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

Let me know if it works! ^_^

---

### Post by rixtr66 on 2008-08-01
divinityx;sorry that didntwork:(
phidia;yes my usb hardrive is first in line in the bios,and i installed
grub to dev/sdb of the usb hard drive.do you have a fix??
i would be eternally greatful if you do!!
thanx rick:confused:oh yes i used an iso that iburned its not a live cd
its a dvd.

---

### Post by phidia on 2008-08-01
> **rixtr66 said:**
> divinityx;sorry that didntwork:(
phidia;yes my usb hardrive is first in line in the bios,and i installed
grub to dev/sdb of the usb hard drive.do you have a fix??
i would be eternally greatful if you do!!
thanx rick:confused:oh yes i used an iso that iburned its not a live cd
its a dvd.

Part of the problem, I think, is that when you installed to the usb drive the installer sees it as (hd0,0) 

> title Ubuntu 8.04.1, kernel 2.6.24-20-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-20-generic root=UUID=74840861-fc5b-418b-bd63-5c58fb657afe ro quiet splash
initrd /boot/initrd.img-2.6.24-20-generic
quiet

And you're saying you installed grub to sdb which in grub notation is (hd1). I had an external usb drive install-different partitioning than yours but try changing that entry I quoted in menu.lst to > root (hd1,0) and see what happens when you try to boot. At the very least we will learn more about this. If you have problems or need help editing let us know.

---

### Post by rixtr66 on 2008-08-01
i did some changes,and reinstalled every thing,i installed ubuntu studio
to my main drive and and again to the usb drive,only this time i put the
bootloader on dev/sdb not sdb1,then i reinstalled to my hard drive,when i booted i got error 21,but on another boot it worked,i could boot to both,
then it went back to error 21.hmmmmmmmm????file doesnt exsist
whoooff rick:(

---

### Post by rixtr66 on 2008-08-02
well i think isorted it out,i just reinstalled on th usb hd,and saved the boot to hdo,and now i can boot both.so i think its solved,but im going to double check.
rick

---

### Post by meindian523 on 2008-08-02
Well,actually that IS the solution.But I found it confusing that you got the error 15 when your external was plugged in.Usually the problem appears when Grub has been installed to the MBR of the external and people try to boot without plugging in the external.The solution,as you found out,is to install Grub to the MBR of the internal HDD.

---

