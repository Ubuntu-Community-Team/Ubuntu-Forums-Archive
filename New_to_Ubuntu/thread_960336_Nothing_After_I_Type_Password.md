---
title: "Nothing After I Type Password???"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by buffettologie on 2008-10-27
I just switched from Vista to Ubuntu on my T61 laptop the other day and so far I really like the change. I'm not at all tech saavy but I was fed up with Vista and decided to try Ubuntu before going out to buy a Windows XP copy. 

My main concern is that sometimes (every other time or so) when I turn my computer on it takes me to the login screen and I type my username/password and then a little music plays and then I get a tan colored screen. Often times this only lasts for a few seconds and then I'm on, but often it queues infinitely until I turn it off and back on. Thoughts?

I tried searching but didn't have much luck since I wasn't exactly sure what this was called.

Thanks for anyone's help.

---

### Post by LowSky on 2008-10-27
If your saying it happen only sometimes that doesn't really point us toward a software issue, but you can disable required sign on.

[QUOTE=http://www.tech-recipes.com/rx/2780/ubuntu_how_to_enable_automatic_login/]1. Go to the Main Menu. Select System, mouseover Administration, and select Login Window.

2. When prompted, enter the administrator password and click the OK button.

3. In the Login Window Preferences window, select the Security tab.

4. Check the Enable Automatic Login checkbox. 

5. Select your username from the User dropdown.

6. Click the Close button.[/QUOTE]

---

### Post by buffettologie on 2008-10-27
Thanks so much, I'll give it a try.

---

### Post by buffettologie on 2008-10-27
That has failed to solve the problem, any one have any other ideas?

---

### Post by bodhi.zazen on 2008-10-27
Not sure why it is hanging, what type of videocard do you have ?

Instead of rebooting, try hitting Ctrl-Alt-Backspace (should bring you back to the log in screen).

---

### Post by germanix on 2008-10-27
I am no expert but maybe your system is looking for some applet or application and cannot find it, or has problems with starting it. This could help, if not then at least one will know that this is not the problem.
Go to Systems > Preferences > Sessions then click the Startup programs Tab. You can disable a startup program in the list by unchecking the enabled check box beside it.
You will find the following entries:
Bluetooth manager: if you do not use blue tooth then disable it.
Check for Harware drivers: If you are happy with your drivers it is safe to disable.
Evolution Alarm. if you dont use Evolution calender then disable it.
Network manager: if notebook leave on. If desktop with static Ip adress choose.
Power manager: suggest you leave this on.
Print queue: leave on if you use a printer.
Tracker: leave on if you use the search function.
Update notifier: Can switch off but then you must do manual updates.
User folder update: If you use one language only take it out.
Visual Assistance: Assume you dont need. uncheck
Volume manager: this automounts cameras, Cd or DVD. leave it on.

if nothing else your system should start faster. If this does not solve the problem please let us know.

---

### Post by buffettologie on 2008-10-27
Thanks, I removed many of those things under my startup like you recommended and I'll see how it goes.

Would it have something to do with the kernel that I'm using? I ended up with 6 dead signons in a row and finally hit ESC to go into the screen where I select the kernel and chose a different one.

---

### Post by buffettologie on 2008-10-27
> **bodhi.zazen said:**
> Not sure why it is hanging, what type of videocard do you have ?

Instead of rebooting, try hitting Ctrl-Alt-Backspace (should bring you back to the log in screen).

How do I determine what type of video card I have?

---

### Post by LowSky on 2008-10-27
> **buffettologie said:**
> 
Would it have something to do with the kernel that I'm using? I ended up with 6 dead signons in a row and finally hit ESC to go into the screen where I select the kernel and chose a different one.
 please open this file and tell us Which kernel worked, in terminal type
```
gedit /boot/grub/menu.lst
```
This way we can maybe figure out what broke and what still works.

Thanks

---

### Post by buffettologie on 2008-10-27
> **bodhi.zazen said:**
> Not sure why it is hanging, what type of videocard do you have ?

Instead of rebooting, try hitting Ctrl-Alt-Backspace (should bring you back to the log in screen).

> **LowSky said:**
> please open this file and tell us Which kernel worked, in terminal type
```
gedit /boot/grub/menu.lst
```
This way we can maybe figure out what broke and what still works.

Thanks


I put that in and the output was this: 

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
# kopt=root=UUID=4e63fc9d-9ff8-4666-8ffd-3a9170092450 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4e63fc9d-9ff8-4666-8ffd-3a9170092450 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4e63fc9d-9ff8-4666-8ffd-3a9170092450 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4e63fc9d-9ff8-4666-8ffd-3a9170092450 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4e63fc9d-9ff8-4666-8ffd-3a9170092450 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bodhi.zazen on 2008-10-27
What is the output of :

```
sudo lshw -short | grep display
```

---

### Post by buffettologie on 2008-10-27
> **bodhi.zazen said:**
> What is the output of :

```
sudo lshw -short | grep display
```


/0/100/2                           display     Mobile GM965/GL960 Integrated Graphics Controller
/0/100/2.1                         display     Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by bodhi.zazen on 2008-10-27
Well , you have an intel GM965/GL960

I do not know this card, but here are a few links :

[http://ubuntuforums.org/showthread.php?t=709672](http://ubuntuforums.org/showthread.php?t=709672) # See post 12

and 

[http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

---

