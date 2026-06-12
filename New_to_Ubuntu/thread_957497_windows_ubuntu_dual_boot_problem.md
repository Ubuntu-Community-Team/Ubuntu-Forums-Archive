---
title: "windows /ubuntu dual boot problem"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-24
hi,
 i installed ubuntu 7.10 in my system in one partition and in the other i already had windows xp. after i installed ubuntu, i tried to get into windows at startup through GRUB loader... but it failed.. i mean.... when i choose windows in the loader and press ENTER, it says some error number and i cant get into windows. 

But i can get into ubuntu. There is no problem with it. why is it so... 

i have tried reinstalling both operating systems several times (first XP and then ubuntu), but every time i get the same result... 
I want to get into windows....
what should i do.. please help..

---

### Post by Crandom on 2008-10-24
What is the error number? Give us that ans we can probably help you.

---

### Post by eternalnewbee on 2008-10-24
What's the error message that you're getting?

---

### Post by luckydeveloper on 2008-10-24
hey, i actually had xp some 3 days back in my pc and i formatted the whole pc yesterday to put vista < alone > in it.I had the problem when i had xp in the pc.  

And now since you guys asked me the error no. i could not recollect the error no. so i just installed 7.10 again in the pc
now i have
vista ultimate in C;\
and in the remaining portion i have ubuntu 7.10

The same problem occurs with vista also...

Now, in the grub loader, when i choose windows vista and press enter.. the pc just restarts (without giving any error message) but there is no problem with ubuntu 7.10. ubuntu loads swiftly...

why is it so... i want to get into vista as well..
please help

---

### Post by Crandom on 2008-10-24
Can you please paste the output from this command:
```
sudo fdisk -l
```
and the data in the file when you use this command:
```
gksudo gedit /boot/grub/menu.lst
```
into this thread.

To get open the program you need to enter the commands, go to Applications > Accessories > Terminal.

---

### Post by caljohnsmith on 2008-10-24
In addition to what Crandom asked for, how about booting your Vista Install CD, going to the command line, and running:
```
bootrec /fixboot
chkdsk /r
```
And run the chkdsk as many times as it takes until it reports no errors. Then run:
```
bootrec /rebuildbcd
```
After that, reboot, and let me know what exactly happens when you boot Vista again. We can work from there if you want. :)

---

### Post by luckydeveloper on 2008-10-24
This is the output for fdisk -l


Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5772    46357504    7  HPFS/NTFS
/dev/sda2            5773        9540    30266460   83  Linux
/dev/sda3            9541        9730     1526175   82  Linux swap / Solaris


this is the content for grub/menu.lst

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
# kopt=root=UUID=fe26af79-5e3f-4acc-8675-96622fab9b3e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe26af79-5e3f-4acc-8675-96622fab9b3e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe26af79-5e3f-4acc-8675-96622fab9b3e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by luckydeveloper on 2008-10-24
hey caljohnsmith, i dont have the vista boot cd now.. at present..

---

### Post by caljohnsmith on 2008-10-24
> **luckydeveloper said:**
> hey caljohnsmith, i dont have the vista boot cd now.. at present..
Your Grub's entry for Vista in your menu.lst is fine, so you most likely have a Vista problem and not a Grub problem at this point; you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes. :)

---

### Post by luckydeveloper on 2008-10-24
hey but,actually some 6 months back, everything was running normal. Why suddenly this problem arises. this happens in both xp and vista. while i was installing ubuntu in 6.10 times, everything was working fine. i could boot both windows and ubuntu properly. 

But at some point of time during these days, do you think i could have made any mistake in the hard disk and in any other stuff. what could have gone wrong???


Now, while installing ubuntu 7.10 i chose the following disk settings

/dev/sda1 ntfs primary
/dev/sda2 ext3 primary  root
/dev/sda3 swap primary

is anything wrong about how i have chosen the above settings.

---

### Post by caljohnsmith on 2008-10-24
Your partitioning scheme looks fine. If you had both XP and Vista working OK before, it could be you have a hardware problem now. Can you think of anything that happened before you started having problems that might give a clue what changed so that XP/Vista started having problems? Say as much as you can about what led up to the problems. 

If I were you, I would probably start by at least checking the health of the HDD, which if you don't have a diagnostics CD that came with your HDD, you can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com") instead (it has lots of great HDD diagnostic tests).

---

### Post by luckydeveloper on 2008-10-24
so you say the problem is with my HDD...

---

### Post by luckydeveloper on 2008-10-24
i remember this,,, 

some days back i decided to keep  only ubuntu in my system. so i just inserted my ubuntu cd in and chose full hard drive install (guided) of ubuntu. 
could it have damaged my HDD ????

by the way, how can my HDD get damaged. its a hardware. i just formatted and installed several operating systems during the time. .. thats it.. how is that possible.


but this problem does not exit if i use wubi installer. wubi installer installs ubuntu swiftly and i am able to load both operating systems without any problems from the boot time loader. 

what should i do now.. can i try format my whole system and try it again( but i'll lose all my data in vista :(  ) ??? 

please help

---

### Post by caljohnsmith on 2008-10-24
I think you are misunderstanding me; since you said that Windows + Ubuntu were working fine before, and it is only recently that you started having problems with both XP and Vista, that means that you could be having some sort of hardware issue. Ubuntu would not have damaged your HDD though, I was only suggesting you check the health of your HDD in case it is starting to go bad. I don't think there's a big chance of it being a problem with your HDD since you said Ubuntu works, but if I were you I would at least check your HDD. 

So are you saying that Windows XP and Vista work fine when you use the Wubi installer, but XP and Vista don't work when you do the dual boot method?

---

### Post by luckydeveloper on 2008-10-24
yep thats the catch. they work good when i use wubi installer to install ubuntu,

this problem comes only when i use live cd and install it from the ubuntu live environment....i mean.. when i use dual boot method

---

### Post by caljohnsmith on 2008-10-25
> **luckydeveloper said:**
> yep thats the catch. they work good when i use wubi installer to install ubuntu,

this problem comes only when i use live cd and install it from the ubuntu live environment....i mean.. when i use dual boot method
You probably have problems with the dual boot method because of resizing the Windows partition I'm guessing; have you tried at some point setting up all your partitions first and then installing Windows, and after that installing Ubuntu? That would probably fix your Windows problem, but if reinstalling is not a viable option now, you could try and repair Windows. If you still have Vista installed, I would recommend trying the instructions from post #6.

---

### Post by luckydeveloper on 2008-10-25
i seriously dont want to reinstall now ..  it will take time for me to back up all my vista docs through ubuntu( saviour :) ).... but let me explain the process i am following to install xp and ubuntu...

usually, what i do is.. i will first delete all the partitions with xp install cd.. then create one and only partition(NTFS) of 45 GB. I will then install xp in that partition. i have a 80 GB hard disk. i wont touch the remaining free space(40 GB) during xp install. 

after installing xp,

Then for installing ubuntu, the ubuntu installation wizard will show me 40 GB free space out of 80GB. i will then create swap and root space in that 40 GB free space. Then it will install ubuntu.

is there anything problem with the above process....??

---

