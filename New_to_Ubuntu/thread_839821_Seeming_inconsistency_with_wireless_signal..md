---
title: "Seeming inconsistency with wireless signal."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Vinylcake on 2008-06-24
'Ello one, 'ello all.

Just put Ubuntu 8.04 on my lovely computer-box here, but was disappointed at my lack of ability to connect to my wireless network.  Today I snagged the 100-foot ethernet cable from my brother's room just to get online.  Anyway, after an automatic driver update (using ethernet) and a restart, I was finally able to seemingly connect to the wireless network.

The network utility icon on the taskbar shows that I'm connected to the network with about 2.5 out of the 6 graphical bars filled.  This measurement fluctuates slightly like any wireless network would.  However, when I disconnect the from the wired network, I can't connect to the internet.  Also, hovering over the network icon in the taskbar yields a message stating I have 0% connectivity, but clicking on it reveals the same 2 and a half orange bars next to the network name.  The selection-bubble next to the network is indeed checked, so I really can't make of what the problem could be.

Any help would truly be appreciated!  :D

---

### Post by RomeReactor on 2008-06-24
Hi. With the ethernet cable connected, go to 'System->Administration->Hardware Drivers' and see if you get an entry for your wireless card.

We need to know which wireless card you have: please open a terminal (Applications->Accessories->Terminal), paste the following:
```
lspci
```
then press ENTER, and post the output. Also post the output of this (it will ask for your password):
```
sudo lshw -C network
```

---

### Post by Vinylcake on 2008-06-24
Hardware Drivers lists a Broadcom B43 Wireless Driver, Enabled, and In Use.  :O

In: lspci
Out: ```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

In: sudo lshw -C network
Out: ```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:a9:84:75
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.111 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:65:b8:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

:D

---

### Post by RomeReactor on 2008-06-24
Is the router using encryption? If so, turn it off and see if you can connect then. Have you tried setting the wireless card in 'Roaming' mode in Network Manager?

Please post the output of:
```
sudo iwlist scanning
```
```
iwconfig
```
and
```
ifconfig
```

---

### Post by Vinylcake on 2008-06-24
No encryption.  And yup, it's already on Roaming.

In: Sudo iwlist scanning
Out: ```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:30:6E:54
                    ESSID:"Amaral"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/100  Signal level=-80 dBm  Noise level=-73 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000400805e9184
```

In: iwconfig
Out: ```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:30:6E:54   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

In: ifconfig
Out: ```
eth0      Link encap:Ethernet  HWaddr 00:40:ca:a9:84:75  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fea9:8475/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24234280 (23.1 MB)  TX bytes:1763831 (1.6 MB)
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65087 (63.5 KB)  TX bytes:65087 (63.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:41:65:b8:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-41-65-B8-47-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Vinylcake on 2008-06-25
After restarting with the ethernet cable not in place, I found I was unable to connect at all to the wireless network.  Clicking on the said network in the network manager(?) icon in the task bar would leave said icon in the in an "attempting to join wireless network" state for a while, but would just revert back to "No network connection".  :/  I wonder if that's a step down from the former 0% connectivity.  :P

/Sigh at being such a beginner.

---

### Post by RomeReactor on 2008-06-25
It may be that Network Manager is having trouble with your card; you can install [WICD]("http://wicd.sourceforge.net/") (note: it will remove Network Manager, but it does work better with some cards). You can get it directly [from here]("http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0"); if it works for you, you can add the repository later, so it will be kept up to date. Another possible solution: as the card is using the **b43-fwcutter** driver, try removing it and [install bcm43xx-fwcutter]("http://ubuntuforums.org/showthread.php?t=735444").

---

