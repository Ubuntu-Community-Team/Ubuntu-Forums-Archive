---
title: "Wireless Difficulty"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by mkramsey on 2008-11-21
My computer will connect to wireless networks everywhere but at my house. While I'm at home, it doesn't even search for a signal. I've tried to manually add the wireless network, but it doesn't work. Our wireless signal comes from a cable network.

Any suggestions? Do I need to add an additional driver? My wireless card on my Gateway is a Mini pci type 3B. 

Please help!!

---

### Post by efeurich on 2008-11-21
If your computer connects to other wireless networks the settings of the computer seem to be right. Try to look into the settings of your wireless router.

You can go there by finding out what the ipaddress is of the router and connect to it by typing the ipaddress in to the browser. Check if it is set to DHCP (Dynamic Host Configuration Protocol)

---

### Post by ibuclaw on 2008-11-21
What does iwlist tell you?

```
iwlist scan 2>/dev/null | grep ESSID
```

Regards
Iain

---

### Post by marshall.robert on 2008-11-21
I experience something very similar to this.

everywhere i have been so far i  can find wireless networks, but there is 1 at college which i know is there, i can connect to it in windows, i could connect in ubuntu before i reinstalled, but now i cant see it atall...

using intel 3945

---

### Post by chrisod on 2008-11-21
Is the network encrypted? Network Manager on my laptop defaults to 64 bit encryption. If the router is set up for 128 it will not connect. You need to change the encryption type - there are several options, try then all.

Another possibility, are you sure the problem network is not set to filter by MAC address? You'll be able to see the network just fine, but the router will simply ignore your attempts to connect if you are not on the white list.

---

