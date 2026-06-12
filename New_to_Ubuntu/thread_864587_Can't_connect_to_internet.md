---
title: "Can't connect to internet"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by skwarp88 on 2008-07-19
I've just install ubunto 8.04.1 desktop 64bit but i cannot connect to the internet i recognises the ethenet but i can't get anything in browser.

I get this from ifconfig in terminal :

richard@richard-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:d8:d4:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:d8:e0:4b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:130 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:22181 (21.6 KB)
          Interrupt:250 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:247120 (241.3 KB)  TX bytes:247120 (241.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0a:fb:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-0A-FB-C4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I am using a orange livebox and works fine on my windows xp

anyone know if they can help me with this?

---

### Post by braddcadd on 2008-07-19
This will ask for an ip address from the terminal.  If you are trying to connected by wire try etho or eth1.  If by wireless, try wlan0.
```

sudo dhclient eth0

```

Have you ever had it working in Ubuntu?

---

### Post by oilchangeguy on 2008-07-19
turn off the power to your modem, wait about a minute and turn the modem back on. during this time also reboot the computer. you should be able to get online.

---

### Post by skwarp88 on 2008-07-19
hey guys thanks for the quick reply

tried rebooting pc and modem still the same

no the internet has never worked on ubuntu

i got this from terminal:

richard@richard-desktop:~$ sudo dhclient eth0
sudo: unable to resolve host richard-desktop
[sudo] password for richard: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:f3:d8:d4:41
Sending on   LPF/eth0/00:18:f3:d8:d4:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



and the same from sudo dhclient eth1

---

### Post by spiderbatdad on 2008-07-19
```
netstat -r
```and wait about 10 seconds. You should see an ip address in the column and row default/gateway. This would be the ip of your router or modem. If there is none, then there is a connectivity problem.

Rebooting the modem or router sounds like a good place to start. Have you tried a wired connection, or are you doing this wirelessly?

---

### Post by skwarp88 on 2008-07-20
i'm using a wired connection.

still dosen't work after resetting modem and enter manual details.

the only other thing i noticed on the network manager is "connect to a 802.1x protected wired network"

is this anything to do with my connection?

---

### Post by zvacet on 2008-07-20
> sudo: unable to resolve host richard-desktop

```
gksudo gedit /etc/hosts
```

first two lines should look like this

127.0.0.1 localhost
127.0.1.1 hostname

hostname= your hostname

If you don´t have second line or it is incorrect add/correct it and save and close file.After that try to establish internet connection.

---

