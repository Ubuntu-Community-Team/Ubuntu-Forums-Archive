---
title: "Booting problem..."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by yogen on 2008-09-02
whenever i start ubuntu...instead of the usual graphical loading ubuntu logo...i can see a list of files executed...i need my graphical logo back..what should i do...???

have tried gnome splash screen manager...but whenevr i select any downloaded splash screen in splash screen manager...and try to open it...the splash screen manager gets terminatd...!!!

---

### Post by porchrat on 2008-09-02
Can you please copy and paste the ouput of this into this forum:

```
sudo cat /boot/grub/menu.lst
```

See if you can find this in that output:

"ro quiet splash"

---

### Post by yogen on 2008-09-02
yes sure...

yogen@yogen-desktop:~$ sudo cat /boot/grub/menu.lst
[sudo] password for yogen: 
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=/grub/splashimages/NFS:_Most_Wanted_003.xpm.gz

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
# kopt=root=UUID=CA64129C64128B79 loop=/ubuntu/disks/root.disk ro

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
# defoptions=quiet vga=792

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=CA64129C64128B79 loop=/ubuntu/disks/root.disk ro quiet vga=792
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=CA64129C64128B79 loop=/ubuntu/disks/root.disk ro single
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
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

yogen@yogen-desktop:~$

---

### Post by dracayr on 2008-09-02
behind this line:

```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=CA64129C64128B79 loop=/ubuntu/disks/root.disk ro quiet
```, insert the word splash

EDIT: please use the [CODE] tags, to stop the line from breaking. In your post, I noticed the line vga=792 under the line mentioned above. I don't know if these are 2 different lines in your file, as you didn't use the code tags. they should be 1 line

dracayr

---

### Post by yogen on 2008-09-02
its says command not found...!!!

---

### Post by porchrat on 2008-09-03
Please be specific.

What says command not found?

---

### Post by yogen on 2008-09-04
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=CA64129C64128B79 loop=/ubuntu/disks/root.disk ro quiet

this command when executed...it says command not found...

---

### Post by porchrat on 2008-09-04
please post this ouput:

```
sudo ls -l /boot
```

---

### Post by Zalbor on 2008-09-04
It's not a command to execute, you edit your /boot/grub/menu.lst file and add "splash" on that line.

But if you do it this way, the graphical screen will go away next time the kernel is updated. Do the following instead:
-Edit the grub file with:
```
gksu gedit /boot/grub/menu.lst
```
-Find this line:
```
# defoptions=quiet vga=792
```
-Change it like this:
```
# defoptions=quiet splash vga=792
```
-Save the file and close the program
-Run this command:
```
sudo update-grub
```

This way the splash screen will be added, and it will remain if you upgrade the kernel.

---

### Post by yogen on 2008-09-05
output for sudo ls -l /boot...

yogen@yogen-desktop:~$ sudo ls -l /boot
total 19396
-rwxrwxrwx 1 root root  422667 2008-06-18 23:41 abi-2.6.24-19-generic
-rwxrwxrwx 1 root root   80049 2008-06-18 23:41 config-2.6.24-19-generic
drwxrwxrwx 1 root root    4096 2008-09-05 17:15 grub
-rwxrwxrwx 1 root root 8836431 2008-09-02 21:55 initrd.img-2.6.24-19-generic
-rwxrwxrwx 1 root root 7576595 2008-09-02 18:56 initrd.img-2.6.24-19-generic.bak
-rwxrwxrwx 1 root root  103204 2007-09-28 15:36 memtest86+.bin
-rwxrwxrwx 1 root root  905146 2008-06-18 23:41 System.map-2.6.24-19-generic
-rwxrwxrwx 1 root root 1920472 2008-06-18 23:41 vmlinuz-2.6.24-19-generic
yogen@yogen-desktop:~$

---

