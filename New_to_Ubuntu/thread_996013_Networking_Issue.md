---
title: "Networking Issue"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Celauran on 2008-11-28
Not sure how long this has been an issue as I generally plug in my ethernet at 9 and leave it in until 5. Today, however, I had to unplug from the network to configure a modem for someone. Could not establish a connection to the modem. Thinking it might be the modem itself, I tried two others with the same results. I tried reconnecting to the office network, that wouldn't work either. I rebooted and was able to connect to the office network no problem. Unplug the ethernet cable then plug it back in, again no connection.

No idea where to even start looking, so any help is much appreciated.

Using Ubuntu 8.10 on my Toshiba A50.

---

### Post by Michael.Godawski on 2008-11-28
> I rebooted and was able to connect to the office network no problem. Unplug the Ethernet cable then plug it back in, again no connection.

After the reboot your Ethernet connection works without a glitch, but when you unplug and re-plug :) the connection is lost till the next reboot?

Can you please post the output from 
```

lspci | grep Ethernet
sudo lshw -C network
iwconfig
```

---

### Post by Celauran on 2008-11-28
> **Michael.Godawski said:**
> After the reboot your Ethernet connection works without a glitch, but when you unplug and re-plug :) the connection is lost till the next reboot?
Precisely

> **Michael.Godawski said:**
> Can you please post the output from 
```

lspci | grep Ethernet
sudo lshw -C network
iwconfig
```


lspci | grep Ethernet
```
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
```


sudo lshw -C network
```
  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:8a:f4:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:2c:ef:2b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A ip=10.0.0.14 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:5f:d0:e1:9d:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

