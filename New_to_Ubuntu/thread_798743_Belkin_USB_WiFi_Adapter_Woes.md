---
title: "Belkin USB WiFi Adapter Woes"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by chrisleydon on 2008-05-18
Hello,

Complete n00b to Linux and Ubuntu as an OS here, so please bear with me.

I'm aware that 8.04 of Ubuntu has support for the Belkin F5D7050 USB WiFi adapter out of the box, however trying to get that little dongle to work seems like asking the world to rotate on a different axis.

The computer can see Wireless networks, but when the WEP key is entered it cannot connect. I've tried adjusting all of the settings when entering the WEP key and I've repeated them again and again; but cannot get this to work for the life of me.

If anyone could perhaps shed some light on my situation that would be absolutely fantastic!

Thanks,

Chris Leydon.

---

### Post by teaker1s on 2008-05-18
have you tried unencypted test, some routers/wireless are bad combinations if you can connect without encryption, then the next issue is encyption.
Most wep is 64 or 128 bit hex shared key

---

### Post by chrisleydon on 2008-05-19
Thanks, I'll get on to this and give you an update on how it works.

---

### Post by ubume2 on 2008-05-24
I have the Belkin 7050 usb wireless adapter too. I did all of the ndiswrapper stuff, and installed drivers, but no luck. Finally I removed all of those installed drivers via ndiswrapper. I uninstalled ndiswrapper. I discovered that one of the native drivers is a match for this adapter.

I did not use System>Administration>Network, or any GUI.

For me the secret was a change in the /etc/network/interfaces, and adding some lines to /etc/rc.local.

In the interfaces file make sure that your device is installed. 
auto lo
iface lo inet loopback  -----should already be there

I had to add auto eth1
iface eth1 inet dhcp

For the rest follow my post on:
[http://ubuntuforums.org/showthread.php?t=571188&page=51](http://ubuntuforums.org/showthread.php?t=571188&page=51)

Also refer to kevdog's howto in that thread.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by ubume2 on 2008-05-24
oops duplicate

---

### Post by Austin_KW on 2008-05-24
Which belkin F5D7050, There are different chipsets depending on the version. And multiple drivers can get loaded and cause conflicts

Post back the output of the following commands to see what version you have and what usb drivers are loaded
```

lsusb
lsmod | grep usbcore

```

---

### Post by pablodamon on 2008-05-24
help

---

### Post by anewguy on 2008-05-24
Okay, I'm going to pass along something that is going to sound stupid, but it bit me more than once.

I have a Belkin USB "stick" wireless adaptor that sits in a stand but I don't know the model.  However, this is model independent.  When you enter your WEP or WPA code, be SURE the number of bits for encryption is correct.  I was having this same problem - clicking on the network manager icon I could see wireless networks but when I clicked on mine and tried my password it failed.  Low and behold the default is 128-bit encryption, and I needed 64-bit.  Just made that change right on the network key screen when trying to connect and no problems.

Sounds stupid, I know, but I seem to remember back a release or 2 it either defaulted to something else or (I think this was the case) it FORCED you to select the number of bits, etc..

At any rate, if you haven't done that, give it a try.  You'll know from how you set up your router what you need to specify.  Also, be sure your router is broadcasting the SSID for your initial tests.  I never had much luck with mine when I tried to "hide" the network id.

Maybe this dumb suggestion will help!  :):)

---

