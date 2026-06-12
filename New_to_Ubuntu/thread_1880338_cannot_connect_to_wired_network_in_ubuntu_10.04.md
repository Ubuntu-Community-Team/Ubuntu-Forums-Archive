---
title: "cannot connect to wired network in ubuntu 10.04"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by kiranmatrixlee on 2011-11-13
i installed ubuntu 10.04 via USB.now i cannot get wired network(bsnl broadband).
if manually configure network settins,it shows "connection established" but it cannot ping.
This system is perfectly worked with 10.04 earlier.after install ubuntu via usb,it cannot connect to internet.

---

### Post by dineshs on 2011-11-14
Please post the results of ```
route -n
``````
ping 192.168.1.1 -c3
```and ```
ping 8.8.8.8 -c3
```

---

### Post by kiranmatrixlee on 2011-11-14
please go through the result


```
ak@ak-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
ak@ak-desktop:~$ ping 192.168.1.1 -c3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.30 icmp_seq=1 Destination Host Unreachable
From 192.168.1.30 icmp_seq=2 Destination Host Unreachable
From 192.168.1.30 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
, pipe 3
ak@ak-desktop:~$ ping 8.8.8.8 -c3
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.30 icmp_seq=1 Destination Host Unreachable
From 192.168.1.30 icmp_seq=2 Destination Host Unreachable
From 192.168.1.30 icmp_seq=3 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
, pipe 3
ak@ak-desktop:~$

```

---

### Post by kiranmatrixlee on 2011-11-14
i have got the following result```
ak@ak-desktop:~$ route -n Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0 ak@ak-desktop:~$ ping 192.168.1.1 -c3 PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data. From 192.168.1.30 icmp_seq=1 Destination Host Unreachable From 192.168.1.30 icmp_seq=2 Destination Host Unreachable From 192.168.1.30 icmp_seq=3 Destination Host Unreachable  --- 192.168.1.1 ping statistics --- 3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms , pipe 3 ak@ak-desktop:~$ ping 8.8.8.8 -c3 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. From 192.168.1.30 icmp_seq=1 Destination Host Unreachable From 192.168.1.30 icmp_seq=2 Destination Host Unreachable From 192.168.1.30 icmp_seq=3 Destination Host Unreachable  --- 8.8.8.8 ping statistics --- 3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms , pipe 3 ak@ak-desktop:~$
```

---

### Post by dineshs on 2011-11-15
Pl post results of```
sudo lshw -C network
```and```
cat /etc/network/interfaces
```

---

### Post by kiranmatrixlee on 2011-11-15
result of the above post

```
ak@ak-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 10
       serial: 00:16:76:c4:29:66
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.30 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:b800(size=256) memory:ff8ffc00-ff8ffcff
ak@ak-desktop:~$ sudo cat /etc/network/interfaces 
auto lo
iface lo inet loopback

ak@ak-desktop:~$ 

```all the above  results  are working with the configuration shown below

[http://imagebin.org/184183]("http://imagebin.org/index.php?mode=image&id=184183")
[IMG]http://imagebin.org/index.php?mode=image&id=184183[/IMG]




auto eth0 is not working. i.e it is not connected.connection established by manual configuration.

---

### Post by kiranmatrixlee on 2011-11-16
> **dineshs said:**
> Pl post results of```
sudo lshw -C network
```and```
cat /etc/network/interfaces
```
please evaluate my result which is posted above

---

### Post by dineshs on 2011-11-16
The results look OK .
Please run ```
sudo dhclient eth0
```and post the result.Also see if you can browse.
Can you try a live CD and see if the connection is working?
Do you have windows installed?Is the connection OK in windows?

---

### Post by kiranmatrixlee on 2011-11-16
after sudo dhclient eth0



```
ak@ak-desktop:~$ sudo dhclient eth0 
There is already a pid file /var/run/dhclient.pid with pid 1543
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:16:76:c4:29:66
Sending on   LPF/eth0/00:16:76:c4:29:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ak@ak-desktop:~$

```


i have no optical drives with my system.And now only ubuntu in my system which is installed via USB.i have no more choices now.

the connection is ok with another pc (in linux and windows).

---

### Post by dineshs on 2011-11-17
> the connection is ok with another pc (in linux and windows).Means your modem is OK.
Sorry to say I am helpless.

---

### Post by kiranmatrixlee on 2011-11-18
Thank u for your help and support.

---

