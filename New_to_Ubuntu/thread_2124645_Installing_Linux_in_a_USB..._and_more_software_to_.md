---
title: "Installing Linux in a USB... and more software to BOOT from USB"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by Tuexnovia on 2013-03-11
Hi guys I feel like I'd like to put in my USB of 16Gb, several thing to be bottable... "I've seen so many spftware that I get already crazy."

1. Well I'd like to put lubuntu to be bootable from a usb "To boot the system without having to install it, but be able to touch everything" and besides make it able to install it in the hard drive if I want it.

2. More difficult, I'd like to put my original copy of windows 7 to make it bootable just to install it...

3. I'd like to install third software which is an ISO with several programs to use... "you know what I mean xDD"


Is there any program that let you do all that?

---

### Post by Cheesemill on 2013-03-11
Take a look at [Yumi]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/"). I'm not sure if it can boot the Windows installer but it will let you have several Linux distro's on the same USB.

---

### Post by Tuexnovia on 2013-03-11
Well yes it tells you: 
1- Windows Vista/7/8 Installer...         YEAAA...
2- The other software I can put it too YEAAA...
> 3-Most important I need a bootable O.S lubuntu to boot the system without having to install it, but be able to touch  everything" and besides make it able to install it in the hard drive if I  want it.

so is for my last question!!! this option in YUMI...

**Try an Unlisted ISO (Run from RAM)** "can I install the iso from here? to do what I want"

---

### Post by Cheesemill on 2013-03-11
Any of the Linux distro's that you put on your USB with Yumi run exactly the same as if you were using the CD so yes, they will be installable.

---

### Post by C.S.Cameron on 2013-03-11
Windows 7 - Using Gparted, (from Live CD), format flash drive NTFS, set boot flag.
Using Archive Manager extract Win 7 iso to flash drive.

---

### Post by Tuexnovia on 2013-03-11
> **Cheesemill said:**
> Any of the Linux distro's that you put on your USB with Yumi run exactly the same as if you were using the CD so yes, they will be installable.

ok perfect now do you know if there is any option to get always that "USB" updated and with my software already installed I mean firefox VLC, and save settings... or you can't just do that?

---

### Post by C.S.Cameron on 2013-03-11
> **Tuexnovia said:**
> ok perfect now do you know if there is any option to get always that "USB" updated and with my software already installed I mean firefox VLC, and save settings... or you can't just do that?

A persistent install with casper-rw file has maximum 4GB persistence.
This will quickly fill if using update manager, then the drive will not boot.

One option is to use persistent partitions.

Another option is to do a Full install, however you can not use a Full install to install Ubuntu.

---

### Post by Impavidus on 2013-03-11
You can also install Ubuntu on your USB. It will no longer run as live session or run the installer, but you can still take it to whatever computer you want (provided the hardware is similar to the one on which you installed) and you won't have to change anything on the hard disk.

---

### Post by Tuexnovia on 2013-03-11
> **Impavidus said:**
> You can also install Ubuntu on your USB. It will no longer run as live session or run the installer, but you can still take it to whatever computer you want (provided the hardware is similar to the one on which you installed) and you won't have to change anything on the hard disk.

Ok nice idea, and then if I got 16gb I'd say that is more than enough...


Going back to a little problem that it just appears.

I've downloaded a version of lubuntu and I wanted UBUNTU...

Well in the folder of my USB F:\multiboot\ISOS There are my distros of LINUX. well I've deleted one of them and put another with different name...

Before.

lubuntu-12.10-desktop-i386
**lubuntu-12.10-desktop-amd64**

NOW

lubuntu-12.10-desktop-i386
**ubuntu-12.10-desktop-amd64** (Ubuntu instead of Lubuntu)


Well I've change in this files the name of the new .ISO and I saved it, but it doesn't work then it says if I try to BOOT that .ISO

Error 15:File not found

> 
menu.lst


# Modify the following entry if it does not boot
title Boot **ubuntu-12.10-desktop-amd64.iso**
find --set-root --ignore-floppies --ignore-cd /multiboot/ISOS/lubuntu-12.10-desktop-amd64.iso
map --heads=0 --sectors-per-track=0 /multiboot/ISOS/**ubuntu-12.10-desktop-amd64.iso** (hd32)
map --hook
chainloader (hd32)


Well before was working but when I deleted it, and then put another one even changing the name doesn't work... (I want to sort it out I don't wanna have tu install everything again...)
Any idea?

---

### Post by Tuexnovia on 2013-03-11
OK I've added a new ISO doing exactly the same but this time I add the hole LINE I mean...

> 
# Modify the following entry if it does not boot
title Boot lubuntu-12.10-desktop-i386.iso
find --set-root --ignore-floppies --ignore-cd /multiboot/ISOS/lubuntu-12.10-desktop-i386.iso
map --heads=0 --sectors-per-track=0 /multiboot/ISOS/lubuntu-12.10-desktop-i386.iso (hd32)
map --hook
chainloader (hd32)


# Modify the following entry if it does not boot
title Boot ubuntu-12.10-desktop-amd64.iso
find --set-root --ignore-floppies --ignore-cd /multiboot/ISOS/lubuntu-12.10-desktop-amd64.iso
map --heads=0 --sectors-per-track=0 /multiboot/ISOS/ubuntu-12.10-desktop-amd64.iso (hd32)
map --hook
chainloader (hd32)


# Modify the following entry if it does not boot
title Boot lubuntu-12.10-desktop-amd64.iso
find --set-root --ignore-floppies --ignore-cd /multiboot/ISOS/lubuntu-12.10-desktop-amd64.iso
map --heads=0 --sectors-per-track=0 /multiboot/ISOS/ubuntu-12.10-desktop-amd64.iso (hd32)
map --hook
chainloader (hd32)

and all of them are working... I don't really understand why...

---

### Post by Tuexnovia on 2013-03-12
> **Impavidus said:**
> You can also install Ubuntu on your USB. It will no longer run as live session or run the installer, but you can still take it to whatever computer you want (provided the hardware is similar to the one on which you installed) and you won't have to change anything on the hard disk.

Linux live USB creator does what I wanted... it makes if you got 16 GB you O.S and you can take it wherever you want. that is what I want.  That would be amazing xDD with just few programs...

---

