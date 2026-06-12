---
title: "BCM57788 driver"
date: 2018-10-10
forum: New to Ubuntu
---

### Post by jereyu on 2018-10-10
Hi, thank you for your attention, I am a new Ubuntu, recently, I changed my computer (Dell Vostro 460) OS from Windows 7 to Ubuntu, but I found I don't have my wifi driver and I can not use WIFI. So I hope I can have a method to download the driver. 

By the way 

-$ lspci -nn -d 14e4:

Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)

---

### Post by oldrocker99 on 2018-10-11
Broadcom drivers should already be in the kernel. Do you have a wifi icon? Does it show any channels?

---

### Post by Holger_Gehrke on 2018-10-11
The device lspci shows you is your wired LAN. If it were a a WLAN device it would say something like '802.11ac Wireless Network Adapter'. If there's nothing like that in the output of 'lspci', it might be connected by USB. You can list USB-devices with 'lsusb'.

Holger

---

