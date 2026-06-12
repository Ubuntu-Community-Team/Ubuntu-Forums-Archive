---
title: "WiFi problems, drivers?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by XabdullahX on 2008-07-25
This is the only reason keeping me away from ubuntu (Currently using vista)

i have an Fujitsu-siemens amilo Pa2548

on ubuntu i have no wireless internet :(
my wlan card is WN6302A
how do i find the drivers?

---

### Post by gimlithedwarf on 2008-07-25
could you open a terminal and post the results of
```
iwconfig
```
```
ifconfig
```
if you have a wifi card:
```
lspci
```
if you have a wifi usb dongle:
```
lsusb
```

---

### Post by XabdullahX on 2008-07-25
```
abdullah@abdullah-laptop:~$ iwconfig
lo        no wireless extensions.

eth6      no wireless extensions.

abdullah@abdullah-laptop:~$ ifconfig
eth6      Link encap:Ethernet  HWaddr 00:00:6C:65:31:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

abdullah@abdullah-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 SATA controller: nVidia Corporation Unknown device 0555 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

---

### Post by germanix on 2008-07-25
[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)
Go to this link and follow the instructions. I battled for months to get wifi to work on Ubuntu, then I read this and in 10 minutes the wifi was running.

---

### Post by XabdullahX on 2008-07-25
Cool! Gonna check it out for sure.

ThX :KS

---

