---
title: "Strange computer behavior"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-24
When I shut down and then restart my computer, all I get is a blank screen. I then have to unplug it from the wall to get it to shut back down because the power button won't work. The only way I can get it to boot back up after totally shutting it down is to press "ESC" at the grub prompt and manually boot in. Is this normal?

---

### Post by gerben1 on 2008-07-24
perhaps there is some wrong default setting in Grub's menu.lst, that you circumvent by choosing something different? It may help if you post your:
/boot/grub/menu.lst

---

### Post by mczonie on 2008-07-24
> **gerben1 said:**
> perhaps there is some wrong default setting in Grub's menu.lst, that you circumvent by choosing something different? It may help if you post your:
/boot/grub/menu.lst

Sorry, but I have no idea what that is. I'm a total noob.

---

### Post by rockstarrem on 2008-07-24
Type "nano /boot/grub/menu.lst" and copy and paste the file here.

---

### Post by mczonie on 2008-07-24
> **rockstarrem said:**
> Type "nano /boot/grub/menu.lst" and copy and paste the file here.

Type it where?

---

### Post by Dylock on 2008-07-24
Get to a terminal somehow (maybe use recovery mode?) and then you can get whats inside your grub file

---

### Post by gerben1 on 2008-07-24
when you are in ubuntu open a terminal:
Application->Accessoires->Terminal

then in the terminal type:
```

gksu gedit /boot/grub/menu.list

```
it will ask you for your password and after you entered it open menu.list in the text editor. Copy the contents of that file into a forum post, so that someone may be able to tell if there is someting wrong in it.

---

### Post by mczonie on 2008-07-24
> **gerben1 said:**
> when you are in ubuntu open a terminal:
Application->Accessoires->Terminal

then in the terminal type:
```

gksu gedit /boot/grub/menu.list

```
it will ask you for your password and after you entered it open menu.list in the text editor. Copy the contents of that file into a forum post, so that someone may be able to tell if there is someting wrong in it.

OK, I just did that, but the field in menu.list is blank. Is there something else I need to do to make it show the text I need to copy?

---

### Post by gerben1 on 2008-07-24
are you sure you did not mistype the name, or missed a / or something?

can you post the output of this command in terminal:
```

ls -l /boot/grub

```
(it will show a list of the files in that directory with details)

---

### Post by gerben1 on 2008-07-24
I am sorry I mistyped the command...
it is menu.lst
not menu.l**i**st

so like this:
```

gksu gedit /boot/grub/menu.lst

```

---

### Post by mczonie on 2008-07-24
> **gerben1 said:**
> are you sure you did not mistype the name, or missed a / or something?

Yes, I'm absolutely sure because I copied and pasted it. the code that was posted was exactly what I entered.



> can you post the output of this command in terminal:
```

ls -l /boot/grub

```
(it will show a list of the files in that directory with details)

OK, here it is:

total 204
-rw-r--r-- 1 root  999    197 2008-06-30 14:07 default
-rw-r--r-- 1 root  999     15 2008-06-30 14:07 device.map
-rw-r--r-- 1 root  999   8056 2008-06-30 14:07 e2fs_stage1_5
-rw-r--r-- 1 root  999   7904 2008-06-30 14:07 fat_stage1_5
-rw-r--r-- 1 root  999     16 2008-06-30 14:07 installed-version
-rw-r--r-- 1 root  999   8608 2008-06-30 14:07 jfs_stage1_5
-rw-r--r-- 1 root root   4703 2008-07-19 21:43 menu.lst
-rw-r--r-- 1 root root   4265 2008-07-19 21:43 menu.lst~
-rw-r--r-- 1 root  999   7324 2008-06-30 14:07 minix_stage1_5
-rw-r--r-- 1 root  999   9632 2008-06-30 14:07 reiserfs_stage1_5
-rw-r--r-- 1 root  999    512 2008-06-30 14:07 stage1
-rw-r--r-- 1 root  999 108356 2008-06-30 14:07 stage2
-rw-r--r-- 1 root  999   9276 2008-06-30 14:07 xfs_stage1_5

---

### Post by mczonie on 2008-07-24
> **gerben1 said:**
> I am sorry I mistyped the command...
it is menu.lst
not menu.l**i**st

No problem.

> so like this:
```

gksu gedit /boot/grub/menu.lst

```

OK, it worked this time. here is the result:

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
timeout		3

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
# kopt=root=UUID=35a5204f-326b-41e2-ad69-5a0b865d78e6 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=35a5204f-326b-41e2-ad69-5a0b865d78e6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=35a5204f-326b-41e2-ad69-5a0b865d78e6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=35a5204f-326b-41e2-ad69-5a0b865d78e6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=35a5204f-326b-41e2-ad69-5a0b865d78e6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

(LOL, it looks like the forum software has turned some of it into emoticons.)

---

### Post by gerben1 on 2008-07-24
I don't see anything wrong, but I also do not know too much about it...
perhaps someone else will

---

### Post by philinux on 2008-07-24
There is nothing wrong with your menu.lst

when you say you have to boot manually what exactly do you mean.

---

### Post by mczonie on 2008-07-24
> **philinux said:**
> There is nothing wrong with your menu.lst

