---
title: "Grub - boot sequence options?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by chrisp9au on 2008-04-27
Hi, I'm new to Linux & Ubuntu. Install went perfectly and I like what I see. However...
I will need to continue using windows due to work commitments and the need for MS Excel with macros/visual basic.
I would like to have Windows as the default boot option in the Grub boot manager, booting Ubuntu when I specifically want to use it.
How do I change the boot sequence?, which file do I need to edit?, where is that file?, what program do I use to do the edit, do I have the necessary authority to edit the file?
Thanks
Chris

---

### Post by Joeb454 on 2008-04-27
Does Windows show up in your Grub menu? It will be at the bottom I assume :) And are you using the standard Ubuntu install?

---

### Post by chrisp9au on 2008-04-27
Yes, Windows XP Home shows up at the bottom. I downloaded the 8.0.4 version, I have to assume it is the standard version, I'm not aware of any other versions?
Thanks
Chris

---

### Post by Joeb454 on 2008-04-27
Ok yes that's what I thought :) I won't go into the "other versions" now :)

Can you open a terminal from Applications>Accessories>Terminal and then copy and paste the following (or type it) ```
cat /boot/grub/menu.lst > ~/Desktop/menu.txt
```

That will copy your menu file to your desktop. Can you then copy the contents of that file into another post (or attach it to another post) thanks :)

---

### Post by southernman on 2008-04-27
[All things GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

File location: /boot/grub/menu.lst (also file you'd edit)

How to edit the file: go to applications, accessories, terminal and in the terminal type ```
gksudo gedit /boot/grub/menu.lst
```Gedit will be the program you'll use.

Check the grub page above for anything grub related you need to know.

---

### Post by chrisp9au on 2008-04-27
Hi Joeb454,

Menu.txt as requested...

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
# kopt=root=UUID=1d393da1-9b7a-47c1-935e-c98ae7384da1 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1d393da1-9b7a-47c1-935e-c98ae7384da1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1d393da1-9b7a-47c1-935e-c98ae7384da1 ro single
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Joeb454 on 2008-04-27
Ok, now from a terminal, type or copy ```
gksudo gedit /boot/grub/menu.lst
```
And replace it with the following :) it should work ok - I changed the default line

```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default 4**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1d393da1-9b7a-47c1-935e-c98ae7384da1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1d393da1-9b7a-47c1-935e-c98ae7384da1 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1d393da1-9b7a-47c1-935e-c98ae7384da1 ro single
initrd /boot/initrd.img-2.6.24-16-generic

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
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```
Yes that really was all I edited :) it used to be **default 0**

---

### Post by hyper_ch on 2008-04-27
> **chrisp9au said:**
> Hi, I'm new to Linux & Ubuntu. Install went perfectly and I like what I see. However...
I will need to continue using windows due to work commitments and the need for MS Excel with macros/visual basic.

You could run vmware or vbox and start a virtual windows within your ubuntu... depending on your hardware specs it should run quite good :)

---

### Post by gn2 on 2008-04-27
Lots of info on Grub including editing the default OS [**[COLOR="DarkOrange"]here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by chrisp9au on 2008-04-27
Thanks Joeb454, worked perfectly!
I must confess, previous encounters with Linux didn't impress me, but this time I like. Installed perfectly, migrated all my documents and settings, including my desktop picture, I have access to my wife's PC running windows. It all looks good!
Hyper_ch
'You could run vmware or vbox and start a virtual windows within your ubuntu... depending on your hardware specs it should run quite good'
PC is a Dell Optiplex GX270 2.8GHZ, 2GB ram, 80GB HDD.
I don't know anything yet about vmware/vbox, I guess I would install MS Office into this? I have some pretty heavy Excel VBA applications that I run for work.
Thanks everyone for the quick responses, makes me feel very welcome!
Regards
Chris

---

### Post by Joeb454 on 2008-04-27
No worries, glad it worked. I'll go back and edit my post so you can see the line I edited :)

I'll make it bold :)

Glad you're enjoying Linux this time round

---

### Post by southernman on 2008-04-27
> **chrisp9au said:**
> Thanks Joeb454, worked perfectly!
I must confess, previous encounters with Linux didn't impress me, but this time I like. Installed perfectly, migrated all my documents and settings, including my desktop picture, I have access to my wife's PC running windows. It all looks good!
Hyper_ch
'You could run vmware or vbox and start a virtual windows within your ubuntu... depending on your hardware specs it should run quite good'
PC is a Dell Optiplex GX270 2.8GHZ, 2GB ram, 80GB HDD.
I don't know anything yet about vmware/vbox, I guess I would install MS Office into this? I have some pretty heavy Excel VBA applications that I run for work.
Thanks everyone for the quick responses, makes me feel very welcome!
Regards
ChrisGood on you Chris, Joe nailed it for sure.

BTW, Welcome to Ubuntu.

With those specs on your Dell box, should have no trouble running either Hyper_ch suggests.

---

### Post by chrisp9au on 2008-04-27
I'll do some research on vmware etc. through the week, but right now it's time for some shuteye, nearly midnight and an early start in the morning.
Thanks again!
Chris

---

### Post by hyper_ch on 2008-04-27
you could easily run a windows in vmware/vbox... only thing to worry about would be harddisk space (80GB is quite low I think).

Basically with vmware/vbox you can setup a virtual windows that starts within your ubuntu... with your processor and ram it should run quite well...

so you install windows within ubuntu and in that windows you can then install MSOffice or whatever... the only things that don't run is stuff that requires DirectX (games)

---

### Post by southernman on 2008-04-27
> **chrisp9au said:**
> I'll do some research on vmware etc. through the week, but right now it's time for some shuteye, nearly midnight and an early start in the morning.
Thanks again!
Chris
Oh yeee of little Linux experience.....

Linux geeks don't need no stinkin' sleep! Let's get crackin'!

<----- needs sleep!

---

