---
title: "no wired network connection"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by DanMartin65 on 2011-11-17
Hi, am new to ubuntu and have just clean installed 10.04. There is no wired network connection. The info I've got so far is reproduced below. Any help greatly appreciated. Thanks

dan@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0

dan@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fe500000-fe51ffff memory:fe527000-fe527fff ioport:f060(size=32)
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: c8:3a:35:d5:90:6f
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:16 ioport:e000(size=256) memory:fe420000-fe4200ff memory:fe400000-fe41ffff(prefetchable)

dan@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

dan@ubuntu:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 1800
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/c8:3a:35:d5:90:6f
Sending on   LPF/eth0/c8:3a:35:d5:90:6f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dan@ubuntu:~$

---

### Post by Sealbhach on 2011-11-17
```

dan@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

This doesn't look right, normally you would have "auto eth0" in there as well. Using the Network Manager, add an interface for eth0 and set it to connect automatically with DHCP.

Then run 

```
sudo service network-manager restart
```

.

---

### Post by 3rdalbum on 2011-11-17
If you're new to Ubuntu, why not try using a more recent version such as 11.10? If you run up against bugs in 10.04 they might actually have been fixed in a later version.

---

### Post by LowSky on 2011-11-17
> **3rdalbum said:**
> If you're new to Ubuntu, why not try using a more recent version such as 11.10? If you run up against bugs in 10.04 they might actually have been fixed in a later version.
did you stop to think that maybe, just maybe they are using an LTS for another reason. maybe they hate unity.. just thinking.


from the result i'm seeing from the original post, looks like the router or switch is the issue. it's spitting out a network address not commonly seen, so I can only guess its not a common household setup. The router might use static addresses, and one may need to set that by hand from a machine already on the network.

Many places like colleges and business use static addresses to keep machines unknown off the network. Many schools require installing software to grant access, and many businesses add computers by MAC address so that they can connect from any open point but still keep the same address which helps if the network uses counter measures to record online traffic or to grant access to certain areas without the use of additional passwords.

---

### Post by DanMartin65 on 2011-11-17
Thanks for the response. Network Manager already has an auto eth0 entry but it's all blank. Please attached screenshots. I've tried 11.10 and that works but I don't like the desktop as much as 10.04!

---

### Post by DanMartin65 on 2011-11-17
the network and router is standard and hands out dynamic addresses. it can see the ubuntu machine and has allocated 192.168.0.15 to it but has it's status as Inactive.

---

### Post by carranty on 2011-11-17
> **3rdalbum said:**
> If you're new to Ubuntu, why not try using a more recent version such as 11.10? If you run up against bugs in 10.04 they might actually have been fixed in a later version.

If someone is new to Ubuntu, surely using an older LTS release (which has had over a year to have all its bugs worked out) is a better option than a brand new release that even experienced users are having trouble with??


```
Thanks for the response. Network Manager already has an auto eth0 entry  but it's all blank. Please attached screenshots. I've tried 11.10 and  that works but I don't like the desktop as much as 10.04!     
```The network manager's eth0 entry shouldn't be blank, does it specify a MAC address?  This might be the problem.  Can you run
```

ifconfig
```from the terminal, It should display your MAC address (amongst other things)

EDIT : Nevermind, I misread your post, its just the ipv4 settings tab that's blank is it, mines blank too, so I think that's normal. Please still post the output of ifconfig, it might help.

---

### Post by DanMartin65 on 2011-11-17
Thanks again. output from ifconfig as follows

dan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:3a:35:d5:90:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

---

### Post by carranty on 2011-11-17
You say your router can see your computer and has allocated it an IP, if that were the case I'd expect so see it listed in the above output but I don't. Can you ping your router?  Just enter the command
```

ping 192.168.0.1
```into a terminal (I assume 192.168.0.1 is your routers IP address).

Do you have a firewall running?

*sudo ufw status*

---

### Post by DanMartin65 on 2011-11-17
am sorry, the info re the router was incorrect...the router cannot see the machine...pinging anything gives "network is unreachable". There is no network traffic at all going through the interface and both lights on the jack socket are on continuously.

The firewall is set to allow all lan traffic.

---

### Post by carranty on 2011-11-17
I'm sorry but I don't know.  All your outputs look similar to mine, and mine is working.  Are you absolutely certain it isn't the router?  Have you tried plugging something else into it and seeing if that can connect to the internet?

---

### Post by DanMartin65 on 2011-11-18
am pretty certain it's not the router. I did a dual install with 11.10 last night and the network works fine. There are other computers (pc's and mac) on the same network which all work properly. Guess, I'll just have to use 11.10.Thanks for your help all the same.

---

