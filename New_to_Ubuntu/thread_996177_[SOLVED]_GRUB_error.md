---
title: "[SOLVED] GRUB error"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by xecure on 2008-11-28
Hi there,

I recently installed 8.10 and it hadn't been running smoothly for me. My apps would often freeze and graphics weren't rendered well at all (this never happened to me in 8.04 and 7.10). I thought this was because I had a very small swap space so I load in my ubuntu CD and use GParted make my ext3 partition smaller and my linux-swap a littter larger. After doing this i tried restarting and Grub would give me an error. It said "error 17" (i believe) I was wondering if this could be fixed or did i permanently damage my installation?

---

### Post by Tyke91 on 2008-11-28
Error 17 in grub is usually caused by grub trying to boot something that does not exist. It happens alot if you install a linux distro, but then remove it without fully resetting the MBR.

I'm not quite sure how to solve your problem... try booting into a live CD and fixing grub?

---

### Post by zzHanks on 2008-11-28
This error is common, It has been solved.

Google is your friend ;)

-
I'm sorry about that.

---

### Post by Elfy on 2008-11-28
> **zzHanks said:**
> This error is common, It has been solved.

Google is your friend ;)

Very helpful - from the CoC - which you agreed to, if you don't want to help then don't. > RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question

xecure - boot the livecd and run this command and post the result ```
sudo fdisk -l
``` here

It could be that grub just neds to be reinstalled - or it could be that the UUIDs for partitions have chnaged and grub can't find them - all easily solved.

---

### Post by xecure on 2008-11-28
output:```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971520    7  HPFS/NTFS
/dev/sda2            2612        9729    57175335    5  Extended
/dev/sda5            2700        9722    56412216   83  Linux
/dev/sda6            2612        2699      706797   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by unutbu on 2008-11-28
xecure, when you boot up your machine, do you get to the GRUB menu first, or do you see GRUB Error 17 before that?

If you see the GRUB menu, then try this:
[http://ubuntuforums.org/showpost.php?p=5235963&postcount=2](http://ubuntuforums.org/showpost.php?p=5235963&postcount=2)

If it does not work, please post your /mnt/boot/grub/menu.lst and the output of
```

blkid 
```
and we'll go from there.

Edit: If you are seeing "GRUB Error 17" before the GRUB menu, skip straight to forestpixie's instructions below.

---

### Post by Elfy on 2008-11-28
Ok we can try to restore grub first

Open a terminal and do
```

sudo grub
```
then
```
find /boot/grub/stage1
```
That should get a result like hd0,4

Then do this replacing (hd0,1) with your result

```
grub> root (hd0,1)
```

Then 
```
grub> setup (hd0)
```

If it fails do this and post the result of the last command please

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sda5 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
```

---

### Post by xecure on 2008-11-28
```
grub> setup (hd0)

Error 17: Cannot mount selected partition
```and 'cat /mnt/tmp/boot/grub/menu.lst' gave me:```
$ cat /mnt/tmp/boot/grub/menu.lst
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
# kopt=root=UUID=63f5de53-db58-4892-addc-bc0b94e7ae02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63f5de53-db58-4892-addc-bc0b94e7ae02

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		63f5de53-db58-4892-addc-bc0b94e7ae02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=63f5de53-db58-4892-addc-bc0b94e7ae02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		63f5de53-db58-4892-addc-bc0b94e7ae02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=63f5de53-db58-4892-addc-bc0b94e7ae02 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		63f5de53-db58-4892-addc-bc0b94e7ae02
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
```

---

### Post by Elfy on 2008-11-28
Run ```
sudo blkid
``` please and post it here

I must remember that grub uses UUID now :)

---

### Post by xecure on 2008-11-28
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="4A0AA3C70AA3ADFF" TYPE="ntfs" 
/dev/sda5: UUID="63f5de53-db58-4892-addc-bc0b94e7ae02" TYPE="ext3" 
/dev/sda6: UUID="57b21170-a8c1-4333-91c2-6729444d7d12" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
```

---

### Post by Elfy on 2008-11-28
<snip>

mmm when you ran the grub commands did you get a result from find /boot/grub/stage1?

When you resized the drive did anything untoward happen?

Could you open th partition editor again and do a screenshot of it - Apps>Accessories>Take Screenshot - use the manage attachment tools in New Reply to attach the scrnsht

---

### Post by unutbu on 2008-11-28
Perhaps try 
```

