---
title: "Installing a new wireless card"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by noiseordinance on 2008-05-19
Hi there,

I just purchased a new Gigabyte super-G wireless card with an Atheros chipset to replace my POS Broadcom 1390 card. I'm not sure what the process is in uninstalling the current device and installing the new card. I know how to *physically* install the card, but could someone walk me through the steps of uninstalling the current driver and installing the new driver?

Thanks...

(PS - It's a Gigbyte GN-WI01GT miniPCI EXPRESS Super G)

---

### Post by noiseordinance on 2008-05-20
Since no one replied, I simply pulled out the Broadcom 1390 and installed the Gigabyte/Atheros card. It connected to the internet immediately (thank god) but I'm getting a message about restricted drivers. This message stays in my toolbar at the top. Is there anything I should be doing?

---

### Post by jimrz on 2008-05-20
> **noiseordinance said:**
> Since no one replied, I simply pulled out the Broadcom 1390 and installed the Gigabyte/Atheros card. It connected to the internet immediately (thank god) but I'm getting a message about restricted drivers. This message stays in my toolbar at the top. Is there anything I should be doing?

Most Atheros cards (yours is probably the 5212 chipset) use madwifi and the Atheros hal stuff. Since you are connected "out of the box", I think that the system is just advising you that it has found and is using new restricted drivers. To confirm, on your panel go to System > Administration > Hardware Drivers and have a look or simply click on the notification icon that is alerting you to these drivers.

---

### Post by noiseordinance on 2008-05-25
According to Hardware Drivers, I'm using "Atheros Hardware Access Layer (HAL)" and "Support for Atheros 802.11 wireless LAN cards." One thing that is weird is that my wifi light does not turn on any more, even though it did before I switched wireless cards. The light comes on when using Windows XP, btw, so it's fairly Ubuntu specific. Should I be uninstalling NDISwrapper since I no longer use it?

---

### Post by shifty_powers on 2008-05-25
can do if you want, though you never know when it may come in handy ;)

---

### Post by noiseordinance on 2008-05-25
Well.... should I be concerned that my wifi light doesn't turn on anymore? It stopped turning on when I installed my new card, although it turns on just fine in Windows XP. However, wifi light aside, I can connect to the Internet just fine (far better than when I was using the Broadcom 1390). I just wanted to know if I should be concerned about the wifi light or not...

---

### Post by noiseordinance on 2008-05-26
...seriously... my wifi light is either turning on half way or not at all. What could be causing this? How do I verify that the correct wireless stuff is loading on startup? Also, for what it's worth, my conky was configured to show network traffic, which suddenly stopped working when I changed wireless cards...

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

---

