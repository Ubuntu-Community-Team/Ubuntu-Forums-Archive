---
title: "Obtaining open source drivers"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by will1982 on 2012-10-08
Is there any way I  can get open source drivers for this card? Attached is a photo of the screen I get.

The card works perfectly, but I was just wondering.
Thanks :D

---

### Post by albandy on 2012-10-08
Read this article: 
[http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/](http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/)

---

### Post by audiomick on 2012-10-08
> **will1982 said:**
> Is there any way I  can get open source drivers for this card?

Without having completely read the article albandy linked to, here is my two cents. As far as I know, if you remove the proprietary driver using the option offered in that window, the system will revert to the open source drivers that are quite possibly installed already. 

I did that once with my video drivers to check up on a problem with the open source drivers for someone, and it worked that way. I did, however, after re-installing the proprietary drivers, acquire an annoying error message at boot about a saved resolution not being supported.

Your question refers to Wireless drivers rather than video. The reversion to open source drivers should still work if you remove the proprietary one, but I don't know if you can confidently expect the open source drivers, if present on the system, to work properly. In short, I wouldn't be messing around with a working system :) If you really want to try this out, I would strongly suggests doing the playing around in the live environment or in a dedicated experimental install.

---

### Post by GeForce 9500GT on 2012-10-08
This will work as i experienced:
 
- open a terminal
- type the following command:
```
sudo apt-get install firmware-b43-installer
```
- follow the instruction given in the terminal
- then type the following command:
```
sudo apt-get remove bcmwl-kernel-source
```
- reboot your system.

---

