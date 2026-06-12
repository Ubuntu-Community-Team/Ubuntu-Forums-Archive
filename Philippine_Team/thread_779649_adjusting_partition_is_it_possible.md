---
title: "adjusting partition is it possible?"
date: 2008-05-02
forum: Philippine Team
---

### Post by killer_d76 on 2008-05-02
i have formatted my 80GB HDD on my laptop and installed XP with Hardy dual boot on it.. everything is fine and working properly now :KS .. except that i did not noticed that when i re-installed Hardy, it took 70Gig out of 80Gig and whatever remained was for Window$ use, i thought it was ok, but when i re-installed some of the drivers for Window$, the remaining free space for it to use is 615MB and i still haven't installed all the drivers yet, rather than going thru the whole process again :(, is it possible for me adjust Window$ partition using Ubuntu so i could have a bigger space for windows to use?

- thanks in advance!

---

### Post by killer_d76 on 2008-05-02
or perhaps, is there a windows software to adjust partition so i can enlarge the partition for window$.

---

### Post by pendletone on 2008-05-02
Hi killer_d76. You can use Gparted from the Ubuntu LiveCD to shrink your ubuntu partition and give some to Windows.

Or, if you prefer a Window$ program to handle that, you can try Partition Magic (proprietary). Just make sure to backup your data before doing so.

Hope that helps. :)

---

### Post by killer_d76 on 2008-05-02
thanks pendletone, hhmm.. i can try using the live CD, i'm not familiar with partition magic thoug.. so here's what i'm going to do, i'll just open ubuntu using that live CD, open Gparted and adjust the partition there?.

---

### Post by yssida on 2008-05-03
I think that would be good. Just be careful and know which partition your Windows is and where Ubuntu's is. I once wiped my Vista partition AND the 'hidden' recovery partition. Hay, sayang yung nabayaran na OEM licensing...

---

### Post by eilu on 2008-05-03
or you can use the gparted live CD. I've done this before with no problems.

---

### Post by killer_d76 on 2008-05-03
i did it!.. i was able to make window$ a bit bigger (15gig).. now what i did was created a new partition and put a copy of windows there and deleted the original one (3GiG one)and it becomes sdev8?, but now i when i tried to access windows on the boot grub.. i got an error 22 and says "partition does not exist".. i think i need some grub editting and this should work cause if i run ubuntu i can see the partition i have created!.. can you help me here.. thanks.

here's my menu lst.. 

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
# kopt=root=UUID=4a2bdc92-d9fc-4713-b15e-ffd96779fbc7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4a2bdc92-d9fc-4713-b15e-ffd96779fbc7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4a2bdc92-d9fc-4713-b15e-ffd96779fbc7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1

---

### Post by killer_d76 on 2008-05-03
# This entry automatically added by the Debian installer for a non-linux OS
**# on /dev/sda1**
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


.. my new window$ partitions is **/dev/sda8**, if i replace the **/dev/sda1 **part (see above)with **/dev/sda8** will i be able to boot to window$ now?, and do i still need to remove # symbol? .. thanks!.

---

### Post by glenn45 on 2008-05-03
> **killer_d76 said:**
> # This entry automatically added by the Debian installer for a non-linux OS
**# on /dev/sda1**
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


.. my new window$ partitions is **/dev/sda8**, if i replace the **/dev/sda1 **part (see above)with **/dev/sda8** will i be able to boot to window$ now?, and do i still need to remove # symbol? .. thanks!.



yung kelangan mo palitan na linya ay yung sa root (hd0,0), gawin mong 
root (hd0,7)
di mo na kelangan tanggalin ang # na symbol.

---

### Post by killer_d76 on 2008-05-03
thanks for the reply glenn45, but is it possible for you to explain it to me further on how to do it?.. or if possible a step by step on how to change that!.. please! thanks.

---

### Post by killer_d76 on 2008-05-04
ah ok!.. gets ko na sige try ko mamaya.. thanks

---

### Post by glenn45 on 2008-05-04
> **killer_d76 said:**
> thanks for the reply glenn45, but is it possible for you to explain it to me further on how to do it?.. or if possible a step by step on how to change that!.. please! thanks.

ehehe. hmm. 
pasok ka duon sa linux mo. 
tapos mag open ka ng command line terminal.
tapos eh edit mo yung grub file mo.

ako usually gamit ko vim. marunong ka mag vim o vi?

dapat  back up mo muna yung menu.lst file mo bago mo baguhin.

basta yung grub file mo nasa /boot/grub/menu.lst

yung command para eh modify yung menu.lst na file ay

sudo vi /boot/grub/menu.lst

yun. eh edit mo duon. 

kung hindi ka marunong mag vi, try mo yung

gksudo gedit /boot/grub/menu.lst

---

### Post by killer_d76 on 2008-05-04
oks na!.. thanks glenn45.. hehehe kala ko kasi dun sa root titirahin eh.. ):P thanks!

---

