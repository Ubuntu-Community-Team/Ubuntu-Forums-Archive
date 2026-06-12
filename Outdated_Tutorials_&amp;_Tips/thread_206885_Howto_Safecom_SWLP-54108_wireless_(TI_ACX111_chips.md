---
title: "Howto: Safecom SWLP-54108 wireless (TI ACX111 chipset)"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by ?@yk0&amp;^4 on 2006-06-30
Here's my brief howto to get your Safecom SWLP-54108 wireless card working (this may work for other ACX111 chipset wireless cards also) using ndiswrapper and the Windows drivers.


1. First, blacklist the acx module by adding 'blacklist acx' to /etc/modprobe.d/blacklist

2. Configure the interface in /etc/network/interfaces - something like this:

```
auto wlan0
iface wlan0 inet dhcp
    wireless-essid MyWirelessNetwork
    wireless-key s:MyKeyCode
```

At this point it might be advisable to reboot.

3. Then install ndiswrapper and install the Windows drivers (see the Ubuntu Wiki page on ndiswrapper for this).

4. Run 'sudo modprobe ndiswrapper' to install the ndiswrapper module.

5. Test the network using iwconfig and ping.

6. If this works, add ndiswrapper to /etc/modules to allow the module to load during boot.


This may not be the best/only way to do this, but I found that doing the steps in the slightly odd order above worked for me where other methods had failed.

Good luck!
Greg :)

---

### Post by colonelk on 2006-09-11
I know this was a while ago, but did this method enable WPA support with that card?

---

### Post by PRASHPSG on 2007-04-21
I have the SWLPT-54108 card. I cannot get WPA to work on it with Ubuntu 7.04 Feisty Fawn. I think that this may be a driver issue as I have wpa-supplicant installed. 

Does anyone have any ideas on how to make WPA work??

---

