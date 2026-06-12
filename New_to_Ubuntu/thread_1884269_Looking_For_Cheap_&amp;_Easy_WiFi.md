---
title: "Looking For Cheap &amp; Easy WiFi"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by Glkanter on 2011-11-21
Hi guys,

I have a PC running Ubuntu 11.04. I need to purchase and install some WiFi capability. I have an old hand-me-down D-link usb adapter that is just too slow.

I'm using a Zoom router that is 802.11n at 150 mps.
 
I can use either a usb adapter or a pci card. If the cost isn't too much higher, and it will work with Ubuntu, I would consider a 300 mps WiFi solution for the PC.

Thanks!

Garry

---

### Post by lincoln32 on 2011-11-21
Most wireless cards do work and well but there are some issues with N
and are you trying to get faster internet or move files locally?
most internet is well below wireless g devices and you may have other issues
like signal or others---this is my current n usn device

[http://www.ebay.com/itm/Mini-300Mbps-USB-Wireless-Adapter-WiFi-802-11b-g-n-Network-LAN-Card-Antenna-PC-/200678099961?pt=LH_DefaultDomain_0&hash=item2eb958cbf9:](http://www.ebay.com/itm/Mini-300Mbps-USB-Wireless-Adapter-WiFi-802-11b-g-n-Network-LAN-Card-Antenna-PC-/200678099961?pt=LH_DefaultDomain_0&hash=item2eb958cbf9:))

---

### Post by Glkanter on 2011-11-21
I don't understand your comment regarding wifi speed. My experience, and my readings on the subject are very different.

That adapter on eBay doesn't mention supporting Linux. I'd love to find a $10 solution, and have used eBay for this purpose, but I'm just not sure...

Thanks!

---

### Post by haqking on 2011-11-21
> **Glkanter said:**
> I don't understand your comment regarding wifi speed. My experience, and my readings on the subject are very different.

That adapter on eBay doesn't mention supporting Linux. I'd love to find a $10 solution, and have used eBay for this purpose, but I'm just not sure...

Thanks!

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

lists supported cards (USB, PCI)

The speed i think he was mentioning above means the speed of a wifi device usually far exceeds that of an internet connection.

For example a speed of 150Mbps on 802.11n means nothing if your internet connection is only 20 or less, however for LAN file transfer it is more significant

---

### Post by Glkanter on 2011-11-21
This is the result of lsusb for a usb wifi-n device I have, but I haven't gotten it to work:

```
glkanter@glkanter-System-Product-Name:~$ lsusb
...
Bus 002 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
...
glkanter@glkanter-System-Product-Name:~$ 

```Any hope?

---

### Post by anewguy on 2011-11-21
If you want to try to get your existing working:

- post back the output of:

iwconfig

ifconfig

lshw -C network


If you want a cheap replacement - follow some of the links already posted.  Also check Tiger Direct or Micro Center.  Our local Micro Center has carried very cheap Tenda usb units that some have working.

---

### Post by kurt18947 on 2011-11-21
I have 2 USB WiFi N150 adapters that are plug & play.  These are plug & play on Ubuntu  11.04 & later.  They can be used on 10.04 & 10.10 but require tweaks.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122366&Tpk=netgear%20wna1100](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122366&Tpk=netgear%20wna1100)

Note that this is a WNA1100. Other Netgear models, WNA3100 and WNDA3100 are not plug & play.  In fact I'm not sure there are native Linux drivers for them at all.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&Tpk=trendnet%20TEW-649UB](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156268&Tpk=trendnet%20TEW-649UB)

Again, pay attention to the model #.  There is a TEW-64**8**UB which I believe requires some tinkering to get it to work.

I'm sure there are other N speed devices that are plug & play as well but these have worked for me on multiple installs with no tinkering required.

---

### Post by Glkanter on 2011-11-21
[SIZE=2]Once again, you guys are **the best**!

I'm going to close this thread - which asked for a purchase recommendation - [/SIZE][SIZE=2]as solved, [/SIZE][SIZE=2]and open a new one for troubleshooting the stuff I actually have.

Was there a model # for the Tenda inexpensive stuff at Micro Center? I live about 5 miles from a Micro Center, had the various Tenda  products in my hands yesterday, but just couldn't pull the trigger because I knew there could likely be issues.

But, maybe there's another solution, and I haven't really explained what's going on yet...
[/SIZE][SIZE=2]
Thanks![/SIZE]

[SIZE=2]Garry[/SIZE]

---

### Post by Glkanter on 2011-11-21
[SIZE=2]I have re-started this thread at [http://ubuntuforums.org/showthread.php?t=1884457](http://ubuntuforums.org/showthread.php?t=1884457)[/SIZE]

Thanks!

---

