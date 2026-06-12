---
title: "Can't connect to router via wireless/wired on Ubuntu 16.04"
date: 2017-02-21
forum: New to Ubuntu
---

### Post by royahi on 2017-02-21
As I said in the title, I can't connect to my router on Ubuntu 16.04 but I can connect through Windows 10 (with both Ethernet AND wifi) which I dual boot with. I can also connect from other devices such as my phone and my laptop so I'm assuming that my router isn't the problem.
When I go to 'System Preferences -> Network -> Wired' it says that my cable is unplugged even though it isn't and Ethernet works for Windows. 
I was able to connect to this router before today, but I am no longer able to for some unknown reason. I normally connect via Ethernet but I also tried wifi and that doesn't seem to work too. Ubuntu isn't detecting the router at all. However, I am able to connect to other networks (I am currently posting this from another network), so I am not sure what the problem is. 
I tried some solutions online, but none of them seemed to work. I obviously tried restarting and I tried disabling "Enable Wi-fi" to no avail. I don't know much about linux and networking so I apologize in advance. 

**Some Info**
**lspci**
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller

```

**sudo lshw -c network**
```

  *-network                      description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 60:02:92:b3:3f:3c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:32 ioport:d000(size=256) memory:f0204000-f0204fff memory:f0200000-f0203fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:7
       logical name: wlx6c71d99d6dbf
       serial: 6c:71:d9:9d:6d:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-63-generic firmware=0.29 ip=10.0.0.4 link=yes multicast=yes wireless=IEEE 802.11bgn

```

**ifconfig**
```

enp3s0    Link encap:Ethernet  HWaddr 60:02:92:b3:3f:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:44672 (44.6 KB)  TX bytes:44672 (44.6 KB)


wlx6c71d99d6dbf Link encap:Ethernet  HWaddr 6c:71:d9:9d:6d:bf  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:645:4200:1bb7::a20e/128 Scope:Global
          inet6 addr: fe80::b04f:4f8c:ecd0:90f9/64 Scope:Link
          inet6 addr: 2601:645:4200:1bb7:158:f6fa:7975:3299/64 Scope:Global
          inet6 addr: 2601:645:4200:1bb7:6e71:d9ff:fe9d:6dbf/64 Scope:Global
          inet6 addr: 2601:645:4200:1bb7:9018:ccae:a715:c0cf/64 Scope:Global
          inet6 addr: 2601:645:4200:1bb7:bcd7:fc1e:2ddd:cce1/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8771608 (8.7 MB)  TX bytes:2400214 (2.4 MB)

```

Thank you.

---

### Post by gordintoronto on 2017-02-21
This might help:
[https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

According to your ifconfig, your wireless is connected. It has an IP address, and has sent and received megs of data.

---

### Post by royahi on 2017-02-22
> **gordintoronto said:**
> This might help:
[https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

According to your ifconfig, your wireless is connected. It has an IP address, and has sent and received megs of data.

Thanks, that link worked. All I had to do was download the driver. The problem was that my computer was running the r8169 driver when I was supposed to use r8168.

---