sudo umount /dev/sda5
sudo e2fsck -C0 -pfv /dev/sda5
```
This command will attempt to repair any problems it detects in your filesystem.

Here are what the flags mean:```

-C0 draw a completion bar
-p  auto repair ('preen') the filesystem
-f  force checking even if the filesystem seems clean
-v  verbose mode

```
When it is done, try rebooting.

---

### Post by xecure on 2008-11-28
> **forestpixie said:**
> <snip>

mmm when you ran the grub commands did you get a result from find /boot/grub/stage1?

When you resized the drive did anything untoward happen?

Could you open th partition editor again and do a screenshot of it - Apps>Accessories>Take Screenshot - use the manage attachment tools in New Reply to attach the scrnsht

this is the out puts i got from the grub commands:```
grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,1)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 
```
and the Screen Shot is included below

@ unutbu: I tried it but no luck =(

---

### Post by Elfy on 2008-11-29
Ok you knwo where I said > Then do this replacing (hd0,1) with your resultyou need to do that :)

> grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,[COLOR="Red"]4[/COLOR])try again and report back please.

---

### Post by Elfy on 2008-11-29
Ok you knwo where I said > Then do this replacing (hd0,1) with your resultyou need to do that :)

> grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,[COLOR="Red"]4[/COLOR])try again and report back please.

---

### Post by Elfy on 2008-11-29
Ok - you didn't do as I said earler and replace hd0,1 with your result :)

Run the grub restore commands again and when it tells you

grub> find /boot/grub/stage1
 [COLOR="Red"](hd0,4)[/COLOR]

Use that

grub> root (hd0,4)

---

### Post by xecure on 2008-11-30
```
grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)
```thats all i get. After rebooting i also et error 17

---

### Post by Elfy on 2008-11-30
> 
grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub>
Like this?

Not sure then - try using supergrub - [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by xecure on 2008-11-30
oops sorry, i forgot to do the 'grub> setup (hd0)'

it works now, thanks a bunch!

---

### Post by xecure on 2008-11-30
oops sorry, i forgot to do the 'grub> setup (hd0)'

it works now, thanks a bunch!

---

### Post by TheOtherJohnC on 2008-12-07
Just want to add that I too get this error and want to explain my overall experience with Ubuntu in case the powers that be care about new user experiences:

This is my first experience with Ubuntu.  I installed it yesterday *finally* got my network configuration working with a static IP address (first major bug, every time you reboot the network manager blows away static IP settings), then *finally* got my nvidia card working properly, it was offered to be activated as a non open source driver but clicking away accomplished nothing, found instructions online to update it to the manufacturers driver.

Later Ubuntu offered 151 updates even though I had just downloaded and installed it fresh that day (this was a real wtf? moment for me, how could there be so many updates in a freshly downloaded setup?), downloaded the updates, repeatedly got an error when they were being installed about fonts, finally the update started going properly after attempting it three times (note that I changed nothing, it just spontaneously started working on the third attempt again, wtf?), started the updates, got up this morning and rebooted after updates were installed and first off get an error message about the NVIDIA card and it offered three choices, I attempted to use a backup, didn't work, attempted to use a basic setup, didn't work, got prompted again the same three options so finally took the option to reconfigure and still no joy, rebooted and got this grub error 17.

Reading through this thread I get several impressions: this grub problem is common, updates are a thing to be feared, possibly buggy updates can be released at any time and when they are there is no responsibility taken by anyone to ensure it won't happen again and explain why it happened in the first place.

I'm going to try the help suggested, see if I can get back my booting into windows for now and play with this again later when there is some appearance of an Ubuntu that is a little more stable.  Clearly 8.1 is far from stable and the updates are even worse.

I've tried Linux off and on for at least a decade now and I can see very little has changed other than, if you have the perfect combination of really common hardware, it will generally work for most people, that's a step up, but for some reason I'm always finding myself at a command line shortly after installing Linux trying to fix things that should just work.

---

