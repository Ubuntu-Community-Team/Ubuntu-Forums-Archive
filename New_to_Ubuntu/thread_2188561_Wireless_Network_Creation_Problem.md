---
title: "Wireless Network Creation Problem"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by Agnishom_Chattopadhyay on 2013-11-17
I cannot create a hotspot anyway. Although, trying to do so in other Ubuntus, I have succeeded. Although Ubuntu can connect to an active Wi-Fi Network, it cannot create a network. Whats wrong?

Please help

---

### Post by Agnishom_Chattopadhyay on 2013-11-18
bump

---

### Post by yc.chenyi on 2013-11-18
It depends on the Wireless card and its driver. 
Most card drivers support to work both as Access Point (Hotspot) and Station (general use).
It seems that your card doesn't support AP mode. Or perhaps, the driver you are using doesn't provide AP mode.
Try ***lspci*** to find out the model of the card, and search some other drivers to try.

---

### Post by Agnishom_Chattopadhyay on 2013-11-19
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```
This card *does* support Wireless Access Points. I've created Access Points with this card on Windows 7 and Puppy Linux.

How to find information on my driver?

---

