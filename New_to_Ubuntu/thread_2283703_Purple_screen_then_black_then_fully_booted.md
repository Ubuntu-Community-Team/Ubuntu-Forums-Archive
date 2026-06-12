---
title: "Purple screen then black then fully booted"
date: 2015-06-23
forum: New to Ubuntu
---

### Post by bublz2 on 2015-06-23
Hello there :) 
I have a minor problem. Whenever I boot up Ubuntu it goes to a purple screen then a black screen then it boots into the desktop. 
I don't that happening but I would like to see a splash screen instead of random screens :P
How can I fix this problem? 

Ubuntu: 14.04
Laptop: company precarious CQ57
Graphics card: AMD 
Installed Ubuntu: 22/6/15

---

### Post by grahammechanical on 2015-06-23
You will get used to it.

It is all part of the way Linux works. We start with a boot loader that is using a motherboard default video mode. Then as Linux begins to load the Xserver takes over and loads a video driver and usually a splash screen by some software called Plymouth. At some point Linux has fully loaded and Ubuntu needs to login to Linux in our name. By the time we get to the login screen Light Display Manager has taken over and then after logging in everything switches to the desktop environment and the user interface, which are managed by the Compiz compositor/window manager.

There is a lot of switching going on. And things will remain that way until Ubuntu replaces Xserver, LightDM and Compiz (and for all I know Plymouth) with Ubuntu's very own Mir compositor. Fingers crossed - by this time next year. Or later.

Regards.

---

### Post by bublz2 on 2015-06-24
> **grahammechanical said:**
> You will get used to it.

It is all part of the way Linux works. We start with a boot loader that is using a motherboard default video mode. Then as Linux begins to load the Xserver takes over and loads a video driver and usually a splash screen by some software called Plymouth. At some point Linux has fully loaded and Ubuntu needs to login to Linux in our name. By the time we get to the login screen Light Display Manager has taken over and then after logging in everything switches to the desktop environment and the user interface, which are managed by the Compiz compositor/window manager.

There is a lot of switching going on. And things will remain that way until Ubuntu replaces Xserver, LightDM and Compiz (and for all I know Plymouth) with Ubuntu's very own Mir compositor. Fingers crossed - by this time next year. Or later.

Regards. 

Ah right ok. Thanks for the very detailed information  :) so it's not possible to get the splash screen working?

---

### Post by rlovi on 2015-07-01
> **bublz2 said:**
> Ah right ok. Thanks for the very detailed information  :) so it's not possible to get the splash screen working?

The following worked for me using Ubuntu Studio 14.04. First edit /etc/default/grub:

```
sudo gedit /etc/default/grub

```

add the line:

```
GRUB_GFXPAYLOAD_LINUX=auto
```

so it looks like this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]GRUB_GFXPAYLOAD_LINUX=auto[/COLOR]

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Save the file and reboot.

Richard

---

