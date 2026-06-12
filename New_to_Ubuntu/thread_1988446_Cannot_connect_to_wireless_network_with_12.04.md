---
title: "Cannot connect to wireless network with 12.04"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by jmills1624 on 2012-05-27
I managed to finally get my HP AMD 64 desktop loaded with Ubuntu 12.04. During the install, I got an error message about needing rt73.bin, which I tried unsuccessfully to install several times. I ended up going to Staples and buying a netgear usb dongle, and it loaded just fine. Where before the usb wifi wouldn't/couldn't see a network, now it sees the network, but it absolutely will not connect no matter what I do. It'll say connecting for 2-5 minutes, then disconnect, then retry over and over. I've reset the router, removed and added WPA to the router, no matter what it just does not work. Please help!

---

### Post by NikTh on 2012-05-27
Hi , 
it will need further info for someone to help you .. 
For begin let us see the output of these commands with dongle plugged
```
lsusb 
iwconfig 
rfkill list all
```

---

### Post by jmills1624 on 2012-05-27
lsusb -
 Bos 001 Device 001 - Linux foundation Root 2.0 hub
 Bus 002 Device001 - Linux Foundation Root 1.1 hub
 Bus 001 Device 002 Netgear Inc WNA1000M 802.11bgn [REALTEK RTL81 88CUS]
 Bus 001 Device 005 - 0bda:001 realtek semiconductor corp cardreader
 Bus 002 Device 002: 046d:092e Logitech Quickcam Chat
 Bus 003 Device 003: 046d:c52f Logitech Wireless Mouse M305

iwconfig -
 lo   no wireless extensions.

 wlan0 IEEE 802.11bgn ESSID:off/any
       mode:managed Access Point: Not-Associated  Tx-Power=20dbm
       Retry long limit:7 RTS thr=2347 B Fragment thr:off
       Power Management: off

rfkill list all
 0: phy0: Wireless LAN
      Soft blocked: no
      Hard blocked: No

---

### Post by anewguy on 2012-05-27
Please see [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190") thread in launchpad.  It's quit large to look through and some od the posts you can just skip over.  It sounds like others are getting the driver source fron Realtek, patching that source, building the new driver and removing the old.

Also - if you temporarily use a hardwire connection do so and then run additional drivers and see if it gives any recommendations.

dave ;)

---

