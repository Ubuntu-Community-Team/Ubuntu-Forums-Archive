---
title: "[SOLVED] New dualboot install; GRUB Error 17"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by DippaH on 2008-08-17
Hey guys.

After trying Ubuntu on my laptop for a little while, I decided to go for a dualboot solution on the desktop. 

I've choosen to install Ubuntu 8.04 on a *seperate* hard drive, so it wouldn't interfere with my rather important Vista installation. But now the problem...

After a 100% problem-free installation, I can't get the darn thing to boot up Ubuntu. 
When i choose to boot up via the designated Ubuntu hard drive(using the BIOS boot-up manager), I get to the GRUB-screen fine, but will get "Error 17" when i choose to run Ubuntu. I have no problems starting up Vista this way. 
I just installed Ubuntu, using the "Entire Disk" installation option.

I don't have much experience with GRUB but i fail to see what i could've done wrong, during the installation. 


Hope you guys can help...

---

### Post by Elfy on 2008-08-17
Can you boot with the livecd, open a terminal and run

```
sudo fdisk -l
```

If you are able to do so, find the linux drive in places > computer - open it and paste the text in /boot/grub/menu.lst as well.

---

### Post by DippaH on 2008-08-17
Okay, I booted up with the Live-CD, and this is what i got:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25fa798c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf5fdf5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa599a599

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

