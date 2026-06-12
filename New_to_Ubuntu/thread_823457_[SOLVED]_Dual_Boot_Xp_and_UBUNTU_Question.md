---
title: "[SOLVED] Dual Boot Xp and UBUNTU Question"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by appoloin on 2008-06-09
I have setup mu comp with dual boot XP and UBUNTU. I have been noticing that everytime i boot up the list the i have to choose to bootup on XP or UBUNTU seems to increase. is it doing a backupor something? if so anyway i can clean this up?

---

### Post by SunnyRabbiera on 2008-06-09
you mean you are getting more entries in the bootloader correct?

---

### Post by appoloin on 2008-06-09
yes thats it

---

### Post by miss.magenta on 2008-06-09
when you update your kernel, there will often be a new entry in your grub conf file for that new kernel version.  to remove the older versions from the list edit

/boot/grub/menu.lst

to either totally remove or comment out the items you don't want to appear in the list

---

### Post by appoloin on 2008-06-09
So i should just leave it then?

---

### Post by ukripper on 2008-06-09
> **appoloin said:**
> I have setup mu comp with dual boot XP and UBUNTU. I have been noticing that everytime i boot up the list the i have to choose to bootup on XP or UBUNTU seems to increase. is it doing a backupor something? if so anyway i can clean this up?

I believe you are looking at grub menu at bootup. Whenever there is kernel updates and new kernel is added to your menu list. If you want to remove the previous kernels from grub menu, you would need to remove the previous kernels not in use by you.

go to synaptic package manager and type linux kernel and find the kernels marked with green. **[COLOR="Red"]Warning:[/COLOR]** only remove which you dont want! it wil be something like kernel-2.6.24.16
just remove the unwanted ones.

if you are using the latest kernel from package manager then it will be 2.6-24-19 and dont remove that one and keep the 2.6-24-18 just as a backup and rest you can remove.

After you have finished with it. Go to terminal and run following command to update your grub entries:

```
sudo update-grub
```

---

### Post by appoloin on 2008-06-09
sorry for this dumb question but this is the one right? Kernel Logging Daemon

---

### Post by ukripper on 2008-06-09
> **appoloin said:**
> sorry for this dumb question but this is the one right? Kernel Logging Daemon

no it should give you something like that
2.6.24.16 generic

Do not remove kernel logging daemon or anything else without knowing.

---

### Post by miss.magenta on 2008-06-09
You don't need to remove the unused kernels - you are much safer just editing grub's menu.  it's a whole lot easier and less stressful to put back a backup of a single conf file than it is to reinstall your system because you accidentally removed the wrong kernel.

---

### Post by arckeda on 2008-06-09
They are your older kernels, you can boot into them if there is a problem with your current one...  Though they are kind of useless.

If you want to remove them from your list comment them out with the "#" symbol in:

/boot/grub/menu.lst

CHEERS!
     -ARCKEDA

---

### Post by appoloin on 2008-06-09
ok i got this when i did the upgrade grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


im sure i can get rid of some of them

right?

---

### Post by ukripper on 2008-06-09
Then everytime you have to edit menu.lst whenever grub entries are changed which is just extra work. Make sure the kernels you don't need just remove them and it just simple. or easier way to go about is. change a setting in menu.lst to limit your kernel entries.

Ok let me tell you easier way. just post your /boot/grub/menu.lst here and we will change it for you and and then you can replace it after we have changed.

---

### Post by meierfra. on 2008-06-09
Click on drs305 in my signature for a very nice HowTo on this subject.

---

### Post by ukripper on 2008-06-09
> **appoloin said:**
> ok i got this when i did the upgrade grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


im sure i can get rid of some of them

right?

That is not many entries. In my opinion you don't need to remove anything.

---

### Post by appoloin on 2008-06-09
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
# kopt=root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by miss.magenta on 2008-06-09
to keep just the current kernel and your xp in the list:

<snip>


title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
initrd /boot/initrd.img-2.6.24-19-generic

#title Ubuntu 8.04, kernel 2.6.24-18-generic
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=cf667e2e-87ef-4e2b-#8b2e-d066c7b7f48f ro quiet splash
#initrd /boot/initrd.img-2.6.24-18-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
#initrd /boot/initrd.img-2.6.24-18-generic

#title Ubuntu 8.04, kernel 2.6.24-17-generic
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
#initrd /boot/initrd.img-2.6.24-17-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
#initrd /boot/initrd.img-2.6.24-17-generic

#title Ubuntu 8.04, kernel 2.6.24-16-generic
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro quiet splash
#initrd /boot/initrd.img-2.6.24-16-generic
#quiet

#title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=cf667e2e-87ef-4e2b-8b2e-d066c7b7f48f ro single
#initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by ukripper on 2008-06-09
> **appoloin said:**
> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
**# howmany=all**


Just replace the above bold line to this:
```
**# howmany=3**
```

save and exit and run 
```
sudo update-grub
```

you all done and you will have only three kernel entries.

---

### Post by appoloin on 2008-06-09
should i copy and paste this?

---

### Post by ukripper on 2008-06-09
> **appoloin said:**
> should i copy and paste this?

yeh just copy paste 

# howmany=3

leave evrything else as it is

---

### Post by appoloin on 2008-06-09
i tried to change it from 7 to 3 and it says i dont have permission how. funny thing is im the only one that log in to this. why is that?

---

### Post by ukripper on 2008-06-09
> **appoloin said:**
> i tried to change it from 7 to 3 and it says i dont have permission how. funny thing is im the only one that log in to this. why is that?

you need to use sudo;

```
sudo gedit /boot/grub/menu.lst
```

and change #howmany=all to #howmany=3

---

### Post by appoloin on 2008-06-09
done!!! i love you all Thank you for your help

---

### Post by ukripper on 2008-06-09
No probs.

Have you done ```
sudo update-grub 
```after that?

---

### Post by appoloin on 2008-06-09
yeah i have

---

