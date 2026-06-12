---
title: "Grub Help Needed"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by brookswm on 2008-09-26
I have Grub installed, but for the life of me I cant get Ubuntu to be the primary boot.  Does it matter that I have it installed on my 'second' hard drive?

---

### Post by Nepherte on 2008-09-26
I'm not sure if I get it. Did you install grub on a second hard disk and not the master boot record? If that's the case, just change the order of the boot devices in bios.

---

### Post by brookswm on 2008-09-26
That may have been it, I'll try installing it on the primary hard drive.

---

### Post by caljohnsmith on 2008-09-26
How about posting:
```
sudo fdisk -lu

```
And let us know what drive you are booting from on start up. Then we can give you some better ideas of what your options might be. :)

---

### Post by Nepherte on 2008-09-27
> **brookswm said:**
> That may have been it, I'll try installing it on the primary hard drive.
There's no need to reinstall at all. You can change boot order for your disks in the bios.

---

### Post by brookswm on 2008-10-01
I recently installed Ubuntu on my second HD, WinXP is on the first.  I want to have my computer boot up into Ubuntu, but have not been able to figure out how to do it.  I havent put anything new on the WinXP HD, any tips or advice?

---

### Post by hashimoto on 2008-10-01
> **brookswm said:**
> I recently installed Ubuntu on my second HD, WinXP is on the first.  I want to have my computer boot up into Ubuntu, but have not been able to figure out how to do it.  I havent put anything new on the WinXP HD, any tips or advice?
See instructions here:
[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)
After installing the start-up manager you should be able to change the default OS from Windows to Ubuntu.

---

### Post by uberdonkey5 on 2008-10-01
On 2nd hard-drive? If both operating systems come up in the grub menu you can do this:

[http://ubuntuforums.org/showthread.php?t=927036](http://ubuntuforums.org/showthread.php?t=927036)

without using startup manager (i.e. this is the way to do it with the terminal rather than a gui; its very simple though)

---

### Post by brookswm on 2008-10-01
I think I tried both of what you suggested and was met with no luck.
Here is my info:

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
**default		0**

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
# kopt=root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
# defoptions=quiet splash vga=771

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1
```

I changed the bold to "1," but my primary boot on restart was still Windows XP.

---

### Post by aysiu on 2008-10-01
Based on what I see in there, the number should be **0**, not *1*.

0 is the first entry (Ubuntu)
1 is the second entry (recovery mode)
2 is the third entry (memtest)
3 is the fourth entry (other operating systems title)
4 is the fifth entry (Windows XP)

---

### Post by brookswm on 2008-10-01
This was a mispost, I had 2 windows open and responded to the wrong one.  I'll re-explain:

> I recently installed Ubuntu on my second HD, WinXP is on the first. I want to have my computer boot up into Ubuntu, but have not been able to figure out how to do it. I havent put anything new on the WinXP HD, any tips or advice?

Someone suggested I download a start up manager program and I was also told to edit the menu.lst  I have done both and have had no luck, ever single time if left to its own devices, Windows XP boots up.

---

### Post by hashimoto on 2008-10-02
As far as I can see, everything seems to be OK in your grub. The "default 0" should boot Ubuntu first, but this is obviously not happening.

I'm now guessing here, but try removing the line "savedefault" from the Windows entry. It should not be needed and removing it should not affect anything.

---

### Post by brookswm on 2008-10-02
That's what I was thinking of doing, but being a beginner I didnt want to royally screw my computer.

---

### Post by caljohnsmith on 2008-10-02
I believe that "savedefault" line in the Windows menu.lst entry is exactly what you want to get rid of if you don't want Windows to be your default OS in the Grub menu. :) See the [official Grub manual page on "savedefault"]("http://www.gnu.org/software/grub/manual/html_node/savedefault.html#savedefault") in case you want more information. If you remove that line and then make sure the "default" line at the beginning of your menu.lst is "default 0", then Grub should boot the first Ubuntu entry by default. Is this what you are looking for?

---

