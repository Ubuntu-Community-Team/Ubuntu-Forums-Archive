---
title: "Belkin F5D7050 - help please"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by travismoore on 2008-04-28
Hi,
well I installed hardy today and I'm having a little internet issue. To be honest I never quite got my wireless internet working in gutsy either :oops:.

The problem I'm having is that it connects but the speed is painfully slow. I had the same problem in gutsy but it was much harder to even get it to connect so this is some progress :).

These might help i hope:
```
travis@travis-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:11:50:35:F2:24   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=30/100  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
travis@travis-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:11:50:6a:ca:3f  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe6a:ca3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50796 (49.6 KB)  TX bytes:32856 (32.0 KB)

```


I only one problem I can see is the Bit Rate says 11Mbps where as on my use adapter itself it says 54Mbps. This is the same thing it had in gutsy but even if I change it, it still runs slow unfortunately.

If you need me to post any further info please ask.

Any help is appreciated,

Travis

P.S I'm using hardy

---

### Post by travismoore on 2008-04-28
bump

help please :confused:

---

### Post by travismoore on 2008-04-28
lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Unknown device 0183 (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

```

---

