---
title: "lost wireless networks after updating, how can I fix it?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by gumpontheweb on 2008-05-11
after updating I lost my list of wireless connections. I have made sure everything is enabled.  Nothing simple I am overlooking. I checked and unchecked everything. I went through the help and troubleshooting and cant figure anything out! My guess is the part of the program that finds wireless routers is broken. I don't have a clue how to fix this. Another old program for finding networks found some but couldn't connect to them.
I think my hardware is recognized so here is the rest of the troubleshooting if this is helpful.
```
zeus@the-laptop:~$ sudo lshw -C network
[sudo] password for zeus: 
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:20:73:c1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. ip=192.168.0.101 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:bd:28:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

```

```
zeus@the-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"M"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:40:05:30:73:4D   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
zeus@the-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"M"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:40:05:30:73:4D   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zeus@the-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:bd:28:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:20:73:c1  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe20:73c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2940156 (2.8 MB)  TX bytes:521240 (509.0 KB)
          Interrupt:17 Memory:50000000-50004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I hope that helps some...

---

### Post by shifty_powers on 2008-05-11
try

```
sudo /etc/init.d/networking restart
```

---

### Post by gumpontheweb on 2008-05-11
I see all the other people who have had the same problem! I just cant find the solution!

> **shifty_powers said:**
> try

```
sudo /etc/init.d/networking restart
```

would I have to do that on every startup?
I pressed esc before boot yo revert to the earlier version to get to the web so I would have to re-start and try. Should I restart and try it or is it something I can I do without restarting?
thanks for the quick help!

---

### Post by shifty_powers on 2008-05-11
heh just go applications>accesories>terminal

and type in the command. It should restart your networking and then we can take it from there ;)

---

### Post by gumpontheweb on 2008-05-17
NOPE, not working still.
I have other concerns so I will make another post

---

