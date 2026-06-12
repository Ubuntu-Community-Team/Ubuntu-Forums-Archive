---
title: "Dual boot within Ubuntu"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by r5gtt2k3 on 2008-05-17
Hi, Is there anything i can install on Ubuntu to set up a boot manager so when i boot the machine up it lets me choose which OS to run ? (Ubuntu is the slave and Vista is the Master yet Ubuntu is booting up 1st)

I just want to choose which OS to run when i turn the pc on, Not quite sure if i am explaining it properly though heh

---

### Post by Biggy on 2008-05-17
Install Startup-Manager from Add/Remove

---

### Post by Raccoon1400 on 2008-05-17
Grub should be able to do that. Do you see the boot menu now?

---

### Post by r5gtt2k3 on 2008-05-17
I've installed that through add/remove, It gives me a menu but only "primary" and it doesn't find vista at all, Grub is being a pain. Doesn't find vista at all, Jumpers are in correct positions I've checked so many times now

---

### Post by r5gtt2k3 on 2008-05-17
They're on 2 different drives, I can't find nothing in google corrosponding to anything just on different partition, yet, I don't even understand that :S

---

### Post by Raccoon1400 on 2008-05-17
Add vista to /boot/grub/menu.lst manually. Should look something like this:

title Windows Vista
root (hd0,2)
makeactive
chainloader +1

Edit: startup-manager can do the same things as editing menu.lst. I prefer menu.lst, it gives me more flexibility.

---

### Post by r5gtt2k3 on 2008-05-17
I'n Bios it shows Vista as the Master and Ubuntu as the Slaveso whyis it booting Ubuntu and not vista ? I could sort it out I'n vista but i can't boot into it :(

---

### Post by r5gtt2k3 on 2008-05-17
Aha i got that page up tried to put it into the list but saving failed, What would i type to get it up with the terminal ? Thanks

---

### Post by Raccoon1400 on 2008-05-17
> **r5gtt2k3 said:**
> Aha i got that page up tried to put it into the list but saving failed, What would i type to get it up with the terminal ? Thanks

Use sudo.
```
sudo gedit /boot/grub/menu.lst
```
this opens it as root.

you will have to modify the vista entry for your hard drive partiton.
Does vista show up in your boot menu?

If you need more help post the output of
```
sudo fdisk -l
```

and the contents of your menu.lst file.

---

### Post by r5gtt2k3 on 2008-05-17
Disk /dev/hda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc1b6c1b6

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       38637   292088828    7  HPFS/NTFS
/dev/hda2   *       38637       41346    20480000    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    5  Extended
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table


Ok, The 320gb is the hdd for Vista but vista is on it's own 20GB partition in the 320gb drive

The 80gb hdd is Ubuntu (slave

And the other hdd is just RAW at the moment, Nothing on it at all

---

### Post by r5gtt2k3 on 2008-05-17
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
#timeout		10

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
# kopt=root=UUID=b7f6b39d-c988-4f37-94ff-fc34621fbc11 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b7f6b39d-c988-4f37-94ff-fc34621fbc11 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


(sorry i don't know how to make the little window with the srcroll on thisforum) thats my menu.list

---

### Post by r5gtt2k3 on 2008-05-17
I did just add 

title Windows Vista
root (hd0,2)
makeactive
chainloader +1

Whislt editing it as the root, I got rid of the memtest and the other boot option, But there is no vista and when i opened the list again the vista part had vanished

---

### Post by Raccoon1400 on 2008-05-17
your vista entry should look like:

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

---

### Post by the8thstar on 2008-05-17
Since Grub considers the disk where Ubuntu is installed as hd0, I would change the Vista entry as:

> title Windows Vista
root (**hd1,0**)
makeactive
chainloader +1 

---

### Post by Raccoon1400 on 2008-05-17
> **r5gtt2k3 said:**
> I did just add 

title Windows Vista
root (hd0,2)
makeactive
chainloader +1

Whislt editing it as the root, I got rid of the memtest and the other boot option, But there is no vista and when i opened the list again the vista part had vanished

You should keep the recovery mode.

There is a divider after the ubuntu entries. It shows up in the boot menu as
other operating systems.

Vista should go after that.

Can someone post that part of menu.lst so r5gtt2k3 can add it. I do not have ubuntu installed. I am using arch.

---

### Post by Raccoon1400 on 2008-05-17
> **the8thstar said:**
> Since Grub considers the disk where Ubuntu is installed as hd0, I would change the Vista entry as:

try that too. I didn't see your menu.lst file before posting my suggestion.

---

### Post by the8thstar on 2008-05-17
Also, in menu.lst, change this:

> #timeout 10
to this:

> timeout 10

Chances are, that might alone be the solution to your problem.

---

### Post by Raccoon1400 on 2008-05-17
> **the8thstar said:**
> Also, in menu.lst, change this:


to this:



Chances are, that might alone be the solution to your problem.

Would help, but r5gtt2k3's menu.lst file doesn't have a vista entry.

---

### Post by the8thstar on 2008-05-17
Correct, **Raccoon1400**. But once he sorts it out, That should help too!

---

### Post by r5gtt2k3 on 2008-05-17
Thanks alot, It now works :) I had to change the drive again on the vista install as reply #14 i think, I don't really want a time out either because i sometimes forget that i have a time out and turn pc on an walk away and then it could load up the wrong OS :D Thanks alot for your help guys, Fantastic community here and people don't mind helping. Once again, Thanks :)

---

### Post by the8thstar on 2008-05-17
Glad we could help. :)

Now, don't forget to THANK us and to mark your thread as SOLVED. ;)

---

### Post by r5gtt2k3 on 2008-05-17
;) Glad to be of service :D

---

