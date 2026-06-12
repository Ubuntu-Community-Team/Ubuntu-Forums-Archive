---
title: "WiFi Problem, not a driver problem."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by link- on 2008-06-06
Hi,

I'm having problem with the wifi. In college they offer free wireless connection to the internet, I used to connect trough windows OS by using the wireless manager and finding the network signal then I click on connect and then open IE where automatically load the page were I type username and password.

When I used Ubuntu I downloaded and installed wifi radar, I found the network on the list, but when I clicked on connect it don't connect. It pop a window with a message that says requesting IP num. (I think) and then nothing. I opened Mozilla and nothing, no connection. 

Any Idea of what it could be?

Thanks
-link

---

### Post by iaculallad on 2008-06-06
Try enabling/check "Enable Roaming Mode" on your Wireless network settings. System->Administration->Network, On the "Connection" tab, select your Wireless and click on Properties.

---

### Post by link- on 2008-06-06
It was enabled.

---

### Post by iaculallad on 2008-06-06
Try posting whatever comes out:

```
ifconfig
```

```
cat /etc/network/interfaces
```

---

### Post by link- on 2008-06-06
The error is Couldn't acquired IP address

---

### Post by link- on 2008-06-06
eth0      Link encap:Ethernet  HWaddr 00:1d:09:53:67:b6  
          inet addr:206.248.70.114  Bcast:206.248.70.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe53:67b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28767426 (27.4 MB)  TX bytes:1756529 (1.6 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:44:c5:31:c8  
          inet6 addr: fe80::216:44ff:fec5:31c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:292
          TX packets:37 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7363 (7.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80000 (78.1 KB)  TX bytes:80000 (78.1 KB)


auto lo
iface lo inet loopback

---

### Post by iaculallad on 2008-06-06
Strange :confused:

Try to post the output of

```
lshw -C network
```

and 

```
iwlist
```

---

### Post by link- on 2008-06-07
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:53:67:b6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=206.248.70.114 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:c5:31:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation

---

