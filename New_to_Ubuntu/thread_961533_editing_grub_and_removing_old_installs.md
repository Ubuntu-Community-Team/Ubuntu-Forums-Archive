---
title: "editing grub and removing old installs"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by cykotiktek on 2008-10-28
I would like to remove some old installs from grub or the computer all together and i want my intrepid ibex to be the first option to boot to.  Personally i don't care but when my wife goes to use the computer she gets confused with all the crap loading when grub comes up and she chooses the wrong one frequently and i get yelled at.  

So remove old installs of ubuntu and editing grub so that intrepid is the first on the list so it defaults to it would be great.

---

### Post by TeoBigusGeekus on 2008-10-28
Could you please post us the output of
```
sudo gedit /boot/grub/menu.lst
```
(menu.Lst)

---

### Post by dracayr on 2008-10-28
the file you have to edit is /boot/grub/menu.lst. You have to have root rights to edit that file, so do it with ```
sudo gedit /boot/grub/menu.lst
``` scroll down to the first lines that don't have a '#' in front of them. These are the lines grub reads (the rest, with the '#', are comments). The system isn't very complicated, I'm sure you'll see how to change positions.

dracayr

---

### Post by oldos2er on 2008-10-28
Use Synaptic Package Manager to uninstall old kernels.

---

### Post by cykotiktek on 2008-10-28
that is the output for menu.lst 




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
# kopt=root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,4)
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

### Post by cykotiktek on 2008-10-31
el bump0

---

### Post by JKyleOKC on 2008-10-31
To simplify things for your wife's use, first open menu.lst as described in post #3 above. Then scroll down to find these lines:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
Change the last line by removing the "#" so that they read:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
Now save the file.

The result will be that the grub menu no longer shows up at all, and the timeout will automatically load from the first item listed. If you want it to automatically open some other item instead, change the "default" line near the top of the file to something other than "0".

When you're booting and want to see the menu, just press the ESCape key at the start and it will appear.

---

### Post by drs305 on 2008-10-31
Here is a link to a tutorial on StartUp-Manager. I originally entitled it: "Grub Menu Kernel Display Options" because new users were surprised by a growing number of kernels displayed in grub's boot menu. I quickly found that StartUp-Manager corrected this and many other boot options which interested new users.

[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177") 

Removing old kernels is covered in Section 7. You can uninstall them via synaptic or simply hide them from appearing in the menu via StartUp-Manager.

---

### Post by Duck2006 on 2008-10-31
> sudo gedit /boot/grub/menu.lst

Should be,

gksudo gedit /boot/grub/menu.lst

To just view the file should be,

cat /boot/grub/menu.lst

---

### Post by cykotiktek on 2008-10-31
ok i can do that but how do i change the first item that will load in grub?  currently it's a fresh install that i have never even bothered to log into i would actually like to remove it entirely

---

### Post by CowzRule on 2008-11-01
Under the line > ## ## End Default Options ##Change it so it looks like> title Ubuntu 8.10, kernel 2.6.27-4-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.27-4-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro quiet splash
initrd /boot/initrd.img-2.6.27-4-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.27-4-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro single
initrd /boot/initrd.img-2.6.27-4-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=b943ebe8-ffe0-4537-90a6-f9bed9923a7f ro single
initrd /boot/initrd.img-2.6.27-7-generic
Then look for the following section
> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
Change the last line so it reads> # howmany=1
That will give you a grub menu that looks like
> Ubuntu 8.10, kernel 2.6.27-4-generic
Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)

---

