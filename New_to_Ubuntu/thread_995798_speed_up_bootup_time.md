---
title: "speed up bootup time"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-11-28
is there anything i can do to reduce the bootup time on my laptop? i'm not dualbooting i'm only using ubuntu so erm... is there anyway?

---

### Post by philinux on 2008-11-28
How long is it taking now.

From grub to login.
From login to desktop useable.

---

### Post by hyper_ch on 2008-11-28
install bootchart and check what takes how long ;)

---

### Post by Sarmacid on 2008-11-28
You can install the boot up manager and disable some start up services.```
sudo apt-get install bum
```

---

### Post by nkri on 2008-11-28
First, disable any startup options you don't use by going to System>Preferences>Sessions and unchecking what you don't want/need.

Then, try [_this_]("http://ubuntuforums.org/showthread.php?t=254263") thread; this method took about 12 seconds off of my boot time, so hopefully it will help for yours (by the way, the "bonus hack" will not work since it is now built into Ubuntu).

Good luck!
-nkri

---

### Post by barbedsaber on 2008-11-28
every kernel that comes out, shaves about 4 seconds off my boot time, so I am content to wait.
May I suggest that you install startup manager
(I assume it will be sudo apt-get install startup-manager but I am so tired, I am unable to check) activate text during boot, and tell us if any part of it seems to take much longer than others. There may be things you can do to fix something that is looping during boot.
(I say this, assuming your boot time is quite large, that being the reason for you posting this thread, so... forgot what I was gonna say, gotta get more sleep) :)

---

### Post by 133794m3r on 2008-11-28
> **hyper_ch said:**
> install bootchart and check what takes how long ;)

how do i activate this bootchart that you speak of?

---

### Post by hyper_ch on 2008-11-29
you just install it

---

### Post by 133794m3r on 2008-11-29
> **hyper_ch said:**
> you just install it

ok i have it installled but how do i see how long it takes for me to start up what kinda command do i need to do to do that? I can't seem to find it under the apps link so i'm guessing it doesn't have a GUI

---

### Post by jakupl on 2008-11-29
> **133794m3r said:**
> ok i have it installled but how do i see how long it takes for me to start up what kinda command do i need to do to do that? I can't seem to find it under the apps link so i'm guessing it doesn't have a GUI

in terminal you write
```

ls /var/log/bootchart
```

then you see all the bootchart files named with date and number.

then do:

eog /var/log/bootchart/*filename*

to see it.

EDIT: or you just click your way to /var/log/bootchart/

EDIT 2: I usually use this thread [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491). check it out.

---

### Post by 133794m3r on 2008-11-29
[[IMG]http://img525.imageshack.us/img525/6681/intrepid200811291gp6.th.png[/IMG]](http://img525.imageshack.us/my.php?image=intrepid200811291gp6.png)
ok there's my boot chart is there anyway to also remove the grub splash screen? I'm also going to take a look at that guide you told me...
Also i can't find the splashimage line that that guy's talking about so i can remove the grub menu at start up.

---

### Post by jakupl on 2008-11-29
> **133794m3r said:**
> [[IMG]http://img525.imageshack.us/img525/6681/intrepid200811291gp6.th.png[/IMG]](http://img525.imageshack.us/my.php?image=intrepid200811291gp6.png)
ok there's my boot chart is there anyway to also remove the grub splash screen? I'm also going to take a look at that guide you told me...
Also i can't find the splashimage line that that guy's talking about so i can remove the grub menu at start up.

To remove the splash screen, do:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

You will see a line like this near the bottom:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a459dc22-9c50-4dad-8345-f46455524732
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a459dc22-9c50-4dad-8345-f46455524732 ro quiet splash 
```

I usually remove "ro quiet splash", but just removing "splash" will do.

---

### Post by 133794m3r on 2008-11-29
also i don't know if you'd know how to fix this but after i did the little guide thing it's removed my autologin feature so that's added a bit of time to my boot time... >.<

---

### Post by 133794m3r on 2008-11-29
also i don't know if you'd know how to fix this but after i did the little guide thing it's removed my autologin feature so that's added a bit of time to my boot time... >.< 

also when i did that... it completely removed that graphic loading screen i was talking about making it so i didn't have to wait on the choose which kernel menu. I'd like to somehow remove that b/c that adds ~5 seconds to my loading time on its own.

---

### Post by jakupl on 2008-11-29
this is how my menu.lst looks like.

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
timeout		1

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
# kopt=root=UUID=a459dc22-9c50-4dad-8345-f46455524732 ro hpet=disable

## default grub root device
## e.g. groot=(hd0,0)
# groot=a459dc22-9c50-4dad-8345-f46455524732

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
# defoptions=quiet

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
uuid		a459dc22-9c50-4dad-8345-f46455524732
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a459dc22-9c50-4dad-8345-f46455524732 hpet=disable 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a459dc22-9c50-4dad-8345-f46455524732
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a459dc22-9c50-4dad-8345-f46455524732 ro hpet=disable  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a459dc22-9c50-4dad-8345-f46455524732
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Notice the "timeout     1" place. Yours is probably 5. Change it to 1, although if you want to boot in recovery mode, you will need to be snappy if the timeout is only 1.

about the autologin... I'm not sure. I never tried it. Don't like it.

---

### Post by jakupl on 2008-11-29
Hit System, Administration, then Login Window.
Go to the Security tab, check the Enable Automatic Login, and select your user name from the list. That’s it. When your system loads up it should head automatically to the desktop.

---

### Post by 133794m3r on 2008-11-29
yeah i already have it set as me as shown in this screenie

---

### Post by jakupl on 2008-11-29
> **133794m3r said:**
> yeah i already have it set as me as shown in this screenie

and does it work?

---

### Post by 133794m3r on 2008-11-29
sadly no....

---

