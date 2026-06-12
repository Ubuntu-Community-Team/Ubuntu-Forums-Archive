---
title: "[SOLVED] my startup progress bar missing!!!"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by macvr on 2008-08-29
hi, 
i'm new to ubuntu.

i'm not sure how to bring back the startup progress bar.

it was working fine till yday, but 2day i just get the list of process in the terminal during startup, no progress bar!

but the usplash[i think that i what it is called], the initial ubuntu black screen with the moving bar is displayed. 

i'v tried:```
sudo dpkg-reconfigure usplash
```

but didnt have any effect!

---

### Post by Sam Lars on 2008-08-29
I've had my usplash disappear a while ago, I never got around to doing anything about it.
You say that you just get the process list, not the progress bar, but you get the black screen with the progress bar?  Which is it?

---

### Post by Oldsoldier2003 on 2008-08-29
try looking at this thread. [http://ubuntuforums.org/showthread.php?t=901254](http://ubuntuforums.org/showthread.php?t=901254) It should sort you out as well as give some insight into the problem. There are a few things that can cause quiet boot to stop happening. Usually changing your grub boot options fixes it but the guy in this thread had other issues too.

---

### Post by macvr on 2008-08-29
> **Sam Lars said:**
> I've had my usplash disappear a while ago, I never got around to doing anything about it.
You say that you just get the process list, not the progress bar, but you get the black screen with the progress bar?  Which is it?
its the sweeping bar that i see initially, after that its the verbal boot

> **Oldsoldier2003 said:**
> try looking at this thread. [http://ubuntuforums.org/showthread.php?t=901254](http://ubuntuforums.org/showthread.php?t=901254) It should sort you out as well as give some insight into the problem. There are a few things that can cause quiet boot to stop happening. Usually changing your grub boot options fixes it but the guy in this thread had other issues too.
its like its said no that thread,
i had ONLY resized a ntfs partition
so i checked via partition manager, i found  that the swap partition has been now modified to unallocated

so i changed the unallocated space[previous swap space]
i did the following, using partition manager
"new partition> logical drive> swap partition> switched on swap"
is this correct?

_but on every restart i find that the swap does not get mounted!!!_

i checked the fstab but its the same as it was before i had this problem.

i'm not sure what to edit the initramfs-tools/conf.d/resume ?

how do i proceed?

---

### Post by Oldsoldier2003 on 2008-08-29
if your swap isn't being mounted there is a good chance it is because the UUID of the swap is wrong:

```
ls -alh /dev/disk/by-uuid

```

and check it against your fstab
Edit:
"i checked the fstab but its the same as it was before i had this problem." would indicate to me it hasn't been updated since the UUID would be changed when you redid the swap.

---

### Post by macvr on 2008-08-29
> **Oldsoldier2003 said:**
> if your swap isn't being mounted there is a good chance it is because the UUID of the swap is wrong:

```
ls -alh /dev/disk/by-uuid

```

and check it against your fstab
Edit:
"i checked the fstab but its the same as it was before i had this problem." would indicate to me it hasn't been updated since the UUID would be changed when you redid the swap.

i manually edited the fstab, with the results from the above command, now my swap gets mounted at startup
but i still have the same verbal boot only

have i missed to update it somewhere else?

---

### Post by tangibleorange on 2008-08-29
> **macvr said:**
> i manually edited the fstab, with the results from the above command, now my swap is mounted but i still have the same verbal boot only

have i missed to update it somewhere else?

try:

```
sudo update-initramfs -u
```

that magical command seems to fix all bootsplash problems :)

---

### Post by macvr on 2008-08-29
> **tangibleorange said:**
> try:

```
sudo update-initramfs -u
```

that magical command seems to fix all bootsplash problems :)
didnt work for me:(

still its verbal boot :confused:

---

### Post by tangibleorange on 2008-08-29
```
sudo apt-get purge usplash-theme-ubuntu
sudo apt-get install usplash-theme-ubuntu
sudo update-initramfs -u
```

then reboot. if that doesn't work, post the output of:

```
cat /etc/usplash.conf
cat /boot/grub/menu.lst
```

---

### Post by macvr on 2008-08-29
the purge and reinstall didnt work:(

> **tangibleorange said:**
> 
```
cat /etc/usplash.conf
```

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=800

```

> **tangibleorange said:**
> 
```
cat /boot/grub/menu.lst
```

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
timeout		1

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
# kopt=root=UUID=35d1037f-c973-4a71-b24f-e1195e33c1a6 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=35d1037f-c973-4a71-b24f-e1195e33c1a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=35d1037f-c973-4a71-b24f-e1195e33c1a6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
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
title		Microsoft Windows XP HOME
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by tangibleorange on 2008-08-29
hmm well i'm afraid i'm out of ideas. everything in the files looks good, so I don't know what's wrong...

---

### Post by macvr on 2008-08-29
fixed,
 from the thread that oldsoldier had given, got to another thread, and the solution was there

[http://ubuntuforums.org/showpost.php?p=5377919&postcount=5]("http://ubuntuforums.org/showpost.php?p=5377919&postcount=5")

it turns out that i had to manually edit the /etc/initramfs-tools/conf.d/resume file and change the UUID there also...[stupid Microsoft had to mess up my config!!! when all i did was just resize the ntfs!]

now the progress bar is displayed...

thanx for the help guys

---

