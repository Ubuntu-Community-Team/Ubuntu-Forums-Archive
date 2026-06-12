---
title: "[SOLVED] Restart Wireless Card"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by azurepancake on 2008-05-21
Every once in awhile, one of my computers running Hardy will loose it's wireless connection to my wireless router and won't reconnect until I reboot the system. The wireless status bar is at 0% and when I look at the list of available networks, I can see my network's SSID, presented within decent range.

So my question is if there is anyway to restart my wireless card without rebooting my computer every time this happens? Or even better, does anyone know what might be causing this?

If it is of any help to you, when I run the "lshw -class network" command, I get the following information:

```
  
*-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:30:1b:46:63:63
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:02:3b:95:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.15 multicast=yes wireless=IEEE 802.11g

```

Any advice would be much appreciated. If you need anymore information about my system, please ask.

Thanks

---

### Post by spiderbatdad on 2008-05-21
```
sudo dhclient
```

---

### Post by azurepancake on 2008-05-21
Awesome, thanks a lot. I'll give that command a shot next time the problem occurs.

---

### Post by spiderbatdad on 2008-05-21
My understanding is that command requests an ip adress from the dhcp server.

You can also try: sudo ifup eth1

---

### Post by azurepancake on 2008-05-21
Ok. I just got my first chance to test the commands out and unfortunately I didn't have much luck..

"sudo dhclient" spits out:

```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:16:e6:42:14:e0
Sending on   LPF/eth0/00:16:e6:42:14:e0
Listening on LPF/wlan0/00:16:b6:9b:f6:5f
Sending on   LPF/wlan0/00:16:b6:9b:f6:5f
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.9 from 192.168.1.254
DHCPREQUEST of 192.168.1.9 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.9 from 192.168.1.254
bound to 192.168.1.9 -- renewal in 42849 seconds.

```

and "sudo ifup wlan0" outputs:

```

Ignoring unknown interface wlan0=wlan0.

```

I'm not quite sure where to go from here. I tried reconnecting, but nothing. I just rebooted the system and it connected on its own, no problems. I noticed this time that the system lost it's connection almost immediately after I began a large transfer to it, via rsync from another machine. Don't really know if this had anything to do with it, but will try at it once more.

Thanks again.

---

### Post by azurepancake on 2008-05-21
Well after attempting the transfer, it began and cut off soon after. I am beginning to doubt this is just a coincidence.

---

### Post by FRuMMaGe on 2008-05-26
Same problem here I'm afraid. Unfortunately it doesn't seem like it is specific to one wireless chipset.

By the way, you can easily solve the "Ignoring unknown interface wlan0=wlan0." error by doing the following:
```
sudo gedit /etc/network/interfaces
```
Then add the following to the end of that file (without the quotes) "iface wlan0 inet dhcp"

---

### Post by hyper_ch on 2008-05-26
restarting the whole network stuff:
```

sudo /etc/init.d/networking restart

```

---

### Post by FRuMMaGe on 2008-05-26
> **hyper_ch said:**
> restarting the whole network stuff:
```

sudo /etc/init.d/networking restart

```

Just a note, this doesn't solve the problem.

I've found a solution though, just install WICD instead of network manager. I haven't had any problems since.

Just add to your software sources the following repository (without the quotes) "deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras".

Now just "sudo apt-get install wicd"

---

### Post by azurepancake on 2008-06-06
> **FRuMMaGe said:**
> Just a note, this doesn't solve the problem.

I've found a solution though, just install WICD instead of network manager. I haven't had any problems since.

Just add to your software sources the following repository (without the quotes) "deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras".

Now just "sudo apt-get install wicd"

WICD is amazing! This has fixed all my issues and I can actually assign a static IP to this system and still be able to connect to my network! No more random disconnects either. 

Thank you very much!

---

### Post by ukripper on 2008-06-06
Please mark this thread as SOLVED.

---

