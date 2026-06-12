---
title: "Ubuntu 8.04 32bit unable to connect to the net"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-05-07
Hi,

I recently installed ubuntu 8.04. I also have xp on the same machine. 

At first, the internet connection was working fine with ubuntu. However, after I mounted my ntfs drives and rebooted, I lost the connection. I tried a few things here and there, but was unable to restore the connection. 

I have cable internet. IP given automatically (dhcp). I use a linksys router. I tried the connection with the router and without it: same results. (note that my connection in xp works just fine, so, it cant be a hardware problem).

Here is some ubuntu info that might help:

```
ali@ali-ubuntu:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Memory:cffc0000-d0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          inet addr:169.254.6.142  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Memory:cffc0000-d0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3872 (3.7 KB)  TX bytes:3872 (3.7 KB) 
```


```
ali@ali-ubuntu:~$ sudo dhclient eth0 
There is already a pid file /var/run/dhclient.pid with pid 6161 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth0/00:1e:8c:9d:27:94 
Sending on   LPF/eth0/00:1e:8c:9d:27:94 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2 
No DHCPOFFERS received. 
No working leases in persistent database &#8211; sleeping. 
```




```
ali@ali-ubuntu:~$ sudo netstat -nr 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0 
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0 

```

Also, here is a copy of my syslog:

[http://nahawand1.googlepages.com/syslogubuntu.odt](http://nahawand1.googlepages.com/syslogubuntu.odt)

or

[http://nahawand1.googlepages.com/syslogubuntu.txt](http://nahawand1.googlepages.com/syslogubuntu.txt)

any help is appreciated!


[COLOR="Red"]EDIT SOLUTION:

Click on system, administrator, network:
Highlight wired connection, click on properties, then select: dhcp
reboot
reset bios settings to default[/COLOR]

---

### Post by superprash2003 on 2008-05-07
go to system->administration->network and click on wired connection(eth0) properties..  and ensure that you have selected DHCP there(it may have been in roaming mode)

---

### Post by newbuntuxx on 2008-05-09
It was on roaming superprash2003, I changed it to dhcp, then rebooted and powered off the modem, router. Still no connection.

Anything else i should do? do you want any specific information?

btw, my network card is:
Atheros L2 Fast Ethernet 10/100 on board

---

### Post by newbuntuxx on 2008-05-09
here is more information after changing the network connection type to dhcp:

```
ali@ali-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:9d:27:94
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair

```

```
ali@ali-ubuntu:~$ sudo dhclient -r eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:8c:9d:27:94
Sending on   LPF/eth0/00:1e:8c:9d:27:94
Sending on   Socket/fallback
```


```
ali@ali-ubuntu:~$ sudo dhclient eht0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eht0: ERROR while getting interface flags: No such device
eht0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


```

---

### Post by hyper_ch on 2008-05-09
post:

```

cat /etc/network/interfaces

```


```

cat /etc/resolv.conf

```

```

ifconfig

```

---

### Post by newbuntuxx on 2008-05-09
Here you go:

```
cat /etc/network/interfaces

ali@ali-ubuntu:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0

```



```
cat /etc/resolv.conf

ali@ali-ubuntu:~$ sudo cat /etc/resolv.conf
search phub.net.cable.rogers.com
nameserver 64.71.255.198

```

```
ifconfig

ali@ali-ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:cffc0000-d0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          inet addr:169.254.6.142  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:cffc0000-d0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4567 (4.4 KB)  TX bytes:4567 (4.4 KB)

```

Also, I noticed the following: 

When I entered network settings (System, administrator, network settings) and clicked on hosts, I noticed everything in the list box has ip6. Could that be causing the problem?

Here is a screenshot of what I saw:

[http://nahawand1.googlepages.com/Screenshot.jpg](http://nahawand1.googlepages.com/Screenshot.jpg)

Also, when I went to: System, Administrator, network tools. On the devices tab, I selected my Ethernet interface (eth0:avahi) and then clicked on configure, I got the following error:

```

The interface does not exist
check that it is correctly typed and that it is correctly supported by your system
```

Here is a screenshot of that:

[http://nahawand1.googlepages.com/Screenshot1.jpg](http://nahawand1.googlepages.com/Screenshot1.jpg)

---

### Post by hyper_ch on 2008-05-09
how do you connect to the net? Through a dsl-modem/router? dial-up?

---

### Post by newbuntuxx on 2008-05-09
I have cable internet. The ip address is assigned automatically. I do not have to use a username and password authentication. I have a link sys router that is connected to my cable modem. The link sys is programmed to assign the ip addresses to the computers connected to it: dynamically (dhpc). I also tried bypassing the link sys and connecting directly to the cable modem. Still not luck.

---

### Post by hyper_ch on 2008-05-09
edit your interfaces file and set this:
```

auto eth0
iface eth0 inet dhcp

```
Instead of the other way around

Then restart the network and post all the stuff asked before:
```

sudo /etc/init.d/networking restart

```

---

### Post by bobbyshafter on 2008-05-09
I am having the same problem
please let us know if that solve the problem

---

### Post by newbuntuxx on 2008-05-09
> **hyper_ch said:**
> edit your interfaces file and set this:
```

auto eth0
iface eth0 inet dhcp

```
Instead of the other way around

Then restart the network and post all the stuff asked before:
```

sudo /etc/init.d/networking restart

```

I did the above, still no connection. Here is the new info, if its new:

```
ali@ali-ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:cffc0000-d0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:9d:27:94  
          inet addr:169.254.6.142  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:cffc0000-d0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6112 (5.9 KB)  TX bytes:6112 (5.9 KB)

```

```
ali@ali-ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:8c:9d:27:94
Sending on   LPF/eth0/00:1e:8c:9d:27:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


```
ali@ali-ubuntu:~$ sudo netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0

```

```
ali@ali-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:9d:27:94
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair

```

```
ali@ali-ubuntu:~$ sudo dhclient -r eth0
There is already a pid file /var/run/dhclient.pid with pid 6026
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:8c:9d:27:94
Sending on   LPF/eth0/00:1e:8c:9d:27:94
Sending on   Socket/fallback

```

```
ali@ali-ubuntu:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback



auto eth0
iface eth0 inet dhcp
```

```

ali@ali-ubuntu:~$ sudo cat /etc/resolv.conf
search phub.net.cable.rogers.com
nameserver 64.71.255.198
```

---

### Post by newbuntuxx on 2008-05-09
any help is appreciated guys

---

### Post by newbuntuxx on 2008-05-09
I want to thank all those who helped me through my ordeal!

I am embarrased to say that the solution to my problem was a simple "reset to defaults" of the bios. After doing so, I rebooted to ubuntu and fired firefox: it worked. 

This was a painful three days for me, and I am sure it was for you. 

thanks everyone!

---

