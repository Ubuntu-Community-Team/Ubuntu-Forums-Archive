---
title: "[SOLVED] Computer doesn't shut down"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-28
When I go to shut down my computer, it just makes the screen go black and nothing happens. I use the shutdown icon, not a command or anything. I don't get why it's happening, and I don't really like it cause I gotta force a shutdown by holding the power button. also, alt+ctrl+backspace doesn't work.

---

### Post by jualin on 2008-09-28
Go to the terminal and type > sudo shutdown -h now and check if your computer shuts down correctly.

---

### Post by bumanie on 2008-09-28
Don't know the cause of that other than assuming there is a process that is not turning off. Try command > sudo shutdown -h now and see whether that works. It's not as convenient as clicking a button, but it is better than a hard shutdown.

---

### Post by ronnielsen1 on 2008-09-28
Do you get a message when it's booting about your bios being old and acpi=force needs to be enabled?

If so, you need to:

gedit /boot/grub/menu.lst

in a root terminal and add 
acpi=force

---

### Post by adobrakic on 2008-09-28
```

sudo shutdown -h now

```

didn't work, i just got some error in terminal but the screen went black right away so i couldn't see what it was. Also, I'm not sure about the acpi thing, but I'll go check. If it does say that, where in menu.lst would I add it?

---

### Post by ronnielsen1 on 2008-09-29
> didn't work, i just got some error in terminal but the screen went black right away so i couldn't see what it was. Also, I'm not sure about the acpi thing, but I'll go check. If it does say that, where in menu.lst would I add it?
at the end. I had to use this on a couple of computers

---

### Post by nowshining on 2008-09-29
> **adobrakic said:**
> ```

sudo shutdown -h now

```

didn't work, i just got some error in terminal but the screen went black right away so i couldn't see what it was. Also, I'm not sure about the acpi thing, but I'll go check. If it does say that, where in menu.lst would I add it?

how long do u wait for it to shutdown?? do u try waiting a minute or two before being so quick to press and hold the power button?

---

### Post by angelsguitar on 2008-09-29
After you check for the acpi message, you can post the contents of your menu.lst and we can tell you where to add the line, if in doubt.

Another way around the acpi problem is to add the following line to etc/modules file:

```
apm power_off=1
```

I would suggest you first try the menu.lst modification and, if it doesn't work, try the etc/modules modification.

---

### Post by adobrakic on 2008-09-29
> **nowshining said:**
> how long do u wait for it to shutdown?? do u try waiting a minute or two before being so quick to press and hold the power button?

Once I let it sit overnight, now I wait like 30 seconds.

> **angelsguitar said:**
> After you check for the acpi message, you can post the contents of your menu.lst and we can tell you where to add the line, if in doubt.

Another way around the acpi problem is to add the following line to etc/modules file:

```
apm power_off=1
```

I would suggest you first try the menu.lst modification and, if it doesn't work, try the etc/modules modification.

My menu.lst: 

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(recovery mode) single
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

title		Linux Mint, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Linux Mint, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by anewguy on 2008-09-30
In a terminal window:

cd /boot/grub/ <enter>

sudo gedit menu.lst

find the first kernel line that isn't commented out (after the ## ## End Default Options ##):

kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash


add the following to the end:

<space> acpi=force  where <space> means just press the space bar.

Your line should then look like this:

kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash acpi=force


Save the file, exit and reboot, then try shutdown.

Dave :)

---

### Post by adobrakic on 2008-10-01
ah, this worked flawlessy. thank you!!

---

### Post by angelsguitar on 2008-10-01
Glad you solved your issue:D

---

