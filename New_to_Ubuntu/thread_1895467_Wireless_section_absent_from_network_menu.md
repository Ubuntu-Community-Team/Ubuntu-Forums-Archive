---
title: "Wireless section absent from network menu"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by Oli123 on 2011-12-14
Hi, 

I am completely new to Linux and I am trying to set up wireless Internet on Ubuntu 11.10, however, when I go to my network menu there is nothing to select about a wireless connection. See screen-shot attached. 

Technical information about my situation which may be relevant is: the wireless connection does work fine on Windows XP; my computer is a Dell INSPIRON 6400; and I am actually running Ubuntu from an external USB powered HDD.

 One thing which does seem quite obviously wrong is that I can't use Fn and F2 to turn on the the wifi LED (however, this hardware switch does work while I am running Windows). 

I know I have b43-fwcutter installed, and the STA Broadcom proprietary wireless driver is shown as active, (in the additional drivers window it says This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware). When I run the code      lspci -vnn | grep 14e4 the returned information is

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

So my PCI-ID is 14e4:4311 ? From a thread I read it seems this should be compatible with b43-fwcutter.

Please could somebody help me so that I can connect to wireless networks?

---

### Post by JohnDillinger43 on 2011-12-14
I'm new to Linux as well, and don't know exactly what the problem would be, but I would assume it has to do with the fact that you're running it off an external drive.  A USB connection is going to be a lot slower than an SATA connection, and I wouldn't be surprised if that ends up introducing some problems with hardware (though again, I'm no expert).  Is there a specific reason you want to run Ubuntu off an external drive?  Even if the hardware problems can be fixed there's going to be a performance cost to running an OS on a USB drive.

FWIW I'm running Ubuntu and Win7 dual boot on a Dell Inspiron 1545, and Ubuntu has been working great (including the Wireless card, which I think is the same as yours).

---

### Post by Oli123 on 2011-12-15
I just wanted to run it from the usb device because it has more memory on it. But to be fair I have made better progress with this problem since I booted Ubuntu from the SATA connection, as you predicted. 

After using the code in post #3 of thread [http://ubuntuforums.org/showthread.php?t=1878099&highlight=b43-fwcutter](http://ubuntuforums.org/showthread.php?t=1878099&highlight=b43-fwcutter) the wireless section now appears in the network menu, however it says, device not ready (firmware missing). I found this a little bit confusing, as I thought that post #3 of that thread had installed the necessary firmware, or maybe it just isn't running for some reason.

The other thing that is a bit curious is when I check the additional drivers app it tells me that the STA Broadcom wireless driver is not activated. I thought it was from earlier, as I never told it to be de-activated. So anyway, I activate it but then the wireless section in the network menu disappears.

I feel like I am walking round in circles...

Please help...

---

### Post by Oli123 on 2011-12-15
Just to say to JohnDillinger, thank you very much for your reply :) ! 

I resolved the issue using the following steps. First use the code in thread post #3 of [http://ubuntuforums.org/showthread.php?t=1878099&highlight=b43-fwcutter](http://ubuntuforums.org/showthread.php?t=1878099&highlight=b43-fwcutter). Then follow steps given at [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware). It worked for me, I hope it works just as well for anyone else with the same problem.

---

