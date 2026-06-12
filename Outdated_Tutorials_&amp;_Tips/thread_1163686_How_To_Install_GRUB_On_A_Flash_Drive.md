---
title: "How To Install GRUB On A Flash Drive"
date: 2009-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by reevine on 2009-05-18
Hello peoples,

[INDENT]The reason i wanted GRUB on a flash drive is because i have Windows Vista and there is a recovery partition on my hard drive also that i have needed to use a couple of times (because Vista sucks and corrupts itself every-once-in-a-while)[/INDENT]

So i wanted GRUB because i can boot into that partition from there.

Now i have Ubuntu installed on my Toshiba laptop and i didnt want to run Ubuntu on my Sony VAIO (the one with Vista) because i run Ubuntu from my Sony via Virtual Server Network (VSN) which is connected to my Toshiba which is what the VSN runs from.

so i needed to separate GRUB from Ubuntu. So looking around i found some info and took my own info that i already had and combined all the information to put together what i wanted; an independent GRUB system that doesn't need Ubuntu.

now to start off. first install Ubuntu and boot into it after installation. The reason we do this is so that we can have our Grub system build itself instead of having to build it ourselves.

after you do that go to Terminal and do the following steps (some of the letters look alike so please copy and paste if need  be.):

1. First we are going to take a flash drive we don't use and delete all the data on it.
2. then we are going to make some directories. This is where we will put the GRUB files at. so mount your flash drive. look at what the name of the drive is. you can rename it if need be for easier access. im going to use USB for the name of the flash drive but please enter the name of your drive in place of that. enter the following command:

```

sudo mkdir /media/USB/boot

```

this will put a folder in your flash drive named "boot".

3. We are going to copy the GRUB files into the drive. enter the following:

```

sudo cp -r /boot/grub /media/USB/boot/

```

4. we are going to access the main file that tells GRUB what to do. enter the following:

```

gksudo gedit /media/USB/boot/grub/menu.lst

```

this will open the menu.lst file.

5. we are now going to edit the menu.lst file. Now that we have the file we need, we are going to edit how GRUB will look and what will be in it. this will be to take out the Ubuntu partition listings because all i want is the recovery drive and the main windows partition.
_________________________________________________________________

From here we are going to be changing things in the menu.lst file.

here is what you should have or something similar depending on what you have for partitions:

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
## 
## Start Default Options 
##
## default kernel options

## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8cfd73a3-5d46-41d0-beff-de66a0513019

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

## 
## End Default Options 
##


title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other Operating Systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
rootnoverify	(hd1,1)
savedefault
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery
rootnoverify	(hd1,0)
savedefault
chainloader	+1
 
```

now we are simply going to look at one section of this file and edit it. We are going to make the Ubuntu options go away and make it so it auto loads windows.

this is the section that we will be looking at:

```


title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other Operating Systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
rootnoverify	(hd1,1)
savedefault
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery
rootnoverify	(hd1,0)
savedefault
chainloader	+1


```

ok so if you look there is the Vista partition and the Recovery partition i was talking about. Now depending on what you are doing with GRUB you will have to edit it differently.
if you look there are Pound symbols (#) floating around in there. the reason those are there is so that what is typed in wont be "seen" by GRUB. # is used for making a comment and when grub accesses this file it overlooks the comments. now to get rid of the ubuntu partions we will put # next to them instead of just deleting them. that way they are still there in case you need them. now i customized it so that windows is loaded first and have the recovery partition below a section.

so this is what mine looks like:

```


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
rootnoverify	(hd1,1)
savedefault
chainloader	+1


title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Recovery Options:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery
rootnoverify	(hd1,0)
savedefault
chainloader	+1


#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8cfd73a3-5d46-41d0-beff-de66a0513019 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic


#title		Ubuntu 9.04, memtest86+
#uuid		8cfd73a3-5d46-41d0-beff-de66a0513019
#kernel		/boot/memtest86+.bin
#quiet


```

so it should look like this when GRUB boots up depending on what you did:

```

Windows Vista

Recovery Options:

Windows Vista Recovery

```
_________________________________________________________________

now to start on installing GRUB to this partition:

1. open terminal
2. type:

```

sudo grub

```

3. type:

```

find /boot/grub/stage1

```

something like this should have come up:
```

grub> find /boot/grub/stage1
find /boot/grub/stage1
[INDENT](hd0,1)[/INDENT]
[INDENT](hd1,0)[/INDENT]

