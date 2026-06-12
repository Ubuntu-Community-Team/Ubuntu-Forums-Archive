---
title: "HOWTO: Convert a syslinux.cfg file to menu.lst"
date: 2008-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Belak on 2008-04-19
In my recent attempts to make the ultimate USB recovery drive, I ran across a new version of the gParted live cd which changed from using a Grub bootloader to Syslinux. I was running SuperGrubDisk on my USB key already, and I didn't want to have to make a new partition for gParted, so I used the current one and converted the Syslinux config file to a Grub config file.

Steps:
[LIST]
[*]Open syslinux.cfg file
[*]Convert the Syslinux entry to a Grub one
[/LIST]

Step 1
Find your syslinux file and open it. It's usually either located in the root directory of the Live CD, or in a separate folder called syslinux.
Before we get onto anything else, let's take a minute to learn how the syslinux config file stores it's commands.

Here is an example of one entry (From the gParted Live CD)
```
label GParted Live
  MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Default settings)
  # MENU PASSWD
  kernel /live/vmlinuz1
  append initrd=/live/initrd1.img boot=live  username=casper   noswap vga=788 ip=frommedia
  TEXT HELP
  * GParted live version: 0.3.6-7. Live version maintainer: Steven Shiau
  * Disclaimer: GParted live comes with ABSOLUTE NO WARRANTY
  ENDTEXT
```

The part after label just shows what will be displayed as the menu entry.
The MENU DEFAULT tells us that this is the default entry.
The MENU LABEL tells us what we need to put into the command line version of syslinux to get this option to boot. (Correct me if I'm wrong)
The kernel and append lines are the important lines. They actually do the booting. They are what we are going to need.
All the text in the TEXT HELP isn't needed, so we'll leave it.

Step 2
Now, I said that the important lines were
```
  kernel /live/vmlinuz1
  append initrd=/live/initrd1.img boot=live  username=casper   noswap vga=788 ip=frommedia
```
Those are what we will need.

The following is a sample grub entry:
```
title		Ubuntu 7.10, kernel 2.6.22-14
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c552af7-35a5-4647-9648-3cbcc79d2eab ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
```

So, to convert our syslinux entry into a grub entry, we need to make out base entry (the hd1,0 may be different for you):
```
title gParted
root (hd1,0)
```

This entry will not do anything. It just sets the root at a certain hd, so we need to add the kernel file (/live/vmlinuz1 in this case) and pass it the parameters.
```
title gParted
root (hd1,0)
kernel /live/vmlinuz1
```

Ok, so we have the kernel, but what about the append line? We need to take everything after the initrd=/live/initrd1.img and add it to the kernel
```
title gParted
root (hd1,0)
kernel /live/vmlinuz1 boot=live  username=casper   noswap vga=788 ip=frommedia
```

Ok, now for the last part, and one of the easier ones: the initrd part.
All you have to do is change the initrd= into an initrd then a space.
So, for the final result:
```
title gParted
root (hd1,0)
kernel /live/vmlinuz1 boot=live  username=casper   noswap vga=788 ip=frommedia
initrd /live/initrd1.img
```

Cheers,
Belak

---

### Post by ChronoSphere on 2008-04-25
I've been looking for something along these lines. Thanks for posting this info.

---

### Post by Belak on 2008-04-25
Glad I could help.

:)

---

### Post by love2learn on 2008-05-18
totally lost me on this part....

I am following your other guide

[http://ubuntuforums.org/showthread.php?t=759935&highlight=bt3+usb](http://ubuntuforums.org/showthread.php?t=759935&highlight=bt3+usb)

and when you make a reference over to this guide i am totally lost. I get that we are trying to modify the grub file to look like the syslinux.cfg file but what grub file should we be modifying?  ( or am i totally lost? )

Thanks

---

### Post by Belak on 2008-05-18
It sounds like you have it backwords.

We're taking a syslinux config file (Syslinux.cfg or isolinux.cfg) and converting it to a Grub config file (Ususlly at /boot/grub/menu.lst, or anywhere like this but on a different drive)

I don't know if that helps or not...

---

### Post by love2learn on 2008-05-18
yes, that helps a bunch. I felt the rest of the questions i have are better asked in your other thread. Thanks!

---

### Post by flyboy612 on 2008-10-14
When I use the liveusb-creator make the Fedora 9 on my usb drive,and I want to change the syslinux.cfg to menu.lst,but it does not work .so who can help me?

The syslinux folder file list:
boot.cat
initrd0.img
isolinux.bin
memtest
splash.jpg
vesamenu.c32
vmlinuz0
syslinux.cfg

and the LiveOS folder file list:
livecd-iso-to-disk
osmin.img
squashfs.img
overlay-COFFEE-1C0D-BF44

The content of syslinux.cfg:

default vesamenu.c32
timeout 100

menu background splash.jpg
menu title Welcome to Fedora-9-Live-i686!
menu color border 0 #ffffffff #00000000
menu color sel 7 #ffffffff #ff000000
menu color title 0 #ffffffff #00000000
menu color tabmsg 0 #ffffffff #00000000
menu color unsel 0 #ffffffff #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000
menu hidden
menu hiddenrow 5
label linux0
  menu label Boot
  kernel vmlinuz0
  append initrd=initrd0.img root=UUID=1C0D-BF44 rootfstype=vfat rw quiet liveimg overlay=UUID=1C0D-BF44 rhgb 
menu default
label check0
  menu label Verify and Boot
  kernel vmlinuz0
  append initrd=initrd0.img root=UUID=1C0D-BF44 rootfstype=vfat rw quiet liveimg overlay=UUID=1C0D-BF44 rhgb check
label memtest
  menu label Memory Test
  kernel memtest
label local
  menu label Boot from local drive
  localboot 0xffff

---

### Post by Belak on 2008-10-28
Ok, are you using liveusb-creator on Windows or Linux?
It should do everything for you... but I'm not sure... I've never used it...

-Belak

---

