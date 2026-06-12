---
title: "Second Hard Drive Doesn't Show Up"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by awanpmjadb on 2008-05-06
Right, so as an obvious preface, I've no idea what I'm doing.  My much nicer, faster computer died, so I'm using a much older, slower computer.  Windows was just far too slow, and I was interested in trying out Linux.

Anyway, I installed Ubuntu on my 8GB drive and was able to see all of my files on my 40GB just fine.  However, it was still running a bit slow.  

I heard that xubuntu ran a bit more smoothly so I switched.

However, after having installed the system on my 8GB like before but with xubuntu, I can no longer view my 40GB.  Before it showed up in places and even on the desktop.

I ran "sudo fdisk -l" and the hard drive is at least recognized.  From the initial installation of ubuntu to the switch to xubuntu, it's been only a few hours, so I highly doubt that anything physical is wrong with the drive and I haven't manually changed any settings/jumpers, etc.

My guess is that it's likely something simple and I'm making an *** of myself.

Help?

---

### Post by bumanie on 2008-05-06
8g is very minimal as root will probably take at least half of that. Despite that, you probably need to edit /etc/fstab and possibly /boot/grub/menu.lst.
Please post the output of > cat /etc/fstab and > cat /boot/grub/menu.lst>  sudo fdisk -l may also be helpful.

---

### Post by awanpmjadb on 2008-05-06
Thanks for the quick response!  As you requested:

> patrick@Patrick:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c34d7618-362d-4069-9c4b-9ffb396fa63c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ddbbc3a2-7d19-4e68-b590-34abd4bd832c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


[COLOR="Blue"]> patrick@Patrick:~$ cat /boot/grub/menu.lst 
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
# kopt=root=UUID=c34d7618-362d-4069-9c4b-9ffb396fa63c ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c34d7618-362d-4069-9c4b-9ffb396fa63c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c34d7618-362d-4069-9c4b-9ffb396fa63c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[/COLOR]

> [COLOR="Red"]
patrick@Patrick:~$ sudo fdisk -l 
[sudo] password for patrick: 

Disk /dev/sda: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         748     6008278+  83  Linux
/dev/sda2             749         788      321300    5  Extended
/dev/sda5             749         788      321268+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94b72c26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    7  HPFS/NTFS
[/COLOR]

---

### Post by bumanie on 2008-05-06
Sorry, I have little time right now, but if no-one else helps, I will get try to get back to you later. Your xp is safe, it is just that it is not recorded in /boot/grub/menu.lst nor /etc/fstab. xp being on sdb1 can cause issues (windows prefers the first hard drive), but it is not out of the question to get things working again. Boot flag is on xubuntu, I think it should be on windows. Sorry, have to go.

---

### Post by awanpmjadb on 2008-05-06
Not a problem, I really appreciate your help.  I'm still searching google for answers, but to no avail so far.  Hopefully someone here will spell it out for me.  Thanks again!

---

### Post by bumanie on 2008-05-06
I will help as much as I can. It is good that you are searching google. I can tell you for future reference that [this]("http://users.bigpond.net.au/hermanzone/p15.htm") page is most helpful for grub and booting problems.

I have started writing instructions, but had second thoughts as this is a brand new xubuntu installation. Probably the easiest thing to do would be to make your windows drive the primary hard drive in bios and reinstall xubuntu to the slave/secondary drive. That would be easiest. I can post the other instructions, but I think  doing the above will be easier. I should have thought of this before. Changing lists etc. can get messy. Post back with your decision.

---

### Post by hyper_ch on 2008-05-06
the 40gb drive is a ntfs drive and it's not being mounted. Have a look here:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by jimv on 2008-05-06
> **bumanie said:**
> 8g is very minimal as root will probably take at least half of that.
Please post the output of  and  may also be helpful.

I've been using this laptop for 6 months and installed everything I coud think of, and I'm only using 6 gigs of space.  8 gigs is plenty for an Ubuntu install, as well as lots of apps.

---

### Post by bumanie on 2008-05-06
> **jimv said:**
> I've been using this laptop for 6 months and installed everything I coud think of, and I'm only using 6 gigs of space.  8 gigs is plenty for an Ubuntu install, as well as lots of apps.

My hardy heron (using gnome) has a root partition in excess of 5g, I'm not sure how much lighter xubuntu is. I'm glad your system is so light on hdd space.

---

### Post by jimv on 2008-05-06
I just got rid of all my old kernels and freed up 700 megs :D

---

### Post by awanpmjadb on 2008-05-06
> **bumanie said:**
> I will help as much as I can. It is good that you are searching google. I can tell you for future reference that [this]("http://users.bigpond.net.au/hermanzone/p15.htm") page is most helpful for grub and booting problems.

I have started writing instructions, but had second thoughts as this is a brand new xubuntu installation. Probably the easiest thing to do would be to make your windows drive the primary hard drive in bios and reinstall xubuntu to the slave/secondary drive. That would be easiest. I can post the other instructions, but I think  doing the above will be easier. I should have thought of this before. Changing lists etc. can get messy. Post back with your decision.

Thanks for the help everyone, I'm going to reinstall as suggested.  I've had a very enjoyable welcome to Linux and these forums.  :)

---

### Post by omnidecay on 2009-02-05
Try to install a program called "Disk Manager" from the synaptic package manager. I also installed the 3g support and then selected the option to auto configure. It doesn't show up on the desktop but if you go into file system/media/ you should see your disk there. Hope this was of some help, I know I'm a little late...

---

