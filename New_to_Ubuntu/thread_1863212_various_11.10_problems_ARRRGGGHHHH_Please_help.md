---
title: "various 11.10 problems: ARRRGGGHHHH Please help"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by mdm27 on 2011-10-17
Hi all

I could really do with some help, as I'm pulling my hair out with problems with 11.10. Its getting so bad, I'm struggling to see how I can carry on using Ubuntu.

I'm using a Samsung N-140 netbook. 

The first problem is the wireless. When I first installed, it was working fine and connected automatically when I turned on the netbook. However, it now simply cannot connect. I have tried restarting, but nothing works. I cannot get online at all. My wifi box is fine (using it now on my other computer)

Secondly, I can't use my mobile broadband dongle. When I put it in the USB, its not registered or recognised. When I was using 10.4 it used to recognise the dongle in the connections menu at the top of the screen, but now there is nothing, its like the dongle isn't recognised. 

If someone could help me, I'd be really grateful. 

Please keep it simple, if possible!

Thanks for your time

---

### Post by TeoBigusGeekus on 2011-10-17
Can you post us the output of
```
sudo lshw -C network
```
and
```
ifconfig
```
?

---

### Post by mdm27 on 2011-10-17
the output for the first one was:

matthew@matthew-N140:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:54:47:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE ip=192.168.1.4 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:16:92:1c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff
matthew@matthew-N140:~$ 



The output for the second one was:

matthew@matthew-N140:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:54:16:92:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5616 (5.6 KB)  TX bytes:5616 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:54:47:a8  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe54:47a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f8060000-f8060100

---

### Post by TeoBigusGeekus on 2011-10-17
Your wireless card is recognized and your wireless interface seems up and running.
Have you checked all your setting in Network Connections?
Try removing the wifi connection and adding it again.

---

### Post by mdm27 on 2011-10-17
could it have something to do with the fact that the wireless is currently working? If I close the lid of my netbook it will cut off and won't reconnect.

I will try the suggestion. Thanks

---

### Post by roger_1960 on 2011-10-17
Hi

try

> rfkill unblock all

---

### Post by mdm27 on 2011-10-17
I've just closed my netbook screen and opened it. My wireless has gone and I cannot reconnect. 

In terminal, I typed sudo lshw C- network again, and it now says "network DISABLED"

---

### Post by mdm27 on 2011-10-17
> **roger_1960 said:**
> Hi

try

Do I type this into the terminal?


Thanks

---

### Post by TeoBigusGeekus on 2011-10-17
So the problem is narrowed to "wireless gone after suspend/hibernate" or something.
I don't know about it as I don't use ubuntu, but, until you find a more permanent fix, you could set your machine not to suspend or hibernate from the power management app.

---

### Post by roger_1960 on 2011-10-17
Hi again

Yes, type

> rfkill unblock all 

in terminal.

Not sure if this will work, but might and won't harm.

---

