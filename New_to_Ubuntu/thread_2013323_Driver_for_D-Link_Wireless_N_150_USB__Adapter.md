---
title: "Driver for D-Link Wireless N 150 USB  Adapter"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by vogelzmr on 2012-06-30
I just Installed Ubuntu 12.04 64bit on my desktop. 

I am wondering if there is a driver for my USB wireless adapter? I checked Dlink's website but it looks like my model does not have a driver for linux. 

I did not understand what I saw in the other threads in this topic as I am brand new to Ubuntu. I am not helpless with a computer but these other threads assume a fair bit of previous knowledge on Ubuntu. So thats why I am here. 

From the other forums it seemed like people were have a lot of troubles with there wireless adapter. Should I just go buy one that can work with linux? 

Thank you

---

### Post by mapes12 on 2012-06-30
A link that may help:-

[http://www.linux-drivers.org/network.html](http://www.linux-drivers.org/network.html)

---

### Post by sudodus on 2012-06-30
Check these links

[[COLOR="Red"]_http://www.pclinuxos.com/forum/index.php?topic=101349.30_[/COLOR]]("http://www.pclinuxos.com/forum/index.php?topic=101349.30")

DLink N150 (DWA-125) Wireless USB adapter 

[[COLOR="red"]_https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB_[/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB")

But bear in mind that this latter report is about Ubuntu 10.04. The support should be much better in the current version 12.04.

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1943983_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1943983")

---

### Post by mapes12 on 2012-06-30
Just had a look at the D-Link USB wifi adapter I have plugged in and it's Model No. DWL-G122. It works out of the box.

---

### Post by kurt18947 on 2012-06-30
What model Dlink?  I have one - WNA1100 - which is plug & play.  Perhaps better yet, if you could post the output of this terminal command:

```
lsusb
```There should be a line there that looks something like this:

> Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]This tells us the chipset which is *really* what matters in linux.

---

### Post by vogelzmr on 2012-06-30
[QUOTE=sudodus;12065304]

DLink N150 (DWA-125) Wireless USB adapter 

[[COLOR=red]_https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB_[/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB")

Well according to this list the DWA-125 (my model) is not supported. I  returned the USB be today and got a full refund :) I kinda want to get a  300 mbps version anyway. 

So I am going to buy a new one. 

There is one I found here [http://shop.linuxemporium.co.uk/hardware/hardware-wireless/tp-link-54mbs-802-11g-usb-wifi-adaptor.html?SID=746e90b567e0c2998eba48bbcb6d8d59](http://shop.linuxemporium.co.uk/hardware/hardware-wireless/tp-link-54mbs-802-11g-usb-wifi-adaptor.html?SID=746e90b567e0c2998eba48bbcb6d8d59) 

its only 54 mbps though? Just looking for opinions on buying a new one. 

Thanks for all the help!

---

### Post by mapes12 on 2012-07-01
I have bought wifi adapters from the Linux Emporium, even a complete Desktop system. They work out of the box, but I see the one you're looking at is still under test. May be worth calling them.

---

