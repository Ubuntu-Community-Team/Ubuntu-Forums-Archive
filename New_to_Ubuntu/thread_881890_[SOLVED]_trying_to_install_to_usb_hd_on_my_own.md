---
title: "[SOLVED] trying to install to usb hd on my own?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-06
im following a recent thread of mine to install kubuntu to a usb hd.
i have u.studio on my first hd,now heres what i did;
i installed kubuntu to /dev/sdb1,then reset the grub for the first hd
using;sudo grub,root (hd0,0),setup (hd0),quit,i then got an error15.
so i got into the /boot/grub/menu.lst,and did some editing,it was coming up 2.6.24-20-generic when its 2.6.24-19-generic.
it boots up fine but when i select ubuntu from the boot menu 
it hangs on the start screen,the blue bar just keeps going back and forth.
is there a step missing?i must admit i got alittle lost on the discussion of the error 15,so i could use alittle help,i guess i still cant do it on my own.thanx in advance.
rick:confused:

---

### Post by mick8985 on 2008-08-06
Can you paste the contents of your menu.lst, just the relevant stuff at the bottom

---

### Post by rixtr66 on 2008-08-06
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title           Kubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Kubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd          /boot/initrd.img-2.6.24-20-generic

title           Kubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Kubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd          /boot/initrd.img-2.6.24-16-generic


title           Kubuntu 8.04.1, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
this may not be correct!
rick

---

### Post by rixtr66 on 2008-08-06
im going to reinstall kubuntu w/kde3.5 i dont like kde 4 its too buggy.
after i install ill post the new menu lst,i hope this works!
rick

---

### Post by mick8985 on 2008-08-06
Well I would imagine a major issue is that I think by the way that you described what you did the kernel you want to load is on sdb1/boot/ and the grub.conf you are using is the one on sda1.
The best way to do this really is to have a seperate boot partition which both distros can use, but failing that another good way is to simply use the chainloader.
```
title kubuntu
   chainloader(hd1,0)+1

```
This will then run the bootloader on your usb drive, this also makes it very convenient as it makes your usb install portable to other computers you would simply change the boot device priority in the bios to decide which bootloader runs.

---

### Post by rixtr66 on 2008-08-06
so how do i make this chainloader work?

---

### Post by mick8985 on 2008-08-06
You set up both drives to boot as if they were the primary drive ie do 
grub > root (hd0,0) > setup (hd0) for sda and also do it for sdb
grub > root (hd1,0) > setup (hd1) > quit. Then pick which drive you boot first in your bios, should be the first one sda anyway right?
So now you want to add another entry to the menu.lst on sda
```
sudo nano /boot/grub/menu.lst
```
and add
```
title Kubuntu
root (hd1,0)
chainloader +1
```
that should do it

---

### Post by mick8985 on 2008-08-06
I thought I'd mention the reason why this way is the best way to do this that everytime you download a new kernel for each OS you'd have to manually fiddle about with things to get it to work again, this way everything is handled normally like a regular ubuntu install, another good way is to have a shared boot partition between the 2 OS's

---

### Post by rixtr66 on 2008-08-06
a thanx ill give it atry!
rick

---

### Post by rixtr66 on 2008-08-06
didnt do any good it still hangs at the splash sreen, and that little
blue bar just keeps going back and forth.
rick

---

### Post by tariquepark on 2008-08-06
> **mick8985 said:**
> You set up both drives to boot as if they were the primary drive ie do 
grub > root (hd0,0) > setup (hd0) for sda and also do it for sdb
grub > root (hd1,0) > setup (hd1) > quit. Then pick which drive you boot first in your bios, should be the first one sda anyway right?
So now you want to add another entry to the menu.lst on sda
```
sudo nano /boot/grub/menu.lst
```
and add
```
title Kubuntu
root (hd1,0)
chainloader +1
```
that should do it

hi there
this is by far the best way of setting it up although i would add that if ur bios is booting from the usb drive the internal drive wil not be listed in grub
if you want to you can do the same to the menu.list on ur usb drive install which will make grub point to the next boot loader on the internal drive
this means you have true portability regardless
i hope that makes sense:)
regards

---

### Post by rixtr66 on 2008-08-07
ok i followed the instructions,butit still hangs,ill try it again.

---

### Post by rixtr66 on 2008-08-07
Then pick which drive you boot first in your bios, should be the first one sda anyway right?

how do i do this?

---

### Post by tariquepark on 2008-08-07
in the bios look for the boot sequence and select usb device first and hard drive 2nd
also is your internal drive a sata or ide?
if its ide (wide ribbon with 48 pins) linux will call it hda instead o sda
sda means serial ata which uses a small black plug
hope this helps
 btw have you got a live disk? if so change the bios to boot from the cdrom and select start terminal and type
sudo fdisk -l
this will list all hard drives and their linux device names sizes etc 
this should help the confusion between which drive is which :)

---

### Post by mick8985 on 2008-08-07
If your BIOS doesn't support boot from USB this won't work, if this is the case the kernel will have to be loaded from your internal drive before you can mount /  on you usb drive if this is the case I will give detailed instructions on how to do this.

