---
title: "Boot problems - grub infinite loop"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by mrkaic on 2008-06-18
I have a problem booting my machine. It often gets stuck in what seems to be an infinite loop -- the bar showing boot progress on the screen keeps circling around, sometimes for hours. I have to press CTRL-ALT-DEL to reboot the machine in in order to break the cycle. Sometimes I have to reboot 4 or more times, before the system really gets loaded.

I noticed the problem after I had played with a live minix 3 CD. Could there be a connection? I have a Dell Inspiron 530, which came with Ubuntu 7.10 and initially I had no problems booting.

Please help, the problem is very annoying.

Thanks,

Mico

---

### Post by Hospadar on 2008-06-18
Could you post a copy of you /boot/grub/menu.lst file?  Probably too, you may want to try booting manually (which I or someone else can help you with) so you can disable the quiet boot and see what's really going on.  Probably it's some component freezing things up during boot.

---

### Post by Nero147 on 2008-06-18
I would agree with Hospadar, the menu.lst would be good to have. Just boot from a live cd and copy it that way. Also when you say that the status bar on the boot screen, do you mean the ubuntu status bar, or your BIOS screen? because if it is your Ubuntu screen hit ctrl-alt-F1 and you will get a verbatim readout of what's happening. If it's your BIOS screen then you might want to try running some diagnostics because your boot sectors might be bad (or your HD). regardless of that though your easiest fix would probably be reinstalling grub manually. However this is only good if you don't have a bunch of OS's. The walkthrough I always use is here. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mrkaic on 2008-06-18
Thank you, will post the menu.lst file. The infinite cycle shows on the ubuntu status bar, not on the BIOS screen.

If all else fails, I will reinstal grub, I don't have a bunch of OS's, only ubuntu.

---

### Post by prshah on 2008-06-18
> **mrkaic said:**
> I have a problem booting my machine. It often gets stuck in what seems to be an infinite loop -- the bar showing boot progress on the screen keeps circling around, 

When your ubuntu status bar starts up, press Ctrl+Alt+F8 to go to a diagnostic screen (initially blank). This will give you messages about what's going on while Ubuntu's starting up. Maybe those messages will give you a clue as to what's going on. Post back any suspicious looking messages for more help.

---

### Post by mrkaic on 2008-06-18
Below is my menu.lst file. Please help if you spot any problems.


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7391ac5d-6721-43a4-b52b-1d51caa5fa8f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1

---

### Post by tjwoosta on 2008-06-18
i hate to say it but if you can get as far as the ubuntu loading screen then grub is not the problem

this has happened to me before, i simply ran ubuntu in recovery mode and when i rebooted everything worked agian

hope this helps:)

---

### Post by mrkaic on 2008-06-19
Thank you all. I noticed something unusual: whet the splash screen gets "stuck" in a loop, I pressed CTRL-ALT-F8 and the system started loading immediately. It seems that I don't have a completely clean solution, but at least a serviceable.

---

### Post by prshah on 2008-06-19
> **mrkaic said:**
> Thank you all. I noticed something unusual: whet the splash screen gets "stuck" in a loop, I pressed CTRL-ALT-F8 and the system started loading immediately. It seems that I don't have a completely clean solution, but at least a serviceable.

I have a similar problem, because of this, I've modified my grub menu.lst file to boot without splash screen. Maybe you should do this too.```
sudo gedit /boot/grub/menu.lst
``` then find the line that you use to boot, and remove "quiet splash" from the end of it. Eg> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4bce0fa6-bf3b-43dc-bd3c-9aac9b0d4eed ro [color=red]quiet splash[/color]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
Then ```
sudo update-grub
```

---

### Post by Nero147 on 2008-06-19
also you might try adding noapic to the end.
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=4bce0fa6-bf3b-43dc-bd3c-9aac9b0d4eed ro quiet splash noapic

---

