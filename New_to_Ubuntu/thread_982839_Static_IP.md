---
title: "Static IP"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Komarus on 2008-11-15
Hi,

here a beginners question:

I use Wireless Lan with static IP instead DHCP. I can fix the IP in the Network-settings and I'll be able to be online.
But if I'll restart my laptop, I can't connect anymore until I open the network-settings and repeat there my password.

Excuse my english... it's not the very best, but I hope, you understood my question.

Thx

Dietbert

---

### Post by Majorix on 2008-11-15
Getting a static ip on Ubuntu with the tools provided isn't easy.

Try [WICD]("http://wicd.sourceforge.net/download.php"). Read the section for Ubuntu.

---

### Post by Peter09 on 2008-11-15
You may not be able to do this but if you can its the best way of getting a static IP.

If you are using a router that supports DHCP then enable it. Then you will have a section concerning your LAN where you can link the MAC address of your machine to an IP. So, everytime your machine connects to the router and asks for an IP it will get the same one - the one you have allocated.

---

### Post by Gone fishing on 2008-11-15
In the latest Ubuntu 8.10 it relatively easy to set a fixed IP address using the applet in the top panel on earlier versions you need to go to Administration > Network and then turn roaming off and set up the card manually.

Alternatively you can edit /etc/network/interfaces
```

gksu gedit /etc/network/interfaces
```

mine looks like

```
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:axxxxxxxxxxxx
wireless-essid fish

auto wlan0
```

---