---

### Post by rixtr66 on 2008-08-07
ihad all this working a few days ago!for some reason the chainloader makes kubuntu onthe usb drive hang at the start screen,no errors.
now,ifma i nstall kubuntu on the usb drive,and save grub to (hd0)
kubuntu boots up fine,i can also boot into ubuntu studio.
however when i unplug the drive i get error21.
so,after installing kubuntu,i go back and get into grub,
and edit root (hd0,0) setup (hd0) quit,things should be normal.
wrong kubuntu hangs at the start screen.ive checked the grub menu
and it looks ok,so im stumped.inthe bios the order is dvd,hd1,usbhd.
as i said i went through this earlier and it worked,but i cant seem to duplicate it.some major help is needed here,and i would appreciate it 
greatly.
rick:confused:  oh yeah the drive is ide,and usb is supported.

---

### Post by rixtr66 on 2008-08-07
help please!
rick

---

### Post by tariquepark on 2008-08-08
ok if you have an ide drive then all references to sda or sda1 are on the usb drive
ide drives will be hda1
maybe this is the problem?
also your bios should be set to boot usb before hard disk
that is cdrom first usb 2nd and hard disk 3rd

---

### Post by rixtr66 on 2008-08-08
ok ive set up my bios like you said,and istill get ubuntu hanging
at the start  screen,so i went back to how i had it set up before 
i changed the grub to (hd0)for the usb drive,and everything shows up
correctly in the boot screen and everything works,except if i unplug
the usb drive i get error21 very strange.when i use the chainloader method
kubuntu only shows 2.6.24-20-generic,and hangs.but when i changed the grub to (hd0)the boot menu correctly shows 2.6.24-20-generic and 2.6.24-19 generic,
im really not understanding this??????
help please!!!!
rick:confused:

---

### Post by tariquepark on 2008-08-08
hmmmm
i think its because grub is trying to start from the wrong partition
if you go back and run the grub setup on both drives but this time remove the chainloader from the .list file
this should basically change everything back to a separate grub for each install
then remove the usb drive and boot up
this should work ok
if it does try again with the usb drive plugged in and hopefully it should too
then we can simply add each entry back in the .list file one at a time
dont forget to check that your bios is set to boot from the usb on the second run
:)

---

### Post by david tutton on 2008-08-08
> **rixtr66 said:**
> didnt do any good it still hangs at the splash sreen, and that little
blue bar just keeps going back and forth.
rick

I had a similar problem, I used a usb2 device on a usb1 port, and it took ages to boot up but it did eventually????:)

---

### Post by rixtr66 on 2008-08-08
ok i did a total overhaul,i installed kubuntu to(hd0),then i installed
ubuntu 8.04 to (hd1)i installed the grub for the usb hd to (hd0)
at first it didnt show up,so i added usb support by editing;
/etc/mkinitramfs/modules,restart and viola!ubuntu appears on the boot
menu,but on a restart its not there?how should i go about setting this upto boot both hds without the usb hd plugged in?
rick

---

### Post by rixtr66 on 2008-08-08
is anybody there...............anyone at all................is this thing on?
just kidding!ineed some help with this while the grub menu is still fresh.
rick

---

### Post by prabhakaran1989 on 2008-08-08
I had got one GUI software to do all these..just search in synaptic package manager pysdm d inatall..then in preferences u will find storage device maneger there u can do that mounting of drives safely!!


for that hda,1 problem u have to edit menu.lst ,by changine 0 s ad 1 s so thatit may work...

first thing is all should be connected to the primary master/slave!

---

### Post by tariquepark on 2008-08-08
you need to set the default device to hd0 so its grubs first choice when booting. make sure the display time is 20-30 seconds to give you time to select the usb drive from the grub menu
also i found the the display time in my grub loader was only 1 second and it just flashed by :)

---

### Post by rixtr66 on 2008-08-08
very strange goings on,if itry to boot to my first hd i get an error11 unrecognized device string.but i can boot to the usb hd just fine.if i unplug the usb hd my first hd boots fine?
why cant i get it set up like before.?
ill keep  searching,and i hope i get some more help.
rick:confused:

---

### Post by tariquepark on 2008-08-08
is that the 1st hd in the bios? hd0? or hd1?
i mean what have you set the bios to boot from?

---

### Post by tariquepark on 2008-08-08
is that the 1st hd in the bios? hd0? or hd1?
i mean what have you set the bios to boot from?

---

### Post by falcon61102 on 2008-08-08
When you have the two different booting drives as you have, you have to configure both GRUBs.  When you boot from the USB drive you are using one GRUB and when you boot from the HD you are using another GRUB.  Since you have two different GRUBS, the paths for the kernals are going to be different depending on which GRUB is trying to load them.  

For instance, when you start the Ubuntu install on you HD, your HD is the first drive, but when you start the GRUB on the USB drive, your HD had now become the second drive so if the GRUB is still pointing to the first drive you are going to get errors.

To eliminate this problem, you can edit the root sting to specify which disk you want it to load from.  Example for you internal drive could look something like this:
```
     title Ubuntu Install on Internal HD
     root (hd0,0)
     ...
     
     title Ubuntu install on USB HD
     root (hd1,0)
     ...

```

