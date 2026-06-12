---
title: "2 drives 2 os's"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by grewolf on 2008-11-14
Is there any way that I can switch back and forth between XP and Ubuntu without having to go into my bios to change my boot device.  I have 2 hard drives one with xp on it and one with Intrepid Ibex on it.  The info I have read on dual booting is if I want both operating systems on one hard drive.

---

### Post by SuperSonic4 on 2008-11-14
Boot up the ubuntu hard drive

you can install grub from the ubuntu live cd and there will be an entry for XP

---

### Post by Duck2006 on 2008-11-14
From the live cd in the terminal,

sudo grub
find /boot/grub/stage1    (the output of this use in the next step)
root (hdx,y)
setup (hd0)
quit

This will setup the grub boot loader, in your mbr of your first drive, to be able to dual boot your system.

---

### Post by louieb on 2008-11-14
> **grewolf said:**
>  The info I have read on dual booting is if I want both operating systems on one hard drive.

Using BIOS is just one way to do it 
Here you go. [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by caljohnsmith on 2008-11-14
As long as you can boot the Intrepid drive, you can simply add an entry in your Grub menu.lst to boot your Windows drive. When you are in Ubuntu, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title	   Windows XP
rootnoverify    (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If you can't yet boot your Intrepid drive, let me know and I can help you install Grub to it if you want. Otherwise let us know how it goes.

---

### Post by grewolf on 2008-11-15
When I get to the grub menu and select the option for windows xp I get ```
[COLOR="Red"]ERROR 13 Invalid or unsupported executable format
[/COLOR]
```

Ok from reading the links that you have provided I feel that maybe I wasn't forthcoming enough with information.  I have 2 Sata drives.  One has XP Pro on it and the other has Intrepid Ibex on it.  I swaped out the drives and loaded them individually.  I also have 2 IDE drives one is a storage drive that I had used for Gutsy Gibbon 7.10 and the Other IDE drive is my Gutsy Gibbon Os.  The Gutsy Os drive became corrupted.  I have it there to try and pull my info off that I require.  

Here is my menu.lst file

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
# kopt=root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd363224-32e5-4cec-824e-4a9dc02367d4

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is to try and dual boot Windows
title              Windows XP
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```



```
jwilson@hopeless:~$ sudo fdisk -l
```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c40061c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080009

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49ace41c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       59477   477748971   83  Linux
/dev/sdc2           59478       60801    10635030    5  Extended
/dev/sdc5           59478       60801    10634998+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc46dc46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60800   488375968+   7  HPFS/NTFS
```

---

### Post by caljohnsmith on 2008-11-15
> **grewolf said:**
> I have 2 Sata drives.  One has XP Pro on it and the other has Intrepid Ibex on it.  I swaped out the drives and loaded them individually.  I also have 2 IDE drives one is a storage drive that I had used for Gutsy Gibbon 7.10 and the Other IDE drive is my Gutsy Gibbon Os.  
Yes, the fact that you have other drives that you didn't mention before is most likely why you are getting that Grub error. :) The problem is that we don't know which drive the XP one is on in the BIOS boot order, so the easiest way to figure out what the correct Grub entry should be is to just try the remaining three combinations:
```

title      Windows XP (hd0)
rootnoverify  (hd0,0)
chainloader +1

title	   Windows XP (hd2)
rootnoverify       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
rootnoverify       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
If none of those entries work, then please let me know exactly what happens when you choose each one from the Grub menu. Otherwise let me know how it goes. :)

---

### Post by grewolf on 2008-11-16
> **caljohnsmith said:**
> 
```


title	   Windows XP (hd3)
rootnoverify       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
If none of those entries work, then please let me know exactly what happens when you choose each one from the Grub menu. Otherwise let me know how it goes. :)

I just wanted to say that this worked for me perfectly.  Thank you

---

### Post by Keen101 on 2008-11-16
I have a desktop machine with two hard drives. When i installed ubuntu i had set the windows drive to SLAVE, and set the empty one as MASTER... when i installed GRUB automatically detected the windows drive and added an option to select it. In your case you could either reinstall or just edit you GRUB bootloader.

other people have commented above as to what to add to your GRUB menu file.

here is how you get to it:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Duck2006 on 2008-11-16
> sudo gedit /boot/grub/menu.lst

Should be

gksudo gedit /boot/grub/menu.lst

---

### Post by caljohnsmith on 2008-11-16
> **grewolf said:**
> I just wanted to say that this worked for me perfectly.  Thank you
You're welcome; glad it was a simple fix. Cheers and have fun with your OSes. :)

---

