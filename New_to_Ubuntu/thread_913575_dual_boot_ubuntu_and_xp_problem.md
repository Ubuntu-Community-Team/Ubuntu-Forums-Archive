---
title: "dual boot: ubuntu and xp problem"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by jayN on 2008-09-07
right now my hard drive is partitioned with xp on one half and Ubuntu on the other. i installed xp first and that worked fine its just after i put ubuntu on, grub isnt detecting xp. anyone know whats going on??

---

### Post by overdrank on 2008-09-07
> **jayN said:**
> right now my hard drive is partitioned with xp on one half and Ubuntu on the other. i installed xp first and that worked fine its just after i put ubuntu on, grub isnt detecting xp. anyone know whats going on??

Hi and welcome, can you post the output of this command ```
sudo fdisk -l

``` in the terminal. The terminal is located under applications, accessories. This will make sure the windows partition is still intact.

Edit moved to ABT :)

---

### Post by jayN on 2008-09-07
jay@jay-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33d07f9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97b997b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1       14592   117210208+   f  W95 Ext'd (LBA)
/dev/sdb5            6375       14592    66011053+   7  HPFS/NTFS
/dev/sdb6            5889        6374     3903763+  82  Linux swap / Solaris
/dev/sdb7               1        5106    41013850+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)

---

### Post by overdrank on 2008-09-07
Hi and you may check and add windows to your grub menu list. You can use this command ```
gksudo gedit /boot/grub/menu.lst
```
This link has some good info 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Sorry to be so short but have to report to work. :)

---

### Post by jayN on 2008-09-08
i added windows to the list but when i restart and try to run windows i get stuck on a black screen that says "starting up..."

---

### Post by kansasnoob on 2008-09-08
Would you please post the output of:

```
sudo gedit /boot/grub/menu.lst
```

I know it's long, but I'd just like to double check it.

These multiple drive systems can be a real bear!

---

### Post by jayN on 2008-09-08
```
st - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet


title 		XP
rootnoverify	(hd0,4)
savedefault
chainloader +1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

thanks for taking a look at my problem.

---

### Post by kansasnoob on 2008-09-08
> **jayN said:**
> ```
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
# kopt=root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet


title 		XP
rootnoverify	(hd0,4)
savedefault
chainloader +1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

thanks for taking a look at my problem.

OK, looking at this:

> Device Boot Start End Blocks Id System
/dev/sdb2 * 1 14592 117210208+ f W95 Ext'd (LBA)
/dev/sdb5 6375 14592 66011053+ 7 HPFS/NTFS
/dev/sdb6 5889 6374 3903763+ 82 Linux swap / Solaris
/dev/sdb7 1 5106 41013850+ 83 Linux

I can see that sdb2 is marked to boot (the * below the "boot" column), now it does slightly concern me that it has "Ext'd" at the end of it, so if what I suggest doesn't work the next thing I'd need to see is a screenshot of Gparted, aka: Partition Editor, but we'll cross that bridge if and when we come to it.

You see Linux sees the win partition as sdb2 which is hard drive #2, partition #2. Grub starts numbering with 0 (zero) so sdb2 is hd(1,1).

So I think where you have:

> title 		XP
rootnoverify	(hd0,4)
savedefault
chainloader +1
boot

I'd try:

> title Windows XP
root (hd1,1)
makeactive
chainloader +1 

It gets different if you have operating systems on different drives but you don't.

---

### Post by jayN on 2008-09-08
unfortunately that didn't fix the problem, it came up with a error 22 no partition exists

---

### Post by kansasnoob on 2008-09-08
> **jayN said:**
> unfortunately that didn't fix the problem, it came up with a error 22 no partition exists

Then I'd think it has to sdb5:

> Device Boot Start End Blocks Id System
/dev/sdb2 * 1 14592 117210208+ f W95 Ext'd (LBA)
/dev/sdb5 6375 14592 66011053+ 7 HPFS/NTFS
/dev/sdb6 5889 6374 3903763+ 82 Linux swap / Solaris
/dev/sdb7 1 5106 41013850+ 83 Linux

Remember I expressed concern about the "Ext'd" at the end of that string?

sdb5 = hd(1,4)

So change:

> title Windows XP
root (hd1,1)
makeactive
chainloader +1 

to:

> title Windows XP
root (hd1,4)
makeactive
chainloader +1 

If that doesn't work I'm a bit stymied without some more research.

---

### Post by kansasnoob on 2008-09-08
You know though, as I look some more, I notice that it's saying:

> title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=7eb088ba-7a1c-460c-88bf-817065ba8d4e ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

Linux is booting from (hd0,6) which boggles my mind because Linux is clearly on sdb7 which should translate into hd(1,6).

Don't change that! You'll end up not even being able to boot Ubuntu!

But that's odd:confused:

Are all three hard drives (sda, sdb, sdc) internal drives?

---

### Post by jayN on 2008-09-08
the same error 22 comes up but if i type this in

title 		Windows XP
root		(hd0,4)
chainloader +1

it just gets stuck at a blank screen with "starting up..." 

don't know if that helps but any other help you can give me would be good

---

### Post by jayN on 2008-09-08
> **kansasnoob said:**
> 

Are all three hard drives (sda, sdb, sdc) internal drives?

sdc is an external but the other 2 sda and sdb are internals

---

### Post by kansasnoob on 2008-09-08
> **jayN said:**
> the same error 22 comes up but if i type this in

title 		Windows XP
root		(hd0,4)
chainloader +1

it just gets stuck at a blank screen with "starting up..." 

