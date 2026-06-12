---
title: "Xubuntu 11.10 and Agere ORiNOCO IEEE 802.11b wireless"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by thepreacherswife on 2012-03-03
Hello all,

I just installed Xubuntu 11.10 on a Gateway 600YGR.  It has an Agere ORiNOCO IEEE 802.11b wireless card installed in a mini PCI slot, I believe. Our router is an Apple Airport Extreme with WPA2 and MAC filtering set up.  I tried the wireless through Win XP on the machine and was able to connect.

Before installing, when I tried booting with the live CD, the network manager recognized my broadcast SSID, but when I entered the password I got no connection.  I tried disabling the password and still no go.

I went ahead with the install and used a wired connection to get updates.  Reading some advice in another thread I installed pcmciautils, installed Wicd and uninstalled network manager, then rebooted.  Still no go with the wireless, so I plugged the wired connection back in.  Now Wicd shows no wireless networks available, even after unplugging the cable.

Here's what I get currently when I run iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"4942harding"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1E:52:78:3D:43   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-37 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:892
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0
```and lshw -C network:
```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:e0:b8:53:3b:13
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=10.0.1.10 latency=66 maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 memory:e8207000-e8207fff ioport:5c00(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:6f:10:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=3.0.0-16-generic firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```and ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:53:3b:13  
          inet addr:10.0.1.10  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe53:3b13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24930177 (24.9 MB)  TX bytes:3908044 (3.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:6f:10:07  
          inet6 addr: fe80::202:2dff:fe6f:1007/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:25 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358985 (358.9 KB)  TX bytes:29935 (29.9 KB)
          Interrupt:10 Base address:0x4100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)
```Any suggestions?

---

### Post by thepreacherswife on 2012-03-03
Quick correction / update: I can connect with the WPA2 disabled (unsecured).  Apparently I hadn't tried that earlier.  So it seems to be a WPA2 personal issue with the wireless.

edit: The orinoco driver doesn't support WPA2.  So looks like I'm in the market for a wireless nic.  At least I can bump up to g or n from 802.11b.

---

