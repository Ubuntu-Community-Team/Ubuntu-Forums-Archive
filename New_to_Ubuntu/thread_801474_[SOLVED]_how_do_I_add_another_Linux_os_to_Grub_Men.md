---
title: "[SOLVED] how do I add another Linux os to Grub Menu"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-05-20
I have Ubuntu Hardy installed and I just installed Arch Linux OS on a partition now I am not exactly sure how to add Arch Linux to the Grub Menu I read this [http://wiki.archlinux.org/index.php/GRUB]("http://wiki.archlinux.org/index.php/GRUB") but it isn't really that clear to me so I thought that I would post here to see if there is a clearer way to do this

---

### Post by shifty_powers on 2008-05-20
```
gksudo gedit /boot/grub/menu.list
```

---

### Post by nick_h on 2008-05-20
Edit the menu.lst file as shifty_powers suggested and then paste a section at the bottom similar to:
```
# (0) Arch Linux
title  Arch Linux  [cpio]
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda6 ro vga=773
initrd /kernel26.img
```

You will have to edit the last 3 lines as appropriate.

For reference read the [Grub Manual](http://www.gnu.org/software/grub/manual/grub.html).

---

### Post by zvacet on 2008-05-20
```
sudo fdisk -l
```

With this command you wil see on which partition is Arch.(Let just for example say it is hda2 and you will enter right partition.)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

you will see this line 

### END DEBIAN AUTOMAGIC KERNELS LIST

and below that line type

title            Arch
rootnoverify     (hd0,1)
chainloader +1

sava file and close it.After reboot you should see Arch as option to boot in.

---

### Post by Shadowmeph on 2008-05-20
> **shifty_powers said:**
> ```
gksudo gedit /boot/grub/menu.list
```
when I do that command it just comes up blank.but if I do this command nano /boot/grub/menu.lst
it shows me the grub ubuntu but I need to know what do I put onto the list like how/were do I add it on the list?

---

### Post by Shadowmeph on 2008-05-20
ok that seems simple enough now for one last question how do I find out which "kernel /vmlinuz26" Arch has ?

---

### Post by Shadowmeph on 2008-05-20
ok I just took a guess on the kernal thing when I rebooted and went into grub it showed Arch in the menu but when I tryed to load it I got  "error 15 file not found"

---

### Post by Shadowmeph on 2008-05-20
> **zvacet said:**
> ```
sudo fdisk -l
```

With this command you wil see on which partition is Arch.(Let just for example say it is hda2 and you will enter right partition.)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

you will see this line 

### END DEBIAN AUTOMAGIC KERNELS LIST

and below that line type

title            Arch
rootnoverify     (hd0,1)
chainloader +1

sava file and close it.After reboot you should see Arch as option to boot in.
ok so the Arch os is in partition /dev/sda2    132    1437   10490445   83  Linux so I just add this title            Arch
rootnoverify     (sda2) chainloader +1?

---

### Post by nick_h on 2008-05-20
> how do I find out which "kernel /vmlinuz26" Arch has ?
Have a look in the /boot directory in your Arch partition.

Did you install grub in the Arch partition when you installed it?

---

### Post by Shadowmeph on 2008-05-21
> **nick_h said:**
> Have a look in the /boot directory in your Arch partition.

Did you install grub in the Arch partition when you installed it?

did I need to do that? I don't know how to I thought that it would install automatically

---

### Post by zvacet on 2008-05-21
> ok so the Arch os is in partition /dev/sda2 

If that is the case  

title Arch
rootnoverify (hd0,1)
chainloader +1

Save file and close it.After reboot you should see Arch in grub as option to boot in.

---

### Post by Shadowmeph on 2008-05-21
Grub shows Arch in the menu but when I click on Arch it goes to to another screen ( like it is going to try an load Arch ) then I get a message saying "error 13 invalid or unsupported executable format"
this is what I have in the grub menu
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=18573b0e-4906-4c7f-8e32-b544fd854ab5 ro

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

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=18573b0e-4906-4c7f-8e32-b544fd854ab5 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=18573b0e-4906-4c7f-8e32-b544fd854ab5 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

[B]# (0) Arch Linux
title  Arch Linux  [cpio]
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda2 ro vga=773
initrd /kernel26.img

### END DEBIAN AUTOMAGIC KERNELS LIST

title Arch
rootnoverify (hd0,1)
chainloader +1[/B]



---

### Post by nick_h on 2008-05-21
> did I need to do that? I don't know how to I thought that it would install automatically
The reason that I asked if you installed grub when you installed Arch was that if you did then you could copy the appropriate block from the Arch menu.lst into your active menu.lst

If you can find the locations of your kernel and initrd then you could write a block similar to that described in the link you posted.

Alternatively, you could use the approach that zvacet suggested.  This will chainload a boot loader in your Arch partition.

---

### Post by nick_h on 2008-05-21
Just saw your last post.

You should put your new entries after the line:
*### END DEBIAN AUTOMAGIC KERNELS LIST*

If the chainloader approach fails then try the other.  You will have to mount your sda2 filesystem and look for the kernel and initrd files.  They are likely to be in either / or /boot.  I don't use Arch myself so I can't be more helpful.  You will also need to change the line *root (hd0,0)* to *root (hd0,1)*.

---

### Post by Shadowmeph on 2008-05-21
ok in the boot/grub folder ( on the Arch mounted Linux) this is what it shows on the Menu
```
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux  [/boot/vmlinuz26]
root   (hd0,0)
kernel /vmlinuz26 root=/dev/hda3 ro
initrd /kernel26.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
```

not to sure why it is showing windows because I don't have windows installed .
so if Iput this title Arch
rootnoverify (hd0,0)
chainloader +1 below ### END DEBIAN AUTOMAGIC KERNELS LIST it should work? but I have to change** root   (hd0,0) to this root   (hd0,1) **
on both the Ubuntu and Arch grub menus?

---

### Post by Shadowmeph on 2008-05-21
Thank you all for your help I posted at the Arch forums also and recieved a reply sayng "It seems to me your grub entry should look like this:
Code:

title  Arch Linux
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/sda2 ro
initrd /boot/kernel26.img

"
which seemed to have worked so it took the effort of Ubuntu forums and the Arch forums for me to understand how to do this thank you again

---

### Post by nick_h on 2008-05-21
I'm glad you got it working.  The boot files are in /boot as they are in Ubuntu.

---

