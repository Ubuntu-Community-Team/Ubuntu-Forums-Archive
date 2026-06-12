---
title: "Internet not working anymore..."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by shoaibi on 2008-11-16
I installed ubuntu 8.10 Intrepid Ibex i386 desktop. I was using a USB DSL Router and Internet was working fine, then I did "apt-get autoremove ubuntu-desktop && apt-get install ubuntu-server" (in single user mode) and now in my server, internet is not working, its not even detected as an interface in ifconfig, also tried editing /etc/network/interface, no use... any idea on how to get it working?

---

### Post by pytheas22 on 2008-11-16
What is the output of:
```

lspci -nn
lshw -C Network
```

---

### Post by shoaibi on 2008-11-19
Now i have 3 NICs and DSL router connected on USB Interface.
At bootup i get some error about PXE, and during ubuntu boot i get:

```

Nov 19 22:50:49 nextcube kernel: [   39.186080] PCI: Firmware left 0000:06:02.0 e100 interrupts enabled, disabling
Nov 19 22:50:49 nextcube kernel: [   39.186097] PCI: Firmware left 0000:06:03.0 e100 interrupts enabled, disabling
Nov 19 22:50:49 nextcube kernel: [   40.624091] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Nov 19 22:50:49 nextcube kernel: [   40.624096] e100: Copyright(c) 1999-2006 Intel Corporation
Nov 19 22:50:49 nextcube kernel: [   41.026614] e100: eth1: e100_probe: addr 0xcfa00000, irq 18, MAC addr 00:08:c7:49:d7:97
Nov 19 22:50:49 nextcube kernel: [   41.050340] e100: probe of 0000:06:03.0 failed with error -11
Nov 19 22:50:49 nextcube kernel: [   50.775252] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Nov 19 22:52:19 nextcube kernel: [  152.282169] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex

```

and something about EEPROM being corrupt of some interface. Its related to a NIC, and when i remove it, i get rid of errors, both the PXE one right after BIOS and this EEPROM at ubuntu startup are vanished.

```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:c7:49:d7:97  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe49:d797/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3228 (3.1 KB)  TX bytes:3806 (3.7 KB)

eth2      Link encap:Ethernet  HWaddr 00:0e:50:9d:a8:37  
          inet6 addr: fe80::20e:50ff:fe9d:a837/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10637 (10.3 KB)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

# lshw -C Network
  *-network:0 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 10
       serial: 00:e0:4c:06:22:90
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth0
       version: 05
       serial: 00:08:c7:49:d7:97
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.0.0.1 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth2
       serial: 00:0e:50:9d:a8:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=yes multicast=yes

# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:00.0 Multimedia audio controller [0401]: Yamaha Corporation YMF-724 [1073:0004] (rev 05)
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:02.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 05)
06:03.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 08)

```

Hope this helps...

---

### Post by pytheas22 on 2008-11-19
It looks like 2 of your 3 ethernet interfaces are detected, and you have an IP address on one of them (eth0), so you should be connected to the Internet.  So does that solve your problem?  If not, I think I'm not entirely sure what else you want to do.

The ethernet card that's not being detected is probably the result of a bad EEPROM checksum; this is a known issue with certain cards.  It's easy enough to work around, but I'd need to see the exact error message from dmesg in order to look up what to do (or just put the error message into Google and you should find the solution easily enough...basically you just need to reload the ethernet module with an argument like 'bad_checksum_allow', but I forget the exact syntax).

If you want an IP address on eth2, just run:
```

sudo dhclient eth2
```

(Provided it's connected to a router that serves dynamic IP addresses, of course.)

---

### Post by shoaibi on 2008-11-19
didn't you meas 2 of 4? lspci shows three but lshw shows four as one usb port is acting as a nic.

I did ifconfig eth1 up and i got it in the list:
```

root@nextcube:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:c7:49:d7:97  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe49:d797/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66435848 (63.3 MB)  TX bytes:4395594 (4.1 MB)

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:06:22:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xb800 

eth2      Link encap:Ethernet  HWaddr 00:0e:50:9d:a8:37  
          inet6 addr: fe80::20e:50ff:fe9d:a837/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14728 (14.3 KB)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93968 (91.7 KB)  TX bytes:93968 (91.7 KB)

```

Problem is that USB interface is not coming up, its shown in lshw -C Network though...

```

root@nextcube:~# cat /var/log/dmesg | grep eth
[   40.995413] eth0: RealTek RTL8139 at 0xb800, 00:e0:4c:06:22:90, IRQ 21
[   40.995420] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   41.026614] e100: eth1: e100_probe: addr 0xcfa00000, irq 18, MAC addr 00:08:c7:49:d7:97
[   42.259082] Driver 'sd' needs updating - please use bus_type methods
[   42.259393]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   50.718338] udev: renamed network interface eth1 to eth0
[   50.741126] udev: renamed network interface eth0_rename to eth1
[   50.775252] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   51.119993] eth2: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 00:0e:50:9d:a8:37

root@nextcube:~# cat /var/log/dmesg | grep e1
[   51.120013] usbcore: registered new interface driver cdc_ether
[   39.186080] PCI: Firmware left 0000:06:02.0 e100 interrupts enabled, disabling
[   39.186097] PCI: Firmware left 0000:06:03.0 e100 interrupts enabled, disabling
[   40.624091] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   40.624096] e100: Copyright(c) 1999-2006 Intel Corporation
[   41.026614] e100: eth1: e100_probe: addr 0xcfa00000, irq 18, MAC addr 00:08:c7:49:d7:97
[   41.050240] e100: 0000:06:03.0: e100_eeprom_load: EEPROM corrupted
[   41.050340] e100: probe of 0000:06:03.0 failed with error -11
[   50.775252] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex


```

---

### Post by pytheas22 on 2008-11-19
So your ultimate goal then is to make the USB connection work, right?

I don't see the USB device mentioned in 'lshw -C Network', however.  The 'unclaimed' device is an 'Intel 82557/8/9/0/1 Ethernet Pro 100', which is an ethernet card, as far as I know, and it says that it's in a PCI slot--if it were connected via USB, I don't think it would mention anything under the 'bus info' section.  I'm not sure why there are four entries for ethernet devices, but it's possible that one of them is a virtual interface or something--it actually looks like the last device mentioned in 'lshw -C Network' is probably a virtual interface based on the first one (notice that they both have the same 'physical id' number of 1).

So if you want to get the USB working, that's probably going to be a whole different game than the ethernet stuff.  The first step would be to see the output of:
```

lsusb
```

so that we can look up the PCI ID and see if anyone has written instructions on getting it working in Linux.

---