don't know if that helps but any other help you can give me would be good

Well, since it boots Ubuntu and sees that as hd(0) it can't hurt to try:

> title Windows XP
root (hd0,1)
makeactive
chainloader +1 

or:

> title Windows XP
root (hd0,4)
makeactive
chainloader +1 

Also you notice here:

> title 		Windows XP
root		(hd0,4)
chainloader +1

You're missing "makeactive".

---

### Post by jayN on 2008-09-08
none of those work, they all come up with error 12, i looked it up and it says error 12 has something to do with they way the partition was created, as either logical or primary, im sure i formated the xp partition as logical, does that still mean i need the "makeactive"

---

### Post by kansasnoob on 2008-09-08
I'm stumped.

Hopefully Caljohnsmith or someone equally knowledgeable will stumble across this thread.

Sorry I couldn't help you out:(

---

### Post by caljohnsmith on 2008-09-08
> **jayN said:**
> ```
jay@jay-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33d07f9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97b997b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1       14592   117210208+   f  W95 Ext'd (LBA)
[COLOR="Blue"]/dev/sdb5            6375       14592    66011053+   7  HPFS/NTFS[/COLOR]
/dev/sdb6            5889        6374     3903763+  82  Linux swap / Solaris
/dev/sdb7               1        5106    41013850+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)
```
I think I see your problem, JayN. Your Windows XP is installed into a logical partition, sdb5. Windows doesn't normally like to be booted from a logical partition, only a primary one, but it can be done. It would be helpful to know how Windows ended up in a logical partition though: did you actually install Windows to sdb5 or did you move it there from some other partition at some point? 

Anyway, the first thing to do would be to use the following entry in your menu.lst: 
```
title 		XP
rootnoverify	(hd0,4)
chainloader +1
```
Note that the above entry doesn't use "makeactive", because Grub can't make a logical partition active. Also note that since your Ubuntu boots fine, and the menu.lst entries for Ubuntu use (hd0,6), that means you must be booting from the Ubuntu HDD; therefore even though Windows and Ubuntu are on the sdb disk, Grub will see them both on (hd0) since Grub goes by boot order, not the device order in linux.

The next step will be to check if you have all the files in Windows necessary to boot:
```
boot.ini
ntldr
NTDETECT.COM

```
So try the following:
```
sudo umount /dev/sdb5  [COLOR="Blue"][don't worry if it returns an error, this is just to make sure sdb5 isn't mounted all ready somewhere else][/COLOR]
sudo mount /dev/sdb5 /mnt
ls -l /mnt
```
Do you see the three files listed above in your directory listing? Let me know whether you do or not, but regardless, just download the boot files that I've attached to this post and put them in your Windows root directory (let them overwrite the ones that you may have there). I've made sure the boot.ini file I'm sending you should work with your partition structure, so you need to use the ones I've attached to this post.

Let me know how it goes, and if you get any new errors. :)

---

### Post by kansasnoob on 2008-09-08
> **jayN said:**
> the same error 22 comes up but if i type this in

title 		Windows XP
root		(hd0,4)
chainloader +1

it just gets stuck at a blank screen with "starting up..." 

don't know if that helps but any other help you can give me would be good

I'm sure Caljohnsmith is onto something here!

In those cases where "it just gets stuck at a blank screen with "starting up..." " I'll bet it is a Windows NTLDR problem rather than a Grub problem.

I wish we had created a backup of your original menu list, but since we only messed with Windows entries it'll be fairly easy to fix.

---

### Post by jayN on 2008-09-08
> **caljohnsmith said:**
> 
Do you see the three files listed above in your directory listing? Let me know whether you do or not, but regardless, just download the boot files that I've attached to this post and put them in your Windows root directory (let them overwrite the ones that you may have there). I've made sure the boot.ini file I'm sending you should work with your partition structure, so you need to use the ones I've attached to this post.

Let me know how it goes, and if you get any new errors. :)

i did all that you told me to, i saw the 3 files after downloading them from the link you gave me and copying them onto the windows hard drive, but im still stuck at the black screen which says "starting up..."

---

### Post by garyed on 2008-09-08
I don't have any answers but I have a question for anyone in the know.
Could the fact that there is no sdb1 partition have anything to do with the problem? I don't understand why its not there.

---

### Post by caljohnsmith on 2008-09-08
> **jayN said:**
> i did all that you told me to, i saw the 3 files after downloading them from the link you gave me and copying them onto the windows hard drive, but im still stuck at the black screen which says "starting up..."
OK, one thing that could still be messed up is the Windows partition boot record (PBR); if you have your Windows Install CD, just boot it up, go to the "recovery console" and run the command "fixboot". Try rebooting again into Windows, and let us know what errors you might get.

Also, to ask again, how did Windows end up on that logical partition? It would help to know that for troubleshooting your problem.

---

### Post by jayN on 2008-09-08
i pretty sure i installed it on a logical partition

oh and how do you get into the recovery console from the xp cd?

---

### Post by cp1969 on 2008-09-08
It will be one of three choices that comes up: Install, repair, exit.

---

### Post by jayN on 2008-09-08
i went into the repair menu and typed fixboot and this message came up:

fixboot cannot find the system drive, or the drive specified is not valid

anyone know what that means?

---

### Post by caljohnsmith on 2008-09-09
When you boot the Windows CD and get the main menu, just press "r" to get the recovery console; did you do that? Also, if it still won't let you run fixboot, try "map" to see your list of drives, find the one that is Windows, and then do "fixboot <drive>", for example "fixboot C:". Does that work?

---

