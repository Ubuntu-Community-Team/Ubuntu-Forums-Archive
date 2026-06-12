---
title: "Internet connection dropping periodically"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by vineetkr on 2008-11-10
I am using Ubuntu 8.04.1
The problem is that my internet goes down and reconnects at regular time*intervals. Any remedy ??

---

### Post by quirks on 2008-11-10
Please explain your problem in more detail.

What are the time intervals?
Is there a router inbetween your PC and the Internet?
If yes, is the Internet "gone" or only the connection between your PC and the router?
Do you use static IPs or DHCP?
Do you use wireless or wired LAN?
Does this problem occur in Ubuntu only, or did you observe this behaviour with other OSs as well?

Feel free to ask, if you have problems understanding any of the above questions.

---

### Post by vineetkr on 2008-11-27
This problem in ubuntu only, my internet connection on windows works fine, i use desktop pc and a DSL connection.

---

### Post by Michael.Godawski on 2008-11-27
Can you please post the outputs of these terminal commands?

```
sudo iwlist scan
iwconfig
ifconfig
sudo lshw -C network
```

---

### Post by theozzlives on 2008-11-27
are the connection lights on on your modem when this happens?

---

### Post by vineetkr on 2008-12-01
**sudo iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp1      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ppp1      no wireless extensions.

ppp0      no wireless extensions.

**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:14:85:94:ee:83  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe94:ee83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3490561 (3.3 MB)  TX bytes:931475 (909.6 KB)
          Interrupt:20 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57749 (56.3 KB)  TX bytes:57749 (56.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.94.131.163  P-t-P:59.94.128.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:489094 (477.6 KB)  TX bytes:105088 (102.6 KB)


**sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:14:85:94:ee:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by mapes12 on 2008-12-01
Try WICD instead of Network Manager. Here's a success story thread: [http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815) It also works for wired networks.

---

