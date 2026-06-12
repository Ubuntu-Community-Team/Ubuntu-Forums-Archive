---
title: "Help finding MAC address for usb wireless"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by tstack77 on 2012-01-21
I am trying to use a usb wireless adapter (TP-Link TL-WN822N) instead of the weak onboard wireless on my Zotac Mag Ion. When I plug it in, Network Manager still uses the internal adapter, and I want to tell it to use the MAC address of the external instead. 

Using "lsusb"I have found that Ubuntu 10.10 recognises that the device is present, but I am not able to find the MAC address using "ifconfig". 

This adapter is known for working straight-out-the-box, where am I going wrong here?

---

### Post by deonis on 2012-01-21
I am not sure it works in 10.10 but it might work with 11.10 ... it looks like you do not have a driver for it.

---

### Post by tstack77 on 2012-01-21
Thanks for that info, I see that it is supported in 11.04. I have been looking for an updated driver to install but I can't find it, plus ndiswrapper doesn't install the windows version.

Where/how can I update my atheros drivers?

---

### Post by SuaSwe on 2012-01-21
Morning!

According to [[COLOR="Blue"]this site[/COLOR]]("http://forums.scotsnewsletter.com/index.php?showtopic=51430"), the following should work:

> 
1. Install firmware-atheros_0.34_all.deb from the Debian sid repo
2. Plug the unit in . It works! The ath9k_htc driver loads automatically.


Does that work?

---

### Post by melhiore on 2012-01-22
> **tstack77 said:**
> but I am not able to find the MAC address using "ifconfig".

iwconfig??

---

### Post by 3rdalbum on 2012-01-22
Connect to the network using the desired device.

Go to the Network Manager indicator on the top panel and come down to Connection Information. Click the tab from the desired wifi adapter and its MAC address will be shown.

Alternatively, if this is an external device, its MAC address is probably printed on its bottom next to the serial number.

---

