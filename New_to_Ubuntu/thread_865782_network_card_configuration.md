---
title: "network card configuration"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by dineshs on 2008-07-21
I am new to linux.After configurinfg ethernet using the command (ifconfig eth0 192.168.1.200 netmask 255.255.255.0 up ) I dont find any change in entry in /etc/network/interfaces.But when I do it via GUI (system-administration-networking)it gets updated.What could be the reason.I am using ubuntu 6.1.Kindly help

---

### Post by iaculallad on 2008-07-21
> **dineshs said:**
> I am new to linux.After configurinfg ethernet using the command (ifconfig eth0 192.168.1.200 netmask 255.255.255.0 up ) I dont find any change in entry in /etc/network/interfaces.But when I do it via GUI (system-administration-networking)it gets updated.What could be the reason.I am using ubuntu 6.1.Kindly help

What about doing restarting the network daemon after configuring the ethernet device using ifconfig:

```
sudo /etc/init.d/networking restart
```

Then, try to **cat /etc/network/interfaces** if it registers the changes.

---

### Post by dineshs on 2008-07-21
I get this when i try sudo /etc/init.d/networking restart

root@dataone-desktop:/home/dataone# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by iaculallad on 2008-07-21
Post whatever displays when you issue the command below on your terminal:

```
cat /etc/network/interfaces
```

---

### Post by dineshs on 2008-07-21
This is what I get

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by ModelM on 2008-07-21
The reason the ifconfig command doesn't alter that (or any) file is that it isn't supposed to. The ifconfig command configures network interfaces. If you want to alter the /etc/network/interfaces file you'll have to edit it by hand, or use some gui tool.

---

### Post by dineshs on 2008-07-21
Thank you very much

---

