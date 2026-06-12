---
title: "No init found. Try passing init=bootarg"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by ownx0rz on 2012-02-07
I am running an Acer Aspire One D255 netbook. When I attempt to boot the computer, I receive a black screen with the message:
"No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13-31ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)"

I have searched many threads for the answer to this, but none of them are providing any fruitful solutions. I cannot boot up the Live CD. I am installing Ubuntu through a USB flash drive and I attempted to put 10.04 and 11.10 on it, but the black screen persists. It used to be that I could go through most of the Ubuntu install, but then it would become stuck during the installation. 

What are some solutions I could try to this?

Edit: I also have used different flash drives and different USB ports on the netbook. Moreover, being that it has no CD drive, I cannot actually make a true Live CD.

---

### Post by SuaSwe on 2012-02-07
Hi ownx0rz,

The internets suggest that running Gparted (see [this link]("http://forum.xbmc.org/showthread.php?t=80959")) or fsck (see [this one]("http://colorlessgem.blogspot.com/2011/04/no-init-found-try-passing-initbootarg.html")) - have you tried these?

---

### Post by Miljet on 2012-02-07
+ 1 for GParted. This error is often caused by improper shutdown or impending disk failure. If you are not making regular backups, it might be a good time to get in the habit of doing so.

---

### Post by ownx0rz on 2012-02-07
> **SuaSwe said:**
> Hi ownx0rz,

The internets suggest that running Gparted (see [this link]("http://forum.xbmc.org/showthread.php?t=80959")) or fsck (see [this one]("http://colorlessgem.blogspot.com/2011/04/no-init-found-try-passing-initbootarg.html")) - have you tried these?

hey SuaSwe, thanks for the suggestions. however, Gparted is not loading when I created a bootable flash drive with Unetbootin. it either goes to the black screen with the BusyBox message mentioned above and now when it starts I receive a message stating:
SYSLINUX 4.03 2010-10-22 EDD Copyright (c) 1994-2010, H. Peter Anvin et al
then nothing loads but a blinking cursor. this only occurs when the flash drive is in the computer. otherwise it gives the aforementioned error. thanks for your help.

---

### Post by SuaSwe on 2012-02-08
Do you get a BusyBox message also when attempting to boot into a LiveCD environment (e.g. when selecting 'Try Ubuntu')?

---

### Post by ownx0rz on 2012-02-08
no I do not. my computer managed to come to the screen where I could finally select the option to try Ubuntu, but it freezes when I touch any key or let the countdown itself run down. I cannot get gparted to boot and now it either displays the Peter Anvin et al message with a black screen afterward or the no init found screen.

---

### Post by SuaSwe on 2012-02-08
OK, now just talking from a past personal experience, but something like this happened to me when I tried to install a fairly new release onto a laptop that I suspect wasn't quite up to the task graphically. You say that you're using a netbook - are you trying to install a specific netbook release or just regular desktop? If the latter, do you have the facilities to burn a new LiveCD or create a LiveUSB with a distro release more suited to your hardware?

---

### Post by ownx0rz on 2012-02-08
I am attempting to install either the desktop version of 10.04 or 11.10. I have also attempted to install Jolicloud and if it randomly succeeds to boot, the computer still freezes if I hit any of the keys.

Edit: Any of the keys during the installation screen, like the Default, Try Jolicloud without installing type options.

---

### Post by ownx0rz on 2012-02-08
I have tried two different USBs as well as using Unetbootin and Pendrivelinux to attempt to install other distros, like Linux Mint. Are there any more suggestions?

---

### Post by Miljet on 2012-02-09
You might try creating a dedicated GParted Live CD. You can download the IOS from  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Miljet on 2012-02-09
You might try creating a dedicated GParted Live CD. You can download the ISO from  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

