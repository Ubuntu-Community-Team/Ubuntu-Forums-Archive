---
title: "Trouble with the First-Time Installation of Ubuntu 14.02 Live"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by potatos2 on 2016-03-06
Hello, as you can probably tell from where I am posting this thread, I  am new to Ubuntu and Linux in general. About a month ago I decided that I  wanted to give Linux a try and now I am wanting to completely switch to  using just Ubuntu Linux. I have yet to fully install Ubuntu on my  computer (have been running it off my USB drive) and there are some  clear disadvantages to using it like that. However, as of late, I can't  even run Linux in preview mode let alone install it. I tried installing  it from while inside the OS a few days ago, but had to stop because I  didn't have the time to finish installing it. Cancelled the installation  and turned off my computer. When I went back on to try and install it  again, instead of booting into Ubuntu from the dual boot, my computer  went to a mostly black blank screen with this text [ATTACH=CONFIG]267684[/ATTACH] displayed in the top  right corner.

I'm using a HP Envy 15 x360 laptop currently running Windows 10 with an Intel Core i5-4210U processor. Any help with this so that I can be transported into the world of Linux will be much appreciated. Thanks :)

---

### Post by grahammechanical on 2016-03-06
Re-burn the ISO image to the USB memory stick. Shutting down the installation process most likely corrupted the USB stick or did some damage. It will happen if we do not correctly eject a USB stick, also.

 There is no point trying to fix a broken live session. Just re-burn the ISO image..

Regards.

---

### Post by potatos2 on 2016-03-06
I tried doing that already with UNetBootin. Still hasn't worked.

---

### Post by sammiev on 2016-03-06
Looks much like what I see when using UNetBootin.

Likely try another burner program for the OS you are installing from.

---

### Post by potatos2 on 2016-03-06
Do you have any others that you could recommend? All I'm finding is UNetBootin.

---

### Post by mastablasta on 2016-03-07
Pendrivelinux, Yumi, LinuxLiveUSB...

---

### Post by HermanAB on 2016-03-07
Uhmmm... You should not need to use unetbootin.  For the last couple years or so, the Ubuntu live ISOs are hybrid files that can be directly written to a USB stick.  Also, don't use an old version, since it may not support your hardware properly.  The latest version of Ubuntu is 15.10.

---

### Post by him610 on 2016-03-07
For what it is worth...
In the past, I have encountered issues with burning a DVD on one system followed by attempting to boot, or read from another system, then on other systems the disk may actually be read. I have no explanation other than possibly some minor differences in the write/read characteristics of the different devices.

---

### Post by Bucky Ball on 2016-03-07
No one seems to have mentioned this, or I have missed it, so I'll throw it in. 14.04.2 is an older point release. We are now at 14.04.4

Try[ downloading from here ]("http://www.ubuntu.com/download/desktop")and use 14.04.4 and save yourself some updating/upgrading when you eventually get this installed which may cause other issues.

UNetbootin works fine (at least I've never had an issue with it). Format the USB to one FAT32 partition that uses the whole stick. Do the UNetbootin thing. Leave the stick plugged in and reboot to the BIOS and set the machine to boot from the USB stick.

Most machines have a boot device menu you can use at boot. Common is hitting F12 at boot to get to it, then choose the USB. Your key to get there may be different.

If that doesn't work, by all means, try something else (Universal USB Installer perhaps?), but if the UNetbootin version isn't working I can only think of user or hardware error.

---

### Post by potatos2 on 2016-03-13
Thank you all for the help. I got it working now by using some of your advice. I am using Ubuntu  15.10 now. I have another problem that I have since encountered, but I am trying to figure out how to fix it using Google before I ask for help on here.

---

### Post by Bucky Ball on 2016-03-13
All good. Feel free to post a new thread when your research hits a dead end.

Please see the first link in my signature and mark thread as solved. Enjoy the ride.

---

