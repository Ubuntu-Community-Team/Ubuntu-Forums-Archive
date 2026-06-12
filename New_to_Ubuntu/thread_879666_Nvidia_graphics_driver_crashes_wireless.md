---
title: "Nvidia graphics driver crashes wireless"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by tsunamiwarrior on 2008-08-04
I am running xubuntu and i am new to it. I opened the hardware devices panel, and i had to install a grapics driver for my nvidia card. Once i restarted the computer, my wireless crashed. I disabled the driver so that i would have wireless but i still cant install it. Any help?

---

### Post by FTBPrimeEvil on 2008-08-04
Perhaps you can give more info on your issues!
From the terminal type: lspci
Also do a cat on your /etc/X11/xorg.conf
And post all info.

---

### Post by northern lights on 2008-08-04
> **FTBPrimeEvil said:**
> From the terminal type: lspci
Could we possibly make that```
sudo lshw -C display
```Thank you.

Further, are you certain the wireless malfunctioning and the graphics driver are related? This seems very odd.

As for the wireless, can you post the output of ```
sudo lshw -C network && iwconfig
```Preferably when malfunctioning.

---

### Post by ranger5664 on 2008-08-08
*-network:0             
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:86:d8:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.139 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 00
       serial: 00:60:08:8d:cf:e1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=10MB/s
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Mad Dog"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:56:AC:45   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=81/100  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thats the output that u asked for.

---

