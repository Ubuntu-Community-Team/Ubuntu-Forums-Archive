---
title: "Kernel &amp; Grub"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by marty1011 on 2008-05-26
Hello.
I am new to linux. In order to learn more about linux I decided to install Gentoo from Ubuntu. I have a few questions:

1. How can I use the default USE Flags?

2. what does ```
cp arch/x86/boot/bzImage /boot/kernel-2.6.24-gentoo-r8
``` mean?

3. How can I add this kernel to Grub inside the Ubuntu boot directory?

Thanks.

---

### Post by cardinals_fan on 2008-05-26
> **marty1011 said:**
> Hello.
I am new to linux. In order to learn more about linux I decided to install Gentoo from Ubuntu. I have a few questions:

1. How can I use the default USE Flags?

2. what does ```
cp arch/x86/boot/bzImage /boot/kernel-2.6.24-gentoo-r8
``` mean?

3. How can I add this kernel to Grub inside the Ubuntu boot directory?

Thanks.
1. ?

2. You're copying the kernel file to a boot location.

3. **Add** the following to /boot/menu.lst, adjusting the parts in red:
```
title  [COLOR="#ff0000"]#your_title[/COLOR]
root (hd0,[COLOR="Red"]0[/COLOR])
kernel /boot/kernel-2.6.24-gentoo-r8 root=/dev/[COLOR="#ff0000"]hda1[/COLOR]
```

---

### Post by marty1011 on 2008-05-27
I cannot boot into Gentoo. I am getting kernel panic error.
During installing I edited gentoo's fstab as following
/dev/sda6 / ext3 
/dev/sda5   swap sw

Don't know if that is causing the trouble.

Also I don't have a seperate boot partition. I have not touched Ubuntu's fstab.

I added the following to Ubuntu's grub menu.lst

title           Gentoo Linux 2.6.24-r8
root            (hd0,5)
kernel          /boot/kernel-2.6.24-gentoo-r8 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda6 udev
intrid          /boot/initramfs-2.6.24-gentoo-r8

Can someone please guide me. Thanks a lot.

---

### Post by Duck2006 on 2008-05-27
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by marty1011 on 2008-05-27
Apparently the reason for kernel panic is that the system cannot read my sda6 partition. It is saying that file system is invalid whereas gparted is showing it to be ext3. Any help guys. Thanks.

---

### Post by Duck2006 on 2008-05-27
In the terminal type

sudo fdisk -l

and 

cat /boot/grub/menu.lst

and post the outputs here.

---

### Post by marty1011 on 2008-05-27
the result of fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51575157

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14471   116238276    7  HPFS/NTFS
/dev/sda2           18377       19457     8683132+   7  HPFS/NTFS
/dev/sda3           14472       17699    25928910   83  Linux
/dev/sda4           17700       18376     5438002+   5  Extended
/dev/sda5           18210       18376     1341396   82  Linux swap / Solaris
/dev/sda6           17700       18209     4096512   83  Linux

Partition table entries are not in disk order

```


and menu.lst
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
# kopt=root=UUID=659f6832-e9b0-4d2b-ac2d-de73ed0f8e5a ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=659f6832-e9b0-4d2b-ac2d-de73ed0f8e5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=659f6832-e9b0-4d2b-ac2d-de73ed0f8e5a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=659f6832-e9b0-4d2b-ac2d-de73ed0f8e5a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=659f6832-e9b0-4d2b-ac2d-de73ed0f8e5a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title           Gentoo Linux 2.6.24-r8
root            (hd0,5)
kernel          /boot/kernel-2.6.24-gentoo-r8 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda6 udev
intrid          /boot/initramfs-kernel-2.6.24-gentoo-r8

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

Thanks.

---

### Post by marty1011 on 2008-05-27
Here is what it says during boot:
No filesystem could mount root tired: ext2 ext3 reiserfs vfat
Kernel Panic not syncing VFS unable to mount root fs on unknown-block(1,0)

Any help guys. Thanks.

---

### Post by meierfra. on 2008-05-27
> Here is what it says during boot:
No filesystem could mount root tired: ext2 ext3 reiserfs vfat
Kernel Panic not syncing VFS unable to mount root fs on unknown-block(1,0)


This is a message from the  kernel, this means that Grub reached the Gentoo kernel and all your grub setting are correct. So something is wrong with  either your gentoo partition or much more likely with  the kernel parameters you are using:
         
> kernel        /boot/kernel-2.6.24-gentoo-r8 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda6 udev




Sorry, I don't know anything about gentoo, so I have no idea what the parameters are supposed to look like.
The problem could also come from your fstab. But again, I don't know how an gentoo fstab is supposed to look like.


Is where any chance that gentoo installed a bootloader to the boot sector of the gentoo partition?
If yes try

```

title Gentoo
chainloader (hd0,5)+1 
```


Also please move your Gentoo item below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise it  will disappear during the next Ubuntu kernel update.

---

### Post by marty1011 on 2008-06-11
Thanks I fixed the problem. And also thanks to meierfra for your tip > Also please move your Gentoo item below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise it will disappear during the next Ubuntu kernel update. 

---

### Post by marty1011 on 2008-06-11
I made a separate /boot partition a while ago. I just have a little question- if by any chance my partition becomes full is there a way to clean my old/unused kernels and make space.

Thanks.

---

### Post by meierfra. on 2008-06-11
Click on drs305 in my signature for a nice howto an kernel updates. It also tells you how to uninstall old kernels.

---

