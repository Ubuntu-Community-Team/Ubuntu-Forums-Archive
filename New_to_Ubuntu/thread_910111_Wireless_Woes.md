---
title: "Wireless Woes"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Matuku on 2008-09-04
My wireless card isn't working on my new laptop and, unfortunately, I think the Ethernet port must be part of it as well as this doesn't appear to be working.

There are two questions I have; I believe the card is an atheros chipset but how can I check this?

And if it is, how can I download NDISwrapper to the laptop with no internet connection on it?

---

### Post by porchrat on 2008-09-04
you check it like this:

```
lshw -C network
```

you actually have 2 options if it an Atheros...you can use ndiswrapper with the windows driver, or you can use the madwifi drivers

---

### Post by Matuku on 2008-09-04
This is the output I get:
```

 *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:65:62:99
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

So the wireless is an atheros yes? And the ethernet appears to be from Nvidia? That's odd.

So how would I go about installing ndiswrapper/madwifi without any form of internet currently on the laptop?

---

### Post by porchrat on 2008-09-04
This is the part you are interseted in:

> product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.


Your card is an AR242x...also known as an atheros AR5007, or just 5007 sometimes.

there are numerous guides around...I have the same card on my Acer laptop and I used the madwifi drivers, they work fine.

Some people say the ndiswrapper system is faster, I wouldn't know though as I got the madwifi working first time.

you can check out the website here:
[http://www.madwifi.org]("http://www.madwifi.org")

Here is a guide for ndiswrapper as well:
[http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419")

---

### Post by Matuku on 2008-09-04
But I don't have build-essentials on the laptop do I? I thought you had to download that package; it wasn't included on the normal install?

---

### Post by porchrat on 2008-09-04
Are you sure your ethernet is not functioning?  how exactly do you access the internet?...through a router?

---

### Post by Matuku on 2008-09-04
Yeah, the ethernet works fine on the windows side but when I plug the cable in on the ubuntu side, nothing; doesn't even seem to register it.

---

### Post by porchrat on 2008-09-04
and you can't ping your router? ...or browse to it using firefox? (or opera or whatever your flavour is)

---

### Post by Matuku on 2008-09-04
It's strange; if I plug in the cable after booting up it fails to recognise it at all, just says its not connected. If I plug it in beforehand then it will appear to connect but won't allow me to access the internet; how can I check if it's actually attached to the network or not?

EDIT: On the times it does connect to the network if I go Places>Network it shows "Windows Network" which should indeed exost on the network but I still can't get internet access with it.

---

### Post by Matuku on 2008-09-05
Got it working by following these [http://ubuntuforums.org/archive/index.php/t-590093.html](http://ubuntuforums.org/archive/index.php/t-590093.html) instructions and using the drivers found here [http://www.megaupload.com/?d=P8I57N0S](http://www.megaupload.com/?d=P8I57N0S) (you want the .inf file from the ndis5x folder). Woo wireless!

---

