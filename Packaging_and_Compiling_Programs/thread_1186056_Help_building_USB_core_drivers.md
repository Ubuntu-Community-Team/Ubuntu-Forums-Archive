---
title: "Help building USB core drivers"
date: 2009-06-13
forum: Packaging and Compiling Programs
---

### Post by PaganImmolator on 2009-06-13
I hope you can help me(is this the right forum?). I am trying to get my wifes Itouch working under VirtualBox and apparently one of the methods to get this to work is to rebuild the USB core drivers to be more compatible with what the Itouch expects. 

I am following the method in this thread: 

[http://ubuntuforums.org/showthread.php?t=970628]("http://ubuntuforums.org/showthread.php?t=970628")

and this section is what is causing me problems

```
sudo apt-get build-dep linux-source-2.6.27
sudo apt-get install linux-source-2.6.27 build-essential
tar -jxvf /usr/src/linux-source-2.6.27.tar.bz2
cd linux-source-2.6.27/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
```

but when I get this error I don't know how to fix it: 
```
strip --strip-debug usbcore.ko
strip: 'usbcore.ko': No such file
```

While not a complete newbie, I still don't don't know a lot about Linux and compiling from source. From what I can tell, its looking for an object file. Did the naming conventions change or did something not get built right? 

Any help appreciated. 

I am using Jaunty AMD64 flavor.

This is the output of the directory /linux-source-2.6.28/drivers/usb/core 

```
buffer.c   devio.c.bak  generic.c  hub.c    Makefile        Module.symvers   sysfs.c
config.c   driver.c     hcd.c      hub.h    message.c       notify.c         urb.c
devices.c  endpoint.c   hcd.h      inode.c  Module.markers  otg_whitelist.h  usb.c
devio.c    file.c       hcd-pci.c  Kconfig  modules.order   quirks.c         usb.h
```

---

### Post by PaganImmolator on 2009-06-14
28 views and no responses. Am I posting to the wrong forum or is this really harder than it appears?

---

### Post by smoohta on 2009-06-19
Hi,
I've also had problems with my Iphone and Virtual Box, what fixed it for me though is not the usbcore rebuild (we'll get to that soon :)) but finding out that my user wasn't part pf the vboxusers group (which you should have added usbfs access to in your fstab - according to the guide you followed previously).
To check if that's your problem just go to System -> Users and Groups -> Unlock -> Manage Groups -> vboxusers -> and see who are the group members- after changing this (and restarting) my usb devices always worked in Virtual Box...
I wasn't happy with the usb devices speed so I figured I'd try the usbcore thingie, I ran into the same difficulties you did and after a whole lot of searching I think I figured it out- in the latest kernels usbcore doesn't seem to be built as a module- it's built as part of the kernel :)
What I did was follow some of the ubuntu kernel (not vanilla kernel!) rebuild guides ([http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way) ,[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) - be sure to copy your current kernel config!), manually changed the value in linux-source/drivers/usb/core/devio.c (from 16384 to 131072) and built the kernel.
As far as I can see it really is much more responsive (even though I didn't do any tests) but it could be just in my imagination :)

---

### Post by smoohta on 2009-06-19
Forgot to say- another key in getting my Iphone to work in Virtual Box was to disable gnome's auto-mounting:

1. I disabled automount entirely in Nautilus by using gconf-editor and unchecking app > nautilus > preferences > media_automount.
2.I made /home/root/usr/lib/gvfs/gvfs-gphoto2-volume-monitor be without execute permissions, I'm not sure if it's needed though...

Hope this works for you... :)

---

