---
title: "Wireless not working in ubuntu 8.10 but was at Alpha 6 - 8.10"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-11-16
Hello, 
My brother latptop has an wireless atheros card

14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) - information gain by doing a lspci in the terminal

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

I try ubuntu 8.10 at Alpha 6 and the wireless card was working perfectly out of the box, but it doesn't seem to work now

I have re-able the restricted drivers and it still doesn't work, any help would be useful!!

---

### Post by ibizatunes on 2008-11-18
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

This howto fix's my issue

---

### Post by bumanie on 2008-11-18
This may help [http://ubuntuforums.org/showthread.php?t=985826](http://ubuntuforums.org/showthread.php?t=985826) I actually used ndiswrapper on my 32bit laptop - it works well (same card).

---

