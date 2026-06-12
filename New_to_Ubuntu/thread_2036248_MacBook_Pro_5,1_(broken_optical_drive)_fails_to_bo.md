---
title: "MacBook Pro 5,1 (broken optical drive) fails to boot from USB"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by samoos on 2012-08-01
I have a MacBook Pro 5,1 and I am trying to install Ubuntu 11.04 Natty (or, in fact, any Linux distro at all)

I haven't done any kind of partitioning, I don't want to use MacOS any  more, so a single boot Ubuntu or multi-boot with different Linux distros  is basically what I'm after.

I used UNetbootin to transfer an .img to a FAT 32 usb drive, but it failed to boot.

I followed the ubuntu '[create a USB stick on Mac OS X]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx")' thread - when trying to boot from the usb drive, it did not show up.

[This technique]("http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/") (using iso-2-usb efi-booter for mac 0.01) got me closer, I got a message with 'loading Linux, loading RAM, fasten your seatbelts while we load the kernel'. it then froze. 

I repeated the technique using different .isos - one was [a method using a minimal CD download]("http://www.joop.in/Archive/multibooting-osx-lion-ubuntu-linux-on-macbook-41-without-cd/"), it got me to grub, but I didn't know how to progress further, and my much-more-linux-literate friend who was helping me was unable to improve the situation.
I've tried with a 1386.iso, and fedora too, but still no luck.

any suggestions?

---

### Post by levlaz on 2012-08-01
Lets start from the beginning. 

Your computer is more than capable of running the latest version of ubuntu so download the .iso  and use [unetbootin]("http://unetbootin.sourceforge.net/") to create the live USB. 

When you are rebooting hold down C 

Select the USB to boot from and tell me what happens then.

---

### Post by samoos on 2012-08-02
p, li { white-space: pre-wrap; }  Once UNetBootin has created the USB, I get the following:
"The created USB device will not boot off a Mac. Insert it into a PC, and select the USB boot option in the BIOS boot menu."

I hold down C, it comes to the refit page, select 'boot linux from USB'.
The screen goes black, then I get a message 'Boot Error_"

---

### Post by samoos on 2012-08-02
the other option at the rEFIt page is boot from efi/boot.

This gets me a screen with three options:
-Try Ubuntu without installing
-Install Ubuntu
-Check disk for errors

All of these result in black screens.

---

