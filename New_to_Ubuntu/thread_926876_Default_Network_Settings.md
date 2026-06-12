---
title: "Default Network Settings"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Sunshine1987 on 2008-09-22
I had wireless difficulties at college and a woman at the IT department used the terminal and must have changed some network settings on my computer.  Although I can connect to the web through an ethernet connection, my wireless no longer works and I can no longer see the icon in the upper right corner of the screen.

Is there any way to convert my network settings back to the default settings?

*********************************

iwconfig:
lo        no wireless extensions.

eth4      no wireless extensions.

eth3      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**********************************

ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:13:02:11:1e:3a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 00:50:5b:05:d8:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth4      Link encap:Ethernet  HWaddr 00:19:b9:74:3d:3b  
          inet addr:150.250.246.237  Bcast:150.250.246.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe74:3d3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4707491 (4.4 MB)  TX bytes:486295 (474.8 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43704 (42.6 KB)  TX bytes:43704 (42.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-11-1E-3A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by northern lights on 2008-09-22
Can you post the output of```
sudo lshw -C network
```in addition? Thank you.

---

### Post by Sunshine1987 on 2008-09-22
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:11:1e:3a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth4
       version: 02
       serial: 00:19:b9:74:3d:3b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=150.250.246.237 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth3
       serial: 00:50:5b:05:d8:02
       size: 10MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=half firmware=ASIX AX88772 USB 2.0 Ethernet link=no multicast=yes port=MII speed=10MB/s

---

### Post by northern lights on 2008-09-22
Your wireless device appears to be configured properly. What happens if you run```
iwlist scanning
```

As an aside, it is helpful,for the sake of readability to wrap shell commands, outputs or code in code tags (hash/pound/# button).

---

### Post by Sunshine1987 on 2008-09-22
iwlist scanning
#lo        Interface doesn't support scanning.

eth4      Interface doesn't support scanning.

eth3      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results#

---

