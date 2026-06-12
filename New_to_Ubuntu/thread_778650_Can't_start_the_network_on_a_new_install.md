---
title: "Can't start the network on a new install"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by dmodmodmo@gmail.com on 2008-05-02
I installed Kubuntu 8.04 on an IBM NetVista desk top box and I can't seem to get the network running.  I went to the Kmenu/SystemSettings/Network/Settings and selected "automatic dhcp" and "activate when the computer starts" and then Enabled the interface and finally clicked apply.   

The IPaddress should be in the 136.167.25.xx range but it is still 10.1.24.197 When I reboot the adaptor's configuration settings disappear. 


I took a look in System Services and found that the networking service was set “not to start at boot” and was not running.  So I enabled “start at boot” and attempted to start the service.  It came back with the “starting networking” popup with the message “*Configuring network interfaces…. Done” but the service was still listed as not running. 

I have lights on the network adapter and the Ethernet drop is good because I can get working DHCP configured network connection on my windows laptop.   

Any assistance would be greatly appreciated.

---

### Post by aeiah on 2008-05-02
in a terminal type ```
ifconfig
```

does your ethernet adaptor show up? it will probably be called eth0 or eth1. what information does it give?

does
```

sudo ifconfig eth0 up 
sudo dhclient eth0

```
do anything? (or eth1 if that is your card)

---

### Post by dokdoom on 2008-05-02
The 137 address is a public IP (If not you shouldn't use public IPs as LAN IPs. That 10 address you are getting is a private address. So when you do get assigned the 10. address are you able to get to the net? Can you ping google.com? If not can you ping 4.2.2.1? To me it is looking like you are getting the correct address but for some reason you expect to receive a public address on your LAN. Now maybe you have your reasons for doing this but I would say it's a horrible idea. 

> **dmodmodmo@gmail.com said:**
> I installed Kubuntu 8.04 on an IBM NetVista desk top box and I can't seem to get the network running.  I went to the Kmenu/SystemSettings/Network/Settings and selected "automatic dhcp" and "activate when the computer starts" and then Enabled the interface and finally clicked apply.   

The IPaddress should be in the 136.167.25.xx range but it is still 10.1.24.197 When I reboot the adaptor's configuration settings disappear. 


I took a look in System Services and found that the networking service was set “not to start at boot” and was not running.  So I enabled “start at boot” and attempted to start the service.  It came back with the “starting networking” popup with the message “*Configuring network interfaces…. Done” but the service was still listed as not running. 

I have lights on the network adapter and the Ethernet drop is good because I can get working DHCP configured network connection on my windows laptop.   

Any assistance would be greatly appreciated.

---

### Post by dmodmodmo@gmail.com on 2008-05-02
Here is what I get:   

$ ifconfig eth0 

link encap:Ethernet Hwaddr 00:02:55:3f:19:f5
inet addr:10.1.24.197 Bcast 255.255.255.255 Mask:255.255.254.0
inet6 addr: fe80::202:55ff:fe3f:19f5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500  metric:1
RX packets:2099 errors:0 dropped:0 overruns:0 frame:0
Tx packets:188 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txpueuelin:1000
Rx bytes 208660 (203.7 KB)  Tx bytes 28211 (27.5 KB)

$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6276
killed old client processes, removed pid file 
Internet System Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet System Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:55:3f:19:f5
Sending on   LPF/eth0/00:02:55:3f:19:f5
Sending on   Socket/fallback
DHCPREQUEST of 10.1.24.197 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.1.24.197 from 136.167.24.1
bound tgo 10.1.24.197 -- renewl in 238 seconds

---

### Post by dmodmodmo@gmail.com on 2008-05-02
When I ping google.com I get
ping: unknown host google.com

So it does not look like the DNS look up is happining. 

As for the 10 vs 136  the desk tops here all run on  the class B  address space. A ipconfig on my lap top confirms this.

---

