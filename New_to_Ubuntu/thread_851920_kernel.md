---
title: "kernel"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-07
I had installed ubuntu with kernel 2.6.22-14-generic.
I downloaded kernel 2.6.25.7 and compiled it.
now my boot menu shows three versions of the above viz.,
2.6.25.7 previous
2.6.25.7 old
2.6.25.7 

The 'previous' one opens (after an era) to a command-prompt like 
(intraframs)

the other two don't open at all.
now I wish to remove them. I can't find them in the synaptic package manager.

---

### Post by sameer.india on 2008-07-07
can anyone help??????????

---

### Post by lisati on 2008-07-07
Post the contents of /boot/grub/menu.lst and someone might be able to walk you through the task.

---

### Post by PmDematagoda on 2008-07-07
The initramfs problem might be due to the fact that you didn't create an initramfs for that particular kernel which would be required if you want to use the kernel with Ubuntu.

---

### Post by ET! on 2008-07-07
when you are compiling a new kernel you need to create an image with

mkinitramfs command. to remove the kernel entry just delete the entry off the grub list...and you cant find kernels listed in synaptic..its not a package or a program

---

### Post by sameer.india on 2008-07-09
> **lisati said:**
> Post the contents of /boot/grub/menu.lst and someone might be able to walk you through the task.

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
# kopt=root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro

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

title		Ubuntu 7.10, kernel 2.6.25.7 Default
root		(hd0,2)
kernel		/boot/vmlinuz root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro quiet splash  locale=fr_FR i8042.reset
quiet

title		Ubuntu 7.10, kernel 2.6.25.7 Default (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro single

title		Ubuntu 7.10, kernel 2.6.25.7.old Previous
root		(hd0,2)
kernel		/boot/vmlinuz.old root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro quiet splash  locale=fr_FR i8042.reset
quiet

title		Ubuntu 7.10, kernel 2.6.25.7.old Previous (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz.old root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro single

title		Ubuntu 7.10, kernel 2.6.25.7.old
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25.7.old root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro quiet splash locale=fr_FR i8042.reset
quiet

title		Ubuntu 7.10, kernel 2.6.25.7.old (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25.7.old root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro single

title		Ubuntu 7.10, kernel 2.6.25.7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25.7 root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro quiet splash  locale=fr_FR i8042.reset
initrd		/boot/initrd.img-2.6.25.7
quiet

title		Ubuntu 7.10, kernel 2.6.25.7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25.7 root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro single
initrd		/boot/initrd.img-2.6.25.7

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro quiet splash  locale=fr_FR i8042.reset
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99e51e9a-3447-4949-9be8-4aa579f8e7d4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
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

---

### Post by sameer.india on 2008-07-09
'default' opens to the command prompt.
the rest do not open at all.

The only kernel i can use here is 2.6.22-7-generic.

And by the way the synaptic shows installed linux kernels.Search for linux headers.

and i don't think that editing menu.lst will free the space that has been taken up by the files of 2.6.25.7.

---

### Post by sameer.india on 2008-07-09
I gave this command after updating grub.

 sudo mkinitramfs -o initrd.img-2.6.25.7 2.6.25.7

---

### Post by sameer.india on 2008-07-09
any suggestions????

---

### Post by zvacet on 2008-07-09
I know it is not answer to your querstion,but read [this.]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

### Post by sameer.india on 2008-07-09
I want to uninstall not install

---

### Post by sameer.india on 2008-07-09
come on please someone

---

### Post by sameer.india on 2008-07-09
noone has any answer???????

---

### Post by PmDematagoda on 2008-07-09
Please be patient sameer.india, and please keep in mind that you may only bump a thread once within 24 hours.

About your problem, did you create an initramfs image? If not, post the entire version of the kernel you made.

---

### Post by master_kernel on 2008-07-09
Try this in a terminal:
```
sudo apt-get remove 2.6.25-*
```
And then:
```
sudo update-grub
```

---

### Post by sameer.india on 2008-07-10
I did create an inraframs image and i didn't make the kernel i downloaded it from kernel.org.

---

### Post by cariboo on 2008-07-10
As far as I know you can not get premade kernals from Kernal.org. What compelling reason do you have, to need a kernel that is not available for any version of Ubuntu.

It sounds like you are just extracting your kernel source to /boot

Go to System-->Adminstration--Synaptic Package Manger and install the latest kernel image v2.6.24.19-generic and then get rid of everything else.

If you do want to compile your own kernel, have a look here:

[http://www.faqs.org/docs/Linux-HOWTO/Kernel-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Kernel-HOWTO.html)

Jim

---

