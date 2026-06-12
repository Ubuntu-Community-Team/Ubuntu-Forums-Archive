---
title: "Broadcom Wireless Problem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by MikeRaines on 2008-05-27
Hi, I'm new to the Ubuntu community, just installed it yesterday.

My problem is I installed Hardy Herin on my HP Pavillion dv6000 with vista preinstalled. This laptop comes with a built in wireless card that appears as the following when run

lspci | grep Broadcom

returns

03:00.0 Newtowrk controller: Broadcom Corporation BCM94311MCG wlan mini-PCT (rev 02)

I spent about 6 hours last night trying to get the wireless to fire up. I spent hours on the let looking at other people's posts who had the same issue but with no luck. Here are the different methods I tried.

Please forgive my ignorance, i'm new to linux.
------------------------------------------
Method 1:
Downloaded & Installed ndiswrapped
Downloaded & Installed cabextract
Downloaded Drivers: [http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1)

Extracted from .exe
sudo ndiswrapper -i bcmwl5.inf

//Then:
iwconfig

//still returns:
lo no wireless extensions

eth0 no wireless extensions

//No wlan0 :(

//After this failed I read about the fwcutter method and how //ndiswrapper can interfere so I formatted again and reinstalled //ubuntu
----------------------------------------------------
Method 2:
Downloaded and Installed bcm43xx-fwcutter
Downloaded and Installed cabextract
Downloaded driver: [http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=ob-38773-1)

extracted from .exe
bcm43xx-fwcutter -w /lib/firmware bcmwl5.sys

//The files then cut to the firmware directory correctlly
//I restarted

//Then:
iwconfig

//still returns:
lo no wireless extensions

eth0 no wireless extensions

//No wlan0 :(
------------------------------------------------
On this version on laptop the wireless card can be toggled off and on via a switch on the front. The light is red when off and blue when on(when vista was installed). Since formatting and installing ubuntu the light is red no matter what the position of the switch. I am not sure if this is a driver issue or what not, but I doubt the card is bad since it was working fine moments before installing ubuntu.

Any help would be greatly appreciated. Perhaps I am not doing something correctlly, or missing some key command or factor to linux.

Thanks in advance.

---

### Post by spiderbatdad on 2008-05-27
Can't tell from your post whether you followed any specific tutorials. There are several steps to configuring the card to work that you didn't list.
Try this tutorial:[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by MikeRaines on 2008-05-27
Thanks i'll give this one a try.

---

### Post by nalinib on 2008-05-27
I have hp-compaq laptop with broadcom wlan and vista preinstalled

I recieved the following error message at boot time (while booting ubuntu 8.04 via lice cd)

"b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4)."

It seems the site has extensive instructions.

Since I don't use wlan I just ignored the error.

Hope this information will help.

Good luck

nalinib

---

### Post by MikeRaines on 2008-05-27
Thanks, this got it recognizing the wireless card, but now it's having issues connecting to the wireless network even though I can see it. I'll post about that in a seperate thread though. Thanks again!

---

### Post by spiderbatdad on 2008-05-27
in your new thread, please post the output of```
iwlist scan
```

---

