---
title: "Network button isn't working so I don't have network"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Darkade on 2008-05-19
I have an Acer Aspire 5720-4216, just installed ubuntu today. The thing is that my wireless card used to activate through a special button, as well as my Bluetooth. and now those buttons don't work so I have no Wireless network nor bluetooth. I don't care if those buttons work or not, but how can I enable my wireless card and my bluetooth? thanks

---

### Post by GCoffee on 2008-05-19
I belive if you go to:

System > Administration > Network (or network tools)

You find a option to enable wireless and for bluetooth I you go to:

System > Preferences > Bluetooth.

Hope that helped.

Gcoffee.

---

### Post by Darkade on 2008-05-19
> **GCoffee said:**
> I belive if you go to:

System > Administration > Network (or network tools)

You find a option to enable wireless and for bluetooth I you go to:

System > Preferences > Bluetooth.

Hope that helped.

Gcoffee.

that was my first option, the thing is it doesn't work. because I don't think the system "see" my Wireless card, nor my bluetooth. even though my card is listed if i use 

```
lspci
```

here's what I get

```
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I also attach the Bluetooth window, and the network window. As you can See in the bluetooth preferences I can't access to the the connections, and in the network preferences there's no wireless card listed

Ideas?

---

### Post by barnex on 2008-05-19
You might want to check if NetworkManager is running in the background, if not you can start it manually: ```
sudo NetworkManager&
```.
There may of course be many other reasons why it's not working in your case.

---

### Post by mapes12 on 2008-05-19
or switch Network Manager apps to this one:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I don't have the same problem but others have reported success by switching.

---

