---
title: "[SOLVED] can't change grub boot selection with &amp;quot;sudo grub-reboot &amp;lt;num&amp;gt;&amp;quot;"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by MiniMe on 2008-06-05
Hello,

I'm running a dual boot Hardy and XP system and I'd like to be able to reboot into Windows from Ubuntu by using without having manually select Windows from the grub menu. I usually use Ubuntu so I don't want to change the selection default from Ubuntu to XP.

From this post ([http://ubuntuforums.org/showthread.php?t=310760](http://ubuntuforums.org/showthread.php?t=310760)) I think I can use:

sudo grub-reboot <num>
where <num> is the number of the grub entry item that describes the windows bootsector.

No matter what number I put after "grub-reboot" it doesn't seem to work for me. The 1st entry is always selected in the grub menu.

my /boot/grub/menu.lst file contains the following
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
# kopt=root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=85d8b45c-2ee1-4d6a-91d2-6a23b4f33a44 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I thought that "sudo grub-reboot 8" should cause Windows to be selected in grub but it isn't. In fact no matter what number I enter, the first entry is always selected in grub.

Any help would be greatly appreciated. Thanks in advance.

---

### Post by mde123 on 2008-06-05
install qgrubeditor
and launch it from the system tools










i hope one day you will go full Ubuntu

---

### Post by drs305 on 2008-06-05
I have edited this post to correct an error. The information below is correct and, since this thread has been marked "solved", notified those who read the post before I corrected it.
....

Well, the number would be 8. The boot option number is derived by counting the number of uncommented titles, including memtest86+ and the "Other operating systems" title and subtracting 1. That is because the count starts at 0.

So you have:
```

title		Ubuntu 8.04, kernel 2.6.24-18-generic
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
title		Ubuntu 8.04, kernel 2.6.24-17-generic
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
title		Ubuntu 8.04, kernel 2.6.24-16-generic
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
title		Ubuntu 8.04, memtest86+
title		Other operating systems:
title		Microsoft Windows XP Professional

```

> No matter what number I put after "grub-reboot" it doesn't seem to work for me. The 1st entry is always selected in the grub menu.
Which system is the default is set by the "default 0" line. It uses the same methodology I described above. 0 is the first kernel/OS listed in the uncommented section near the bottom of the file. If you wanted to have the second kernel, 17-generic, to boot, the number would be 2. You can also set this and many other options in StartUp-Manager. (see link below). 

Your app uses the same logic to determine which kernel/OS to use. I haven't used the app you are trying, but I would expect if you try the number 8 it will work.

By the way, I just wrote a HOWTO on grub yesterday.
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Terrigal on 2008-06-05
Yes I have the same wish. Will be interested if you can solve this.

---

### Post by MiniMe on 2008-06-06
Thanks for the replies but it still doesn't work for me.

I tried all of the following:

sudo grub-reboot 1
sudo grub-reboot 2
sudo grub-reboot 3
sudo grub-reboot 4

None of them changed the grub menu selection to anything but the default first entry during boot.

I also tried qgrubeditor as suggested but it seems to be just a gui to edit the menu.lst file.

I wonder if there's anything I'm doing wrong? Any suggestions or another way to get the same job done?

Thanks again.

---

### Post by MiniMe on 2008-06-06
I've found the solution. In the menu.lst file I had to set to set "default" to "saved"

default         saved
instead of:
default         0

[http://wiki.debian.org/GrubReboot](http://wiki.debian.org/GrubReboot)

Also, if you find that the default selection in grub is then changed to what you rebooted to with grub-reboot, setting savedefault=false supposedly does the trick.
[http://ubuntuforums.org/showthread.php?t=722900&highlight=grub-reboot](http://ubuntuforums.org/showthread.php?t=722900&highlight=grub-reboot)

Thanks again.

---

### Post by stchman on 2008-06-06
Install StartUpManager.  It has GRUB editing capabilities.  Gutsy and later.

```
sudo apt-get install startupmanager
```

---

