---
title: "Netgear n600 problems"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by NickSellors on 2013-04-28
I am new to Ubuntu and I am learning but this netgear has me struggling. Any help for me to get this usb wifi adaptor working would be appreciated.

I am running Ubuntu 12.10 64 bit

lsusb
Bus 008 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

ndiswrapper -l
bcmwlhigh5 : invalid driver!
bcmwlhigh6 : driver installed
    device (0846:9011) present
scmndisp : invalid driver!

---

### Post by NickSellors on 2013-04-28
Think i have it setup ok but i keep getting an error when i run the following 

root@ubuntu:/home/nick/Netgear# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

---

### Post by NickSellors on 2013-04-28
root@ubuntu:/home/nick/Netgear# sudo ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9011) present
root@ubuntu:/home/nick/Netgear#

---

