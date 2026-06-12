---
title: "bootable USB isn't bootable"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by silverwing39 on 2013-03-14
I've followed the instructions on the Ubuntu website and used the Pendrive software to create a bootable 12.04LTS USB stick but when I try to boot from it my PC says "missing operating system" and continues right into windows. I've tried this on both an ACER netbook and a Dell D630. Both say the say thing. Both appear to recognize the USB drive in the BIOS. I've hit F12 for the one time boot menu and chosen the flash drive but still both PCs say "missing OS". I've also tried the LinuxLive USB creator software and i get the same thing. What am i doing wrong?

---

### Post by Vaspro on 2013-03-15
I think some file is correpted in your usb stick try to fix it and try

---

### Post by mörgæs on 2013-03-15
> **Vaspro said:**
> I think some file is correpted in your usb stick try to fix it and try

Unlikely, as the USB has been re-built with both Pendrive and LinuxLive USB creator.

Is the USB stick completely clean without built-in software? The U3 drives were infamous for this, for example.

---

### Post by silverwing39 on 2013-03-15
Yes I'm quite sure any built in software has been removed from the drive as it was already a bootable Linux drive when it was given to me (different distro) which i wiped out and used for storage for a while before trying to do this. It's an 8GB Kingston DT101. So far I've only tried Ubuntu, none of the others. I saw in another thread that someone with the same problem was told to try typing  sudo syslinux -sf /dev/your_device.  I've tried looking in the /dev folder of my PC but i can't identify the "your_device" that would be the flashdrive. When i stick the USB drive into my PC it shows up as PENDRIVE so I found it in /media/PENDRIVE. I tried doing the sudo syslinx command again but it just gave me an error saying "this is a directory" or something like that. I have looked in the /boot folder of my Dell which is currently running Ubuntu 12.04LTS and found lots of stuff in there. I looked in the /boot/grub folder of the USB drive and found only one file loopback.cfg. I'm wondering if that could be the problem. I'm still a Linux noob but I've been dealing with Windows and PCs long enough to think that this folder is surprisingly empty.

---

### Post by fantab on 2013-03-15
Looks to me like a bad burn. What software did you use to burn ubuntu.iso to the USB? from what OS?

This may seem a bit far fetched but recently I had this issue where I could not successfully burn .iso to the USB... [FIXPARTS]("http://www.rodsbooks.com/fixparts/") solved it for me. It just turned out to be mixed up partition table on USB. 
Reformat the USB, preferably from Windows PC and try again.

---

### Post by ibjsb4 on 2013-03-15
Last time I got into this subject it turned out that using a different flash drive solved the problem, even though it checked out good.

You could also try [UnetBootin]("http://unetbootin.sourceforge.net/"), see if it yields any better results.

---

### Post by tea for one on 2013-03-15
> **silverwing39 said:**
> I've followed the instructions on the Ubuntu website and used the Pendrive software to create a bootable 12.04LTS USB stick but when I try to boot from it my PC says "missing operating system" and continues right into windows. I've tried this on both an ACER netbook and a Dell D630. Both say the say thing. Both appear to recognize the USB drive in the BIOS. I've hit F12 for the one time boot menu and chosen the flash drive but still both PCs say "missing OS". I've also tried the LinuxLive USB creator software and i get the same thing. What am i doing wrong?

Good Afternoon

When you mentioned that you used "Pendrive software", are you referring to Start Up Disk Creator in your Ubuntu 12.04 OS on your Dell PC?

---

### Post by schragge on 2013-03-15
On my computer, bootable USBs made with UNetbootin work on USB 2.0 ports, but don't on USB 3.0.

---

### Post by nicraz on 2013-03-15
Not sure if this will help, but the first time I tried installing with a bootable USB stick I had the same error message. It turns out my download was corrupt, I downloaded Ubuntu 12.10 again, used the Pendrive to make it bootable, and then it worked.

---

