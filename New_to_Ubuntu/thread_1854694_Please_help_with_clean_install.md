---
title: "Please help with clean install"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by jrschrock on 2011-10-04
I would like to do a clean install because my system has become unstable. I have done a lot of reading and have attempted to do this on my own, to no avail.

I don't have a CD drive, so can't use the live CD.

I've tried to boot through USB flash drive but have not been successful- can't figure out how to mount the drive. I downloaded 11.10 from another machine, extracted the files to the flash drive, then selected to boot through the USB, but it ends up booting regularly. 

I've also tried going the unetbootin route, but simply can't figure out how to do it successfully.

I really don't know what to do next, and I would greatly appreciate any help! Thanks in advance!

---

### Post by drs305 on 2011-10-04
If you currently have a working Grub 2, and you can get the ISO file onto your main drive, you can install Ubuntu from the ISO *file*.

Here are the instructions. They are a bit convoluted but you can ask if you have questions. The instructions are designed for a user stuck at the grub rescue prompt, so there are some commands you wouldn't need, but it will work regardless:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by Ozitraveller on 2011-10-04
[http://www.mytechguide.org/7818/create-linux-live-bootable-usb-stick-using-unetbootin/](http://www.mytechguide.org/7818/create-linux-live-bootable-usb-stick-using-unetbootin/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by jrschrock on 2011-10-05
Don't have working GRUB2, or if I do, I don't know how to run it (or what it is for that matter). 

The root of my problem is that I can't do a thing with my USB drive. I've never been able to mount a flash drive, so unless I'm missing something, it is impossible for me to create a bootable USB stick. 

I don't know what to do. Is it possible to just completely erase the Ubuntu installation I have and start over. Maybe once the unstable system is gone, the USB booting route will be successful?

If I don't fix this, I'm guessing I pretty much have a useless machine on my hands that was working fine when I ran Windows 7 on it. At my wit's end. 

And yes, I've tried the unetbootin thing and just run into USB problems, so.... I should add that I tried the 'hard disk' option, since USB drive not recognized, then when I rebooted, there was no unetbootin option, as stated by the sourceforge guide.

Anyways, thanks for the responses.

---

### Post by meatytaco on 2011-10-05
If you have another computer to work from, download the Linux Live USB Creator. you will need an .iso image of the distro you want to use. This program will allow you to either use your linux off the flash drive as a live linux, or install it off the flash drive. This is how I got mine to work. Hope this helps :)

[http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

---

### Post by meatytaco on 2011-10-05
Also, if your comp will not boot off the flash drive, try disabling all other boot mediums in your BIOS. (Hard drive, CD Rom, etc.)

---

### Post by mastablasta on 2011-10-05
i second LinuxLiveUSB. it is much more user friendly.
 
> **meatytaco said:**
> Also, if your comp will not boot off the flash drive, try disabling all other boot mediums in your BIOS. (Hard drive, CD Rom, etc.)
 
 
or you can boot from floppy disk (if you have one and driver for it) using PLOP boot manager.

---

