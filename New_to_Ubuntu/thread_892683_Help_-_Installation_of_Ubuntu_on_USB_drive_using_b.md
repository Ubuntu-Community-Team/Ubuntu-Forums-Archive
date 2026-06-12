---
title: "Help - Installation of Ubuntu on USB drive using boot CD"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by djbloc on 2008-08-17
I would appreciate guidance to make a portable USB flash drive/stick with Ubuntu. I’ve spent the last few days reading a number of websites and wiki pages (help.ubuntu.com and pendrivelinux.com to name a few) and I’m confused. While they have given some ideas there are no tutorials that get me to my destination.

I would eventually like to end up with an 8GB USB drive that can:

-	Be used on different hardware/computers
-	Have a first partition of 5.5GB formatted as FAT32 
-	Have a second partition of 2.5GB formatted as encrypted EXT3 with Ubuntu 8 installed
-	For motherboards that support booting from USB - boot directly in Ubuntu on the second partition
-	For motherboards that do not support booting from USB - a CD that will boot the system from the second partition of the USB drive.

Clearly there are a number of steps to get there. The computer (Windows XP) I’m using does not support booting directly on USB and I’ve already created a number of bootable CDs that has not worked.

Any ideas are welcome.

Thanks

---

### Post by TJCIB on 2008-08-17
I have used this tutorial and it works

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)
It works directly from the LiveCD. And creates a persistent boot (saving changes you make)

The only modifications you would have to make are your specific partitioning requirements.  I believe there will then be three partitions, I think that tutorial asks you to make two partitions, not including your own FAT32.  You may want to follow the tutorial "as is", then use gparted or something to add your wanted partition in the end.

When you boot up, you will have a menu similar to when you boot from LiveCD.  It will have "Boot in Live (Persistent) Mode", "Boot in Safe Mode", "Memory Test", etc.  Only persistent mode saves your changes, but it should work with a good majority of hardware.

Booting from USB via a boot CD is a whole different topic.  Once you get the USB set up, that should be pretty straight forward.  I would take it one step at a time, testing on a system that boots from USB.

---

### Post by Amstell on 2008-08-17
Check this out.  Its an amazing little tool for installing anything to a USB drive.  It will even download the distro and extract it.  Works perfectly.  Enjoy

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Cheers

Amstell

---

### Post by SunnyRabbiera on 2008-08-17
practically Ubuntu can be installed on any type of hard drive that is over 4GB in size.
Linux has been compacted onto tiny USB hard drives before, look here:
[http://www.mandriva.com/en/product/mandriva-flash-2008-spring](http://www.mandriva.com/en/product/mandriva-flash-2008-spring)

---

### Post by TJCIB on 2008-08-17
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) looks very interesting.  I am going to mess around with it for sure.

Does it have the partitioning abilities that djbloc needs?  Does it use the normal ubuntu partitioning tool in the regular install?

What I like about the method on pendrivelinux is it shows you what you're doing, so you can control things a little more.  I guess I'm just not an "automatic" kind of guy.

DJ: be sure you tell us how it goes and what methods you use/try.

---

### Post by djbloc on 2008-08-18
Thanks for the prompt replies. I've got a few follow up questions if thats okay:

Unetbootin: Reading the Unetbootin website it seems it alters the boot loader. Is this the case? I do not want to change the boot settings of the machine I'm using to build the USB.

TJCIB: Unfortunately none of the machines I have access to can boot directly from USB so I need to be able to create a boot CD as well. I followed the paragraph "Booting the kernel from a bootable CD" from [https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB") but come across problems when trying to modify the configuration files as they are read only when mounting the live CD using the command ```
mount -t squashfs -o loop /cdrom/casper/filesystem.squashfs /media/livecd
``` I therefore skipped that section and copied the 'vmlinuz' from the live CD (I could not find 'initrd.img' on the live CD) and created a bootable CD. On booting it stops very quickly with a kernel panic stating it can not find the root drive. Any suggestions?

SunnyRabbiera: That Mandriva drive looks similar to what I'm looking for. However, I've recently brought the USB stick so I'm loathe to buy this drive. Are you aware if you can download it instead?

Thanks

---

### Post by TJCIB on 2008-08-18
using "fdisk -l", where is your USB driving showing up?  
I am asking because your mount locations look weird to me. It looks like you're trying to mount a file system from the LiveCD, not your USB
I believe the "system" that they refer to in that walkthrough is your USB System that you just installed.
Normally its something like 
```
mount [options] /dev/sda1 /media/livecd
```


try mounting with this
```
mount -t squashfs /*location_of_usb* /media/livecd -o uid=1000,gid=100,utf8,dmask=027,fmask=137
```
this way the root user (and group) that you are using under the LiveCD is given ownership.
I'm not a pro at troubleshooting, I'm just telling you what I would try.

P.S. - If you could find a computer that boots from USB, just to make sure that the stick is installed correctly, it may save you a lot of headaches.  But sometimes we have to play with the cards we're dealt.

---

### Post by TJCIB on 2008-08-18
I just realized you could leave off the "-t" option to let the operating system autodetect the file system type.

If you get an error, then do the specific type.

---

