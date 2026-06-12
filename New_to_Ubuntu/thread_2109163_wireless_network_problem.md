---
title: "wireless network problem"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by ariello on 2013-01-26
Hello guys.
I have installed **ubuntu 11.10 server** edition on an older machine and I want it to connect to the network by wi-fi (LAN is working with no problems). I bought a usb wi-fi card with Ralink module (**rt5370sta**). There were some problems with installation but thanks to this forum I finally installed it. Now it appears on the list but I do not know how to run this module. I am using command-line only (no gui).
Thank you for any help ;)
Here are some outputs from commands:

**ifconfig** shows details for **eth0** and **lo**.

**iwconfig:**
```

lo
no wireless extensions.

eth0
no wireless extensions

ra0
Ralink STA
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

```

**lsusb:**
```

...
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp.
...

```

**lsmod**
```

...
Module: rt5370sta Size: 713680 Used by: 0
...

```

**sudo lshw -c network**
```

*- network
description: Ethernet interface
...
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: ra0
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=RALINK WLAN multicast=yes
wireless=Ralink STA

```

**iwlist scan**
lo,eth0 and ra0 --> Interface doesn't support scanning.

**uname -mr**
```

3.0.0-30-generic i586

```

---

### Post by frank604 on 2013-01-26
Did you scan as root(sudo)?

---

### Post by NikTh on 2013-01-27
> **ariello said:**
> 
I have installed **ubuntu 11.10 server** edition on an older machine 

Hi ,
why you installed Ubuntu 11.10 ? 
Ubuntu 11.10 will reach E.O.L in few months (April) and will not supported anymore. 
Read here about Ubuntu versions:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Can you re-install another version ? 

Try Ubuntu 12.04 LTS (support until April 2017) , with newer kernel , newer packages , newer modules.. maybe the wireless will work "out of the box" . 

Ubuntu 12.04.1 LTS can be found here
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Thanks

---

### Post by 3rdalbum on 2013-01-27
Ubuntu Desktop can be used as a server too, much easier than Ubuntu Server (which is more for big enterprise sites). You might want to try installing Ubuntu Desktop 12.04 or 12.10 and using the GUI to connect to wifi, and then install your server packages.

Unless you want to jump in the deep end and learn without a GUI safety net. Sorry I can't help further.

---

### Post by ariello on 2013-01-27
Thanks for your answers.

**frank604**: yes, I tried to use all these commands both with sudo and as a root. Some of them did not even run without superuser permissions (if I remember it well).

**NikTh:** Unfortunately, I cannot use Ubuntu higher than 11.04/11.10 because my spare computer is quite old and does not support new feature which is "PAE" (or something like that, I forgot the proper name). Ubuntu 12.04/12.10 does not even run the installer because of this. 

**3rdalbum:** Unfortunately, I cannot use a gui because this computer has 256mb of RAM and gui works so slow... therefore I wanted to try the server option.

Do you have an idea why in **lshw** command the wireless network is shown as "DISABLED"?

In the worst case scenario I will stick to the LAN option :D

---

### Post by 3rdalbum on 2013-01-27
Even if you can't scan for a wifi network, you may still be able to join one with the iwconfig command. I'm not near my computer at the moment but you can type 'man iwconfig' to see the various options it takes and how to use it.

Good luck.

---

### Post by iMac71 on 2013-01-27
you might find some help in [post=11831414]this tutorial[/post] and in [post=11831689]its appendix[/post].

---

### Post by steeldriver on 2013-01-27
If you are using a Server edition then afaik by default your networking (wired and wireless) will be managed by the older networking service rather than network-manager or wicd

You should be able to bring up a wireless connection just like your wired connection by specifying it in the /etc/network/interfaces file. You will need to add the SSID and credentials there - imho the Debian documentation is a good starting point:

[http://wiki.debian.org/WiFi/HowToUse#Command_Line](http://wiki.debian.org/WiFi/HowToUse#Command_Line)

Start by looking at the current contents of /etc/network/interfaces to confirm that's where your wired LAN connection is configured

---

### Post by ariello on 2013-01-27
After some reading I have ran it and connected with the network but then there was another problem --> no IP address. After some more reading I sorted out as well. I had to change files "**interfaces**" and "**wpa_supplicant**" then use "**ifup**" then "**dhclient**" then add lines in interfaces to have it permanently and here we go. Ubuntu server on compaq TC1000 working with no more network errors ;)
Thanks guys for your replys! :popcorn:
In total it took me about 5 days hah, but it was worth it!

---

