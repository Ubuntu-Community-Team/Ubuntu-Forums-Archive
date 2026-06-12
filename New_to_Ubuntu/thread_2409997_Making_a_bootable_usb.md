---
title: "Making a bootable usb"
date: 2019-01-09
forum: New to Ubuntu
---

### Post by redpoppet on 2019-01-09
Hi everybody,
I have been trying out a few distros but have made ubuntu 18.04 my "home" so to speak using a spare laptop to trial different flavours.  One thing that I have had trouble doing within ubuntu is making a bootable usb off other distros.  The tool that comes with ubuntu 'start up disc creator' will make a bootable disc only for certain things.  For example, (and I am sure most of you know this) it won't make a bootable usb for Fedora or SUSE.  I tried to use UNetbootin but it won't run on my ubuntu for some reason.  I did manage to make some bootable usbs with the app within pop but I was wondering if anybody can point me to an app that I can use within ubuntu that will make bootable usbs for me that the onboard 'start up disc creator' won't.  It would be great to have a tool within ubuntu that does this.

I have done a pretty good search around but I can't seem to find anything that fits this bill.

A big thank you ahead of time to anybody who can assist her.

---

### Post by yancek on 2019-01-09
I'm not sure why you would have trouble running unetbootin on Ubuntu.  I've never had any problems with it.  Did you download the correct version for LInux?  Most newer iso files are hybrid so you should be able to simply use the dd command to write to the usb.  Take a look at the link below which has a pretty detailed explanation on its use.

 [https://medium.com/@tbeach/use-unix-dd-command-to-os-bootable-on-usb-drive-6671945d95a6](https://medium.com/@tbeach/use-unix-dd-command-to-os-bootable-on-usb-drive-6671945d95a6)

---

### Post by redpoppet on 2019-01-09
Thanks for the reply.  I downloaded UNetbootin from the Ubuntu store icon from within ubuntu.  Not only does it not work on my main pc I couldn't get it to work on my 'experimental' laptop either.  The program will launch but I get a blank window.  I don't know if its the laptops which are both Dells E6530 & 6430.  I also have problems running some other distros on these Dells as well.  For example they don't like Fedora for some reason.  Maybe its the hardware.  But either way, the problem with UNetbootin is one of the reasons that I was looking for another way to make a bootable usb.

---

### Post by CatKiller on 2019-01-09
[Etcher](https://www.balena.io/etcher/) is painless. It's not in the repository, you need to download a .deb file from [their website](https://github.com/balena-io/etcher/releases).

---

### Post by oldfred on 2019-01-09
Are these UEFI systems?
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) 
    
       Most find this works, but it uses dd under the hood:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by redpoppet on 2019-01-09
Ok, thanks heaps y'all.  I've got enough to keep me occupied and busy I think :)

Many thanks for the replies.

---

### Post by oldrocker99 on 2019-01-09
One thing: When you're burning a bootable USB, format it in DOS mode first, or it won't boot.

---

### Post by C.S.Cameron on 2019-01-10
UNetbootin, (Linux), does not work on 18.04 out of the box. 
There are workarounds, but it is simpler to use MultiBootUSB, (Linux version).
It will make a bootable USB with options for hundreds of Linux OS.
[http://multibootusb.org/](http://multibootusb.org/)

---

### Post by redpoppet on 2019-01-10
Ah, interesting info about UNetbootin.  I couldn't work out why and I didn't really care provided I found something else.  Thanks for the tip!

---

### Post by oldrocker99 on 2019-01-10
Etcher is indeed a superior USB-burning program. Hopefully, it'll be in the repos soon.

---

