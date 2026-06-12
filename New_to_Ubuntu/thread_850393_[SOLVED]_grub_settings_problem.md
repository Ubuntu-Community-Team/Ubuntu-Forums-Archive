---
title: "[SOLVED] grub settings problem"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by freak42 on 2008-07-05
I setup xubuntu on a neighbours laptop.
It had a problem, it didn't display the login screen.
I found a solution on the web that said to remove splash and quit options from the kernel boot line, which I did.
Now I have the most strange behaviour which I cannot explain:
When I let the computer boot withouth going into the grub menu the computer won't display the login screen... however when I go into the grub menu and select the top entry (which I thought would be the same as the default selected by grub) then the login screen works like it is supposed to.

So my question is: What is the difference between letting grub chose the startup and choosing the first entry manually.. from what I see this should be absolutely identical?

Here is my menu.lst from /boot/grub/
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

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=50d95497-287e-4e90-a77f-cf20581c268c ro

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
# defoptions=

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50d95497-287e-4e90-a77f-cf20581c268c ro
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50d95497-287e-4e90-a77f-cf20581c268c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=50d95497-287e-4e90-a77f-cf20581c268c ro
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=50d95497-287e-4e90-a77f-cf20581c268c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

thanks in advance for any help!

---

### Post by phidia on 2008-07-05
You're right they should be identical. I don't know why you are getting that but this: > It had a problem, it didn't display the login screen.
I found a solution on the web that said to remove splash and quit options from the kernel boot line, which I did. is an indication of some problem with the orginal install.
Did you check the md5sum of the download and did you check the cd's integrity (available from the boot menu)?

---

### Post by drs305 on 2008-07-05
When you say that you let the computer boot without going into the grub menu on it's own is it still showing the grub menu for 10 seconds and then continuing without input?

If not, how are you getting to the grub menu to make the choice which allows you to get to the log-on screen?

Also, you could take a look at StartUp-Manager if you have it installed and see which kernel it shows as the default in Boot Options.

---

### Post by freak42 on 2008-07-05
> **phidia said:**
> Did you check the md5sum of the download and did you check the cd's integrity (available from the boot menu)?

yes, I did.
I agree that the problem of the splash screen is ultimately somewhere else, however if removing quiet and splash helps, that's fine with me, I am just wondering what really is happening during this boot stuff.

---

### Post by spiderbatdad on 2008-07-05
There is not likely a problem with the original installation. acpi handling of irq interrupts and other hardware incompatibilities often require the modification you have used. Additionally other boot options are often necessary in place of quiet splash.

You could run this command:```
dmesg > ~/Desktop/dmesg.txt
```right click the file that gets written to the desktop and select "create an archive."
Upload that archive here, with the manage attachment tool below.

---

### Post by alienexplorers on 2008-07-05
change this line:
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

to look like this:
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10


---

### Post by alienexplorers on 2008-07-05
Disregard this post!

---

### Post by freak42 on 2008-07-05
thank you all for your replies...

upon further inspection I am not so sure anymore that it is really a problem related to grub. Because the behavior or success rate of starting the splash screen is also changing wile using the default boot (without intervention) of grub. 
dmesg output implies that grubs kernel line is the same whether the default line is selected by hand or automatically by grub (as usually expected)... My findings described above are either simply wrong or it was just a bad coincidence that the behavior changed. Either way I will have to look into other things, but I have to postpone it because after 8 hrs I am fed up with this computer.

Again,thanks to all for your replies and help! It is always nice seeing how people help here on the ubuntu-forums.

I am marking this read as solved due to the problem probably never existing as described above. (sorry again)

---