And:

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
# kopt=root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by Crafty Kisses on 2008-08-17
You can technically recover your GRUB loader with "SuperGRUB" this link may help you > [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by DippaH on 2008-08-17
> **Codename said:**
> You can technically recover your GRUB loader with "SuperGRUB" this link may help you > [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Just tried that program...

Unfortunately It didn't do the trick. I tried to fix GRUB along with booting my Ubuntu through SuperGRUB - nothing helped. 

The program able to find both system disk, along with the OS's, but still won't boot Ubuntu from it :confused:

---

### Post by bumanie on 2008-08-17
Looks as though grub has got confused between the two window installations on the first and third hard drives. Assuming the first disk is the original windows installation and the the third disk is a data storage area, this should fix it; Boot with ubuntu live cd; in terminal > sudo grub > root (hd1,0) > setup (hd0) > quit reboot and see if it works, otherwise try super grub disc as already indicated.

---

### Post by DippaH on 2008-08-17
> **bumanie said:**
> Looks as though grub has got confused between the two window installations on the first and third hard drives. Assuming the first disk is the original windows installation and the the third disk is a data storage area, this should fix it; Boot with ubuntu live cd; in terminal     reboot and see if it works, otherwise try super grub disc as already indicated.

Just gave your code a shot. Still can't boot into Ubuntu - Error 17 is still haunting me... 

Now I can't boot into Windows though - so it must have changed something or other.

---

### Post by Elfy on 2008-08-17
When you booted windows before - did you do so from the bios boot or form grub - because grub appears to point vista at the linux partition.

It would look like ubuntu should be on hd1 and win on hd0 - but what it is that is on hd2?

When you used the supergrub - did it say it had succeeded and then wouldn't boot - or did it fail?

---

### Post by DippaH on 2008-08-17
> **forestpixie said:**
> When you booted windows before - did you do so from the bios boot or form grub - because grub appears to point vista at the linux partition.

It would look like ubuntu should be on hd1 and win on hd0 - but what it is that is on hd2?

When you used the supergrub - did it say it had succeeded and then wouldn't boot - or did it fail?

When i booted up Windows before, i did so through the BIOS i believe. You know, like a normal Windows startup, where it just loads. After i installed Ubuntu i had to select the "Ubuntu-drive" in the BIOS to get to the GRUB ( - which is also how i would like it to work in the future).

I'm a bit confused about that "hd0/hd1/hd2" stuff, but I'll try to explain;

Disk /dev/sda: My Windows disk, where Vista is installed
Disk /dev/sdb: Apparently the Ubuntu disk
Disk /dev/sdc: A simple storage drive, with lots of various media stored - No OS installed.


With Supergrub I got "succeeded" everytime.

---

### Post by Elfy on 2008-08-17
Ok - grub starts counting from 0 for hdd and partition so hd0,0 is first partition on first hdd - just so you know :)

If the last drive is just a data storage I wonder why it has a boot flag then... not sure about that.

What does the mneu .lst look like now - can you post it again, now that supergrub has worked on it please.

---

### Post by DippaH on 2008-08-17
The menu.lst now looks like this:

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
# kopt=root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



```

Currently when i boot up, I get to the GRUB screen. I which i didn't do before. Still getting the "Error 17" though.

---

### Post by Elfy on 2008-08-17
That's fdisk - l :)

>  find the linux drive in places > computer - open it and paste the text in /boot/grub/menu.lst as well.

---

### Post by DippaH on 2008-08-17
> **forestpixie said:**
> That's fdisk - l :)

Haha, i know - must've edited it while you were reading it... 

Wasn't quick enough - should be fixed now though:)

---

### Post by Elfy on 2008-08-17
So it hasn't changed - try editing it - open nautilus as root from a terminal - ```
gksudo nautilus
```

Navigate to the same file, right click open with text editor, for second line of the ubuntu entry change 

> root		(hd2,0) to
> root		(hd1,0)

do same for recovery mode and memtest

for vista change

> title		Windows Vista/Longhorn (loader)
root		([COLOR="Red"]hd0[/COLOR],0)
savedefault
makeactive
[COLOR="#ff0000"]#[/COLOR]map		(hd0) (hd1)
[COLOR="#ff0000"]#[/COLOR]map		(hd1) (hd0)
chainloader	+1

and try again

---

### Post by Elfy on 2008-08-17
If it doesn't let you edit the file and save it, do this in a terminal

```
sudo mkdir /media/lin
sudo mount -t ext3 /dev/sdb1 /media/lin
```

Then to edit and save

```
sudo cp /media/lin/grub/boot/menu.lst /media/lin/grub/boot/menu.lst.1708
gksudo gedit /media/lin/grub/boot/menu.lst
```

If youy get any errors please post the whole thing - command as well.

---

### Post by DippaH on 2008-08-17
Thanks a bunch - was able to edit menu.lst through Nautilus no problems.

I can load up Ubuntu now, no problems - which is great! 


- Was just wondering. Is there a way, through GRUB that i can make Vista the "default" OS when booting up? 

For me the ideal way would be if GRUB was "hidden" and only came up when i selected the Ubuntu-disk through the BIOS... But don't know if that's possible at all? If not - then never mind :)

---

### Post by Elfy on 2008-08-17
Not sure about that but you can change vista to be the default - either change the default number - as shown - this would need to be changed each time there was a kernel update though, 

or move the vista boot segment up the list and it will stay there - before the ### BEGIN AUTOMAGIC KERNELS LIST line - I have shown both changes here in red, _obviously don't do both_ :) - note that the end of the list has also been removed. If you move the vist up the list and change the deafult you will get memtest as default.

Please alos note a further change in the list for the groot value - change that regardless of which change you make to the vist problem.

Once in ubuntu run

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.17082
gksudo gedit /boot/grub/menu.lst
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
[COLOR="Red"]**default		4**[/COLOR]

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

[B][COLOR="#ff0000"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/COLOR][/B]

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
# kopt=root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=([COLOR="Red"]**hd1**[/COLOR],0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfe0bb31-4132-4697-bfca-a2b1f8277d19 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by DippaH on 2008-08-17
Will try to sort it out later - running out of time here... :)


Thanks to you **forestpixie** and everybody else who took the time to help me out! - Couldn't ask for more... 

//DippaH

---

### Post by Elfy on 2008-08-17
Welcome - when you have done can you mark thread solved please.

---

