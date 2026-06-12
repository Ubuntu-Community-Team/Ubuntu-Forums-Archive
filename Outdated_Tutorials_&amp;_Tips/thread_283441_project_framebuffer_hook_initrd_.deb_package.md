---
title: "project: framebuffer_hook initrd .deb package"
date: 2006-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by evermind on 2006-10-24
# I've resurected my old script which added higer resolution framebuffer
# to the kernels initrd-image. (It worked with Hoary Hedgehog)
# It was meant to be placed inside /etc/mkinitrd/scripts/
# Here the old thread:
[old framebuffer_hook]("http://www.ubuntuforums.org/showthread.php?t=35035#4")

# Now I spent some time porting it to edgy eft. 
# (dapper drake should also work as of 0.3.1-2)
# Also enhanced it a bit and created a .deb package

# so to install: download the package and:
```
sudo dpkg -i framebuffer-initramfs_0.3.1-2_all.deb
```

# currently it does not support many framebuffer devices.
# So I need your support (end of this file):

# atm supported
-vesafb
-radeonfb (not tested on edgy eft)
-sisfb    (not tested on edgy eft)

# NEVER SUPPORTED:
-savagefb, nvidiafb, 
       --> they won't work with X


# The configuration file:
/etc/framebuffer.conf
# you don't need to edit if vesafb and 1024x768@16 is enough for you.
# It also default to vesafb if your vga card is not supported.
# If you want to change the resolution in conjunction 
# with vesafb this are the yet supported resolutions:
800x600 1024x768 1280x1024 1152x864 1600x1200
# depth
8 15 16 24

# the script will use settings 
# to generate a initrd image with highres framebuffer support 
# (if possible using the according modul to your vga-adapter.
# It also alters the kernel cmldline settings in
# /boot/grub/menu.lst|grub.conf
# If you use VESAFB=1 the added option will be sth. like vga=791
# e.g
```
# defoptions=splash quiet vga=791
```
# If you set VESAFB=0 and a either have a supported vga-card or
# provide a custom module FB_MODULES_WITH_PARAMETERS="yourfbmodul and paramters"
# the menu.lst should look similar to this:
```
# defoptions=splash quiet framebuffer
```

# to generate a new initrd type
```
sudo dpkg-reconfigure linux-image-`uname -r`
```
# reboot your system and try to switch to the console via CRTL + ALT + F[1-6]
# So if the result is what you want you're done
# otherwise you need to tweak /etc/framebuffer.conf
# NOTE: vesafb highest refreshrate is 60Hz

# So if your framebuffer modul is not listed above drop me a mail
# or post here. So I'll try to integrate if it don't interfere with X

# hints:
# If the usplash won't show correctly you need to set
DEEPTH=8
# at least when using a radeon 9000 (rv250)

---

### Post by u-foka on 2006-11-02
Hy! This is a very great package! I used it to enable sisfb for my wide lcd (1280x854).

part of my framebuffer.conf
> FB_MODULES_WITH_PARAMETERS="sisfb mode=1280x854x24 rate=60"


It works good, but i found three problems.

1: in the grub/menu.lst it makes some stupid lines:
> kernel          /boot/vmlinuz-2.6.15-27-686 root=UUID=b6aad826-03e1-40da-a3fb-25d148c7ae30 ro quiet splash ERROR: 1280x854 no vesa modes are known for this resolution ERROR: 1280x854 no vesa........

2: usplash only uses 1024*768 resolution on boot up... on shutdown it's ok.

3: TTY1-6 using the correct resolutiun, but is a black line on the top and bottom of the screen.. and it's hiding the last lines from my.

I'm using edgy updated from dapper.

Any ideas?

PS: Sorry for my bad english!

---

### Post by evermind on 2006-11-04
sorry for the delay.

I'll try to fix it

you could try to adjust the resolution in 
/etc/usplash.conf

---

### Post by u-foka on 2006-11-06
Hy!

I worked on it a lot.

I changed the /etc/initramfs-tools/scripts/init-top/framebuffer script to load sisfb and fbcon. It loads it before usplash started. This solved my usplash problems.

The tty problem can be fixed every time when i login to it i type stty rows 50

---

### Post by evermind on 2006-11-06
> **u-foka said:**
> Hy!

I worked on it a lot.

I changed the /etc/initramfs-tools/scripts/init-top/framebuffer script to load sisfb and fbcon. It loads it before usplash started. This solved my usplash problems.


could you post your modified script?

---

### Post by u-foka on 2006-11-07
So. This file is located in /usr/share/initramfs-tools/scripts/init-top