```

now the first drive listed: (hd0,1) will differ depending on how your system is set up. but (hd1,0) should be correct.

4. type:

```

root (hd1,0)

```

that just told grub to look at your flash drive files instead of the ones in Ubuntu

5. type:

```

setup (hd1)

```

that will install GRUB on your flash drive.

6. exit Terminal
_________________________________________________________________

now in order to fix your Windows MBR pop in your Windows installation CD and go to the Recovery console and type the following:

```

fixmbr

```

now if you have trouble with fixing windows just search the forums for help and you should easily find what you are looking for.
_________________________________________________________________

[INDENT]Sincerely Reevine[/INDENT]
[INDENT]:D[/INDENT]

P.S. this is my first tutorial so if the instructions are kinda rough please be patient. i will release a smoother, easier, and more organized one soon. oh and i heard that there is a tutorial similar to this. when i find I'll add the link.

---

### Post by ndeubert on 2010-03-31
Thank you for posting this, this is exactly what I was looking for and worked perfect as far as booting grub. Unfortunately it won't load my Dell recovery partition, I get: "Error 18: Selected Cylinder exceeds maximum supported by BIOS" every time. Any idea what that means in this context? I tried all different devices: hd0,0-4 hd1,0-4. (I think my usb drive im booting off actually shows up as hd0 and hd1 is my real drive with the 3rd partition being the recovery one.

---

### Post by reevine on 2010-04-03
> **ndeubert said:**
> Thank you for posting this, this is exactly what I was looking for and worked perfect as far as booting grub. Unfortunately it won't load my Dell recovery partition, I get: "Error 18: Selected Cylinder exceeds maximum supported by BIOS" every time. Any idea what that means in this context? I tried all different devices: hd0,0-4 hd1,0-4. (I think my usb drive im booting off actually shows up as hd0 and hd1 is my real drive with the 3rd partition being the recovery one.
sure no problem!! ok so for your booting problem: well there are two issues here. first is the fact that you dont have the excact Hard Drive information. this can lead to problems. I believe i had a section on this but took it out. i will look into my plethora of notes ;). now as for the booting error! well i think its just cause your computer sucks... thats all there is to it! hahahaha srry jk! ok well it could be the way dell set up the partition. GRUB may be interfearing with the partition bootup. does it boot any other partitions? if so then its definitely dell's fault for how they set up the partition. oh another question: what version of grub are you using? (2.0? or older version)

---

### Post by ndeubert on 2010-04-06
> **reevine said:**
> sure no problem!! ok so for your booting problem: well there are two issues here. first is the fact that you dont have the excact Hard Drive information. this can lead to problems. I believe i had a section on this but took it out. i will look into my plethora of notes ;). now as for the booting error! well i think its just cause your computer sucks... thats all there is to it! hahahaha srry jk! ok well it could be the way dell set up the partition. GRUB may be interfearing with the partition bootup. does it boot any other partitions? if so then its definitely dell's fault for how they set up the partition. oh another question: what version of grub are you using? (2.0? or older version)

I was using 1.9x i believe (it came from a 8.10 install i believe). It wouldn't boot the other partitions either. Unfortunately I gave up and just installed windows from the cd instead of trying to "recover" the recovery partition. thanks anyway, it is neat to have grub on the usb at least.

---

### Post by reevine on 2010-04-07
oh i am srry that it didnt work. yah if it didnt boot any of the other partitions then its because the Hard drive ID was wrong. one draw back to having grub is that in order for it to recognize a partition you must add it in the menu.lst. im working on seeing if i can patch together an additive so that GRUB can be adaptive and actually scan for partitions available. then GRUB would be the ULTIMATE BOOT LOADER!!! hahaha so if i do complete and succeed in that i will post another tut on how to compile the new files into the GRUB OS

---

### Post by Ferk on 2010-09-08
> **reevine said:**
> oh i am srry that it didnt work. yah if it didnt boot any of the other partitions then its because the Hard drive ID was wrong. one draw back to having grub is that in order for it to recognize a partition you must add it in the menu.lst. im working on seeing if i can patch together an additive so that GRUB can be adaptive and actually scan for partitions available. then GRUB would be the ULTIMATE BOOT LOADER!!! hahaha so if i do complete and succeed in that i will post another tut on how to compile the new files into the GRUB OS

Try Super Grub Disk 2 (at [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/))
It can autodetect installed OS, grub installations and it even ISOs to load from.

---

