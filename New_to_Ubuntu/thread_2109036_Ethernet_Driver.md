---
title: "Ethernet Driver"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by iJordan on 2013-01-26
Hello! Can someone send me the link for my ethernet driver and explain me how to configure my network. :confused: Here are my outputs:

lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 630M] (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 08)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)


```ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112560 (112.5 KB)  TX bytes:112560 (112.5 KB)

wlan0     Link encap:Ethernet  HWaddr cc:af:78:78:56:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```Thanks!

---

### Post by oldos2er on 2013-01-26
Post moved to its own thread.

---

### Post by Cheesehead on 2013-01-26
Here is how others solved the same problem: 
[http://askubuntu.com/questions/205582/how-do-i-get-an-atheros-ar8162-working](http://askubuntu.com/questions/205582/how-do-i-get-an-atheros-ar8162-working)
[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)

---

### Post by Rifester on 2013-01-26
[http://ubuntuforums.org/showthread.php?t=2041219]("http://ubuntuforums.org/showthread.php?t=2041219")

---