Where (hd0,0) is the partition of your Ubuntu install on your internal drive and (hd1,0) is the partition of your Ubuntu install on you USB drive.

---

### Post by rixtr66 on 2008-08-08
ok that explains alot,where is the root string? isit in the grub menu?
someone told me to arrange the bios like this;dvd,usbhd,1sthd,in otherwords,
(hd1,0)1st(hd0,0)2nd is this correct or should i put (hd0,0)1st?
rick:confused:

---

### Post by tariquepark on 2008-08-08
ok thats a great explanation falcon61102 :)
if your computer is fairly new there may be 2 sections in the bios for booting
one is the boot sequence by device type (hd usb cdrom lan etc)
two is boot device priority (to select which hard disk or cdrom if you have 2 or more of either)
i think in your case you would be better with this

sequence: cdrom usb hdd
but you must label each entry clearly in the menu.lst file to avoid any confusion later when booting trying to figure which grub your using :)

---

### Post by falcon61102 on 2008-08-08
It really doesn't matter the BIOS settings.  All that is going to do is help you boot easier from the USB drive when you have it plugged in and default to the HD when you don't, which is handy but it doesn't resolve your problem.

Yes, the root strings are in your GRUB menu.lst.  Remember, you have two of them to edit, one on your HD and one on your USB drive.  What I recommend is boot up from your USB Drive.  Make sure your internal HD is mounted if it doesn't automount. Then run:
```
sudo grub
find /boot/grub/stage1 
```
That will give you a list of the partitions that have GRUBS on them.  You should see at least two.

Exit the Grub menu by typing "Exit"

Then open the menu.lst for you internal HD with:
```
sudo gedit /boot/grub/menu.lst
```

If you scroll through that file you should come to a section with all your installs listed.  What I recommend is once you identify which install is which, you add a comment to the Title portion to help you remember.  For instance, your default OS to load should be the one on the USB HD so you can add "- USB Install" to the title to remind you that is the USB Drive.

The Ubuntu installs on USB Drive should match up with on of the outputs from the find command that just ran.  Now you need to change the settings for your internal HD.  When looking at the menu.lst, they should look identical to the listings for your USB drive, which is the problem.  Change the root setting to the other output from the find command, save the file and close.  Now you should be able to boot from both.

If you run into problems or this is a little much, post the output to the find command and your the contents to you menu.lst and I'll help.

---

### Post by rixtr66 on 2008-08-09
ok i kind understand what you want done,but i dont really feel comfortable
messing around with the grub menu.so ill post the outputs and hopefully
you can help,im alittle surprised that the usb drive is listed first,when i installed kubuntu first on the 1st hd,then installed ubuntu on the usb drive.anyway ;find /boot/grub/stage1
                (hd0,0)
                (hd1,0)

gedit /boot/grub/menu.lst;


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
# kopt=root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6be084e9-38f2-4680-a797-dd183bfe6e7f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		kUbuntu 8.04.1, kernel 2.6.24-20-generic (on /dev/sda1)
root		
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=a3a688ff-4979-4275-bb30-207a688b9f94 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		kUbuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode) (on /dev/sda1)
root		
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=a3a688ff-4979-4275-bb30-207a688b9f94 ro single 
initrd		/boot/initrd.img-2.6.24-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		kUbuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a3a688ff-4979-4275-bb30-207a688b9f94 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		kUbuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a3a688ff-4979-4275-bb30-207a688b9f94 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		
kernel		/boot/memtest86+.bin  
savedefault
boot

i hope this helps,cause its giving me the willys:)
rick

---

### Post by rixtr66 on 2008-08-09
fixed the kU onthe menu.sorry
rick

---

### Post by falcon61102 on 2008-08-09
Ok.. no problem.  Here is an updated exerpt from you menu.lst.  It's way down at the bottom, I left the title portion in as a reference.  
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title kUbuntu 8.04.1, kernel 2.6.24-20-generic (on /dev/sda1)
root **(hd1,0)**
kernel /boot/vmlinuz-2.6.24-20-generic root=UUID=a3a688ff-4979-4275-bb30-207a688b9f94 ro quiet splash 
initrd /boot/initrd.img-2.6.24-20-generic
savedefault
boot

```

Change is in bold.  Just add (hd1,0) to each section following this one and that should do it.

---

### Post by rixtr66 on 2008-08-09
ok i changed the grub menu list,seems strange to have (hd1,0)
on kubuntu cause its actually (hd0,0)an visa verse for ubuntu
but it worked it boot with the usb hd unplugged,
and plugged in it boots to both,except on a restart,it goes
to kubuntu without showing the boot list.but i think i can
live with that!thanks for helping,i learned quite a bit.
rick:)

---

### Post by tariquepark on 2008-08-09
glad you got it sorted :)

---

### Post by falcon61102 on 2008-08-09
No problem, glad it worked out.  If you look around in the menu.lst some more, you will see it has settings to display or hide the menu as well as how long you have to make a selection.

---

