---
title: "Installing Ubuntu from USB to HDD"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Pap3r on 2008-08-24
Using some tutorials, I eventually came across Syslinux, and formatted my USB drive, then installed syslinux onto it.  I copied the contents of an Ubuntu .iso, changed the isolinux.cfg to syslinux.cfg, and moved the proper files.  Syslinux worked like a charm!  It boots quickly and Ubuntu runs well.  My problem is not in setting up the USB though, it pertains to the installation of Ubuntu onto my harddrive, rather than the USB.

This is what I mean.  When I click install, the install only recognizes the USB drive.  That, originally, didn't seem like a big deal.  I attempted to mount my NTFS drive(WinXP) unsuccessfully, however.  After a few more attempts using different formats of /dev/sda1 etc, I checked what sudo fdisk -l had to say.

There's my problem!  The output of sudo fdisk -l shows that the only drive connected to the computer is the USB drive, therefore, I am unable to mount my hard drive on linux.  Every distro I have tried has had this problem (7.10, 8.04, LinuxMint).

My cd drive is broken (that or my motherboard's IDE controller) so I am unable to use it, which is why I'm finding it necessary to make this post.  I have no idea what to do.  Linux doesn't even recognize my HDD as connected to the computer at all...  

How does one mount that which "doesn't exist"?

---

### Post by zamadatix on 2008-08-24
dont know about your mounting but isnt there an easier way to make a live usb of ubuntu?

---

### Post by Pap3r on 2008-08-24
> **zamadatix said:**
> dont know about your mounting but isnt there an easier way to make a live usb of ubuntu?

That was really helpful, thanks a bunch!

---

### Post by nothingspecial on 2008-08-24
I have successfully installed Ubuntu on a laptop, with a broken cd/dvd drive, using a 4gig usb pendrive using this -

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by zamadatix on 2008-08-24
my laptop can only read like part of a cd (ther beggining) to a littl bit out before the cd drive fails (tried everything but replaceing it) so i was able to load gparted but i know ubuntu wont install (goes out to far) is there any way to get my laptop to boot from usb when it doesnt support that in bios? (wihtout using to much space on a cd obviously)

---

### Post by Pap3r on 2008-08-24
UNetbootin seems promising for my situation, though it does not work.

First of all, at one point I formatted my HDD to do a new build, and I ended up with two entries of Windows XP into the windows boot loader.  Only the first option works.  Unfortunately, without a Cd Drive, I am unable to remove the second option and restore windows booting back to how it was.

I think this may be why UNetbootin isn't working.  After I restart my computer and attempt to boot form USB, I get the error of ```
NTLDR is missing
``` or something similar.  I know that it is a required file for the Bootloader, if not the bootloader itself.  I'm not sure what the problem is.  Is it UNetbootin's fault?

---