Requires to add "sisfb" to the kernel parameters in grub.

---

### Post by evermind on 2006-11-09
> **u-foka said:**
> So. This file is located in /usr/share/initramfs-tools/scripts/init-top

Requires to add "sisfb" to the kernel parameters in grub.

please test the new release:
-framebuffer script is now included
-as cmd framebuffer is used (instead in your case sisfb)

Please try to set FB_MODULES_WITH_PARAMETERS in /etc/framebuffer.conf to 
```
FB_MODULES_WITH_PARAMETERS=""
```

as your card should be autodetected
just change the resolution and set VESAFB to 0

---

### Post by u-foka on 2006-11-10
Maybe I'm stupid but, where is the new release? 8-) I can't found it at the old location you posted. Or the version is the same?

---

### Post by evermind on 2006-11-10
> **u-foka said:**
> Maybe I'm stupid but, where is the new release? 8-) I can't found it at the old location you posted. Or the version is the same?
last line in first post!
this is the new release (old one was 0.3.1-2)
I had problems with attachments so I placed it here
EDIT: removed link --> new release first post

---

### Post by u-foka on 2006-11-11
Ok! Sorry. I will try it tonight :)

---

### Post by u-foka on 2006-11-14
Hy! Sorry for the delay! I tryed it now, but it seems to be do nothing. I set the parameters how you sad, the script output looking good ( ADDED MODULE sisfb ADDED MODULE fbcon stb... ) but when i regenerated the initramfs and rebooted my system never loads sisfb :S

P.S.: i removed all my modifications before tryed it.

---

### Post by evermind on 2006-11-14
could you try the following?

```

mkdir /tmp/extractinitrd;cd /tmp/extractinitrd/; gzip -dc /boot/initrd.img-`uname -r`|cpio -i;find |egrep 'framebuffer|sisfb'

```
post the output

```

cat scripts/init-top/framebuffer |egrep -i 'framebuffer|sisfb'

```
post the output

```

cat /boot/grub/menu.lst|egrep 'defoptions|framebuffer
```
post the output

---

### Post by u-foka on 2006-11-14
```
u-foka@u-foka-laptop:~$ mkdir /tmp/extractinitrd;cd /tmp/extractinitrd/; gzip -dc /boot/initrd.img-`uname -r`|cpio -i;find |egrep 'framebuffer|sisfb'
55665 blocks
./etc/modprobe.d/blacklist-framebuffer
./lib/modules/2.6.17-10-386/kernel/drivers/video/sis/sisfb.ko
./scripts/init-top/framebuffer
u-foka@u-foka-laptop:/tmp/extractinitrd$ cat scripts/init-top/framebuffer |egrep -i 'framebuffer|sisfb'
        framebuffer*)
                FRAMEBUFFER=true
elif [ "$FRAMEBUFFER" = "true" ]; then
        modprobe -Q sisfb mode=1280x854x24 rate=60


```

the 3rd command drop an empty prompt for me.

---

### Post by evermind on 2006-11-14
> **u-foka said:**
> 
the 3rd command drop an empty prompt for me.


so try to add framebuffer to your kernel cmdline.

also it would be great if you can put add
set -x
somewhere in /etc/framebuffer.conf
and regenerate the initrd
with
dpkg-reconfigure linux-image-`uname -r` &>initrd_logfile
attach the outputfile initrd_logfile here

---

### Post by reacuna on 2006-11-14
Hi,
I've been trying to use the radeonfb with your script, but when generating the initrd.img, I get the following output:

```

DEBUG: MODULESDIR /lib/modules/2.6.17-10-generic
DEBUG: FB_MODULES_WITH_PARAMETERS:"radeonfb mode-option=1400x1050-16@60"
DEBUG: LOAD_CMDL_MODULES_REVERSED:"radeonfb mode-option=1400x1050-16@60,fbcon"
DEBUG: lLOAD_CMDL_MODULES_CLEAN: radeonfb fbcon
DEBUG: ALL_GIVEN_CMDL_MODULE:"radeonfb fbcon"
ERROR while runing framebuffer_hook
        Please look in /var/log/generate_framebuffer-initrd.log

```

Looking in /var/log/generate_framebuffer-initrd.log I get:
```

ERROR: radeonfb is not enabled in /boot/config-2.6.17-10-generic
        maybe the config file is missing

```
I don't understand this error. Do you have any idea where I could look, in order to test this with the radeonfb?
Thanks.

PD: Sorry for my rusty english.

---