when you say you have to boot manually what exactly do you mean.

I mean I have to press "ESC" at the grub prompt and then select the generic mode option and press "enter" to get to the log in screen.

Is this normal, or should it be taking me to the log in screen automatically?

---

### Post by philinux on 2008-07-24
> **mczonie said:**
> I mean I have to press "ESC" at the grub prompt and then select the generic mode option and press "enter" to get to the log in screen.

Is this normal, or should it be taking me to the log in screen automatically?

What happens if you leave it to do it's stuff.

You should get the bios splash screen then the grub menu with the countdown timer then it should fire up.

---

### Post by mczonie on 2008-07-24
> **philinux said:**
> What happens if you leave it to do it's stuff.



Nothing. All I get is a blank screen, then I literally have to unplug the f*ing thing from the wall to get it to shut back down again, because the power button won't work.

Maybe I'm just not waiting long enough. How long should it take?

---

### Post by Tom--d on 2008-07-24
> **mczonie said:**
> Nothing. All I get is a blank screen, then I literally have to unplug the f*ing thing from the wall to get it to shut back down again, because the power button won't work.

Maybe I'm just not waiting long enough. How long should it take?

Default is 3 seconds, then it boots into the kernel.

---

### Post by philinux on 2008-07-24
> **mczonie said:**
> Nothing. All I get is a blank screen, then I literally have to unplug the f*ing thing from the wall to get it to shut back down again, because the power button won't work.

Maybe I'm just not waiting long enough. How long should it take?

Just to test this - leave it. See what happens

It might be running the file system check fsck

If so it could take a few minutes but we can sort that out later.

Are you running Hardy or Gutsy

---

### Post by mczonie on 2008-07-24
> **philinux said:**
> Just to test this - leave it. See what happens

It might be running the file system check fsck

If so it could take a few minutes but we can sort that out later.


OK, I'll shut it down and start it up again right before bed tonight and then report back in the morning. If it doesn't boot up after sitting all night, then we'll know something's really wrong.

I have no idea what it could be except for a hardware problem, since this is a brand new install.

---

### Post by philinux on 2008-07-24
One thing rather than unplug do this.

With your pinkies hold down Alt and Print Screen then type

R E I S U B

This will reboot the system gently.

---

### Post by mczonie on 2008-07-24
> **philinux said:**
> One thing rather than unplug do this.

With your pinkies hold down Alt and Print Screen then type

R E I S U B

This will reboot the system gently.

Ok, thanks for the tip. I'll remember that.

---

### Post by mczonie on 2008-07-26
OK, I left it all night and it still didn't start up.

alt + print screen + reisub didn't work to get me out either, I had to unplug the computer like usual.

The only thing I can think of is that this is a hardware problem, since this is a brand new install.

---

### Post by CatKiller on 2008-07-26
> **mczonie said:**
> I then have to unplug it from the wall to get it to shut back down because the power button won't work.

I don't know how to fix your specific shutdown issue, but you don't need to do this. Holding the power button down for 5 seconds should be sufficient to turn the computer off.

---

### Post by stevoo on 2008-07-26
If 
holding down ctrl+PrintScrn and then pressing
R+S+E+I+U+B

doesnt do anything, then your computer freezes. 
Something doesnt proccess normal during that time

But holding downthe power buttin for 5 - 10 secs should kill the power with out taking out of the wall

But to get thinks straight. 
When you start the computer if you leave it manually to start with out selecting a boot it will not open ? 
And if you leave it to open on its own it will stop responding ? 

If that is the case are you still selecting the same boot option like the starting one ?

---

### Post by mczonie on 2008-07-26
> 
When you start the computer if you leave it manually to start with out selecting a boot it will not open ? 
Correct.> 
And if you leave it to open on its own it will stop responding ? Correct.

> If that is the case are you still selecting the same boot option like the starting one ?

I press "esc" at the grub prompt and then select the non-recovery mode (or whatever it's called) and press "enter."

---

### Post by Crazyap7 on 2008-07-26
Don't hit alt+prt sc+REISUB, hit alt+sys rq+REISUB

Sometimes the prt sc is under the insert in laptops and sys rq under delete.

---

### Post by stevoo on 2008-07-26
but is it 
REISUB ? cause i know it like 
RSEIUB

The r stands for put keyboard in raw mode
The s for sync the disk
The e for terminate all processes
The i for kill all processes
The u for remount all filesystems read only
The b for reboot the system


Maybe something wrong with the newest kernel. 
Try installing the older one. 
2.26.19 ? 
i think that is the one.
And try booting from that one. 
See what happens

---

### Post by Crazyap7 on 2008-07-26
Yeah i'm sure it's REISUB. I remember it from: Raising Elephants Is So Utterly Boring.

---

### Post by mczonie on 2008-07-26
> **stevoo said:**
> 
Maybe something wrong with the newest kernel. 
Try installing the older one. 


I'm going to do a complete reinstall tomorrow and see if that works.

---

### Post by mczonie on 2008-07-26
> **Crazyap7 said:**
> Don't hit alt+prt sc+REISUB, hit alt+sys rq+REISUB

Sometimes the prt sc is under the insert in laptops and sys rq under delete.

On my keyboard, SysRq *is* print screen. They're the same key.

---