### Post by evermind on 2006-11-14
> **reacuna said:**
> Hi,
I've been trying to use the radeonfb with your script, but when generating the initrd.img, I get the following output:

```

DEBUG: MODULESDIR /lib/modules/2.6.17-10-generic
DEBUG: FB_MODULES_WITH_PARAMETERS:"radeonfb mode-option=1400x1050-16@60"
DEBUG: LOAD_CMDL_MODULES_REVERSED:"radeonfb mode-option=1400x1050-16@60,fbcon"
DEBUG: lLOAD_CMDL_MODULES_CLEAN: radeonfb fbcon
DEBUG: ALL_GIVEN_CMDL_MODULE:"radeonfb fbcon"
ERROR while runing framebuffer_hook
        Please look in /var/log/generate_framebuffer-initrd.log

```

Looking in /var/log/generate_framebuffer-initrd.log I get:
```

ERROR: radeonfb is not enabled in /boot/config-2.6.17-10-generic
        maybe the config file is missing

```
I don't understand this error. Do you have any idea where I could look, in order to test this with the radeonfb?
Thanks.

PD: Sorry for my rusty english.

could you do the same as I suggested in the post above yours?

additional you could check if the file
exists /boot/config-2.6.17-10-generic
and also what if the modul radeonfb exists
modinfo radeonfb

I'll try to do a new release next weekend

---

### Post by reacuna on 2006-11-14
Attached to this post is the output (or lack-of-output :P) of
```

dpkg-reconfigure linux-image-`uname -r` &>initrd_logfile.txt

```

Both the config file and the module exists. /boot/config-2.6.17-10-generic is part of the linux-image-2.6.17-10-generic package.

---

### Post by evermind on 2006-11-15
here a quick fix (not tested) if you want to try
EDIT: removed --> new release --> first post

---

### Post by reacuna on 2006-11-15
Hi, I've tested it (on an Acer Ferrari 4005WLMi), but there is a known problem on this notebook with usplash ([Bug #63558]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/63558")). I've disabled it in the kernel parameters, but the console still is corrupted after the boot. I used to pass the parameter vga=794 (or vga=791) as a workaround, but this no longer works with the actual configuration. I don't fully understand how all of this works, so I'm not really sure how to proceed (in the testing or whatever).
My guess is that there is a problem with the framebuffer devices on this particular model of notebook. I can do more test if you want, but tell me where should I start.

---

### Post by evermind on 2006-11-15
> **reacuna said:**
> Hi, I've tested it (on an Acer Ferrari 4005WLMi), but there is a known problem on this notebook with usplash ([Bug #63558]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/63558")). I've disabled it in the kernel parameters, but the console still is corrupted after the boot. I used to pass the parameter vga=794 (or vga=791) as a workaround, but this no longer works with the actual configuration. I don't fully understand how all of this works, so I'm not really sure how to proceed (in the testing or whatever).
My guess is that there is a problem with the framebuffer devices on this particular model of notebook. I can do more test if you want, but tell me where should I start.
you mean before using this package here. you got a high resolution framebuffer with vga=791/794 in the kernel paramter line?

set
VESAFB=1
and a resolution that is yet supported within this script
in /etc/framebuffer.conf

for working resolutions look here
/usr/share/doc/framebuffer-initramfs/README.gz or at the first post

---

### Post by u-foka on 2006-11-15
Hmm it's work fine now for me :) but i still heve the problem with the tty consoles on my lcd's native resolution 1280x854 :S

---

### Post by reacuna on 2006-11-17
> **evermind said:**
> you mean before using this package here. you got a high resolution framebuffer with vga=791/794 in the kernel paramter line?
Yes, but that uses vesafb isn't it? I'm trying to use the radeon frambuffer in order to get the monitor's native resolution (1680x1050 if that is supported) or the non-widescreen resolution (1400x1050), which are not supported by vesafb.

---

### Post by evermind on 2006-11-17
> **reacuna said:**
> Yes, but that uses vesafb isn't it? I'm trying to use the radeon frambuffer in order to get the monitor's native resolution (1680x1050 if that is supported) or the non-widescreen resolution (1400x1050), which are not supported by vesafb.

yes that's right.

I'm on my way installing ubuntu on a testbox with a radeon vga...

---

### Post by evermind on 2006-11-21
> **evermind said:**
> yes that's right.

I'm on my way installing ubuntu on a testbox with a radeon vga...

I've done a new release: It changes detection and error-handling of fbmoduls

NOTE: I've tested the script with a radeon card and I had to set
DEPTH to 8 to see the splash in non garbled form.
(the colors could not be displayed properly)

---

