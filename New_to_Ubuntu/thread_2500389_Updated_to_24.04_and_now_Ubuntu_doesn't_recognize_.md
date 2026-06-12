---
title: "Updated to 24.04 and now Ubuntu doesn't recognize Wi-Fi adapter...(Updated info!)"
date: 2024-08-31
forum: New to Ubuntu
---

### Post by yatski on 2024-08-31
(Yes, it's me again..)

This problem appeared today during heavy thunderstorm when I decided to share wi-fi hotspot from my Huawei phone with this laptop(old Sony Vaio) so I could access Internet...

Except it doesn't work."No Wi-Fi adapter found". 
Bluetooth(very slow) seems to be only option.


I fear this will cause problems when I travel to my parents place, since wi-fi is there only option to connect into Internet.

I've tried to search help using Google, but came short of anything helpful.(ie. despite [https://www.makeuseof.com/fix-ubuntu-no-wifi-adapter-found-error/](https://www.makeuseof.com/fix-ubuntu-no-wifi-adapter-found-error/) I can't find wi-fi adapter drivers..)

- **lshw** is installed
```
 heta@heta-vaio:~$ sudo lshw -C network
[sudo] password for heta: 
  *-network UNCLAIMED       
       description: Network controller
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b7000000-b7001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 07
       serial: 30:f9:ed:f1:70:6a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-47-generic duplex=full ip=192.168.100.10 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 ioport:3000(size=256) memory:b5004000-b5004fff memory:b5000000-b5003fff
```

**lspci**
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M LE] (rev a1)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 07)

```

**lsusb**
```
heta@heta-vaio:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 08ff:168f AuthenTec, Inc. AES1660 Fingerprint Sensor
Bus 001 Device 004: ID 1bcf:2c08 Sunplus Innovation Technology Inc. USB2.0 Camera
Bus 001 Device 005: ID 12d1:14f1 Huawei Technologies Co., Ltd. Gobi 3000 HSPA+ Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c542 Logitech, Inc. M185 compact wireless mouse
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

(It lists Huawei modem, yet no additional drivers are found.)

Also **iwconfig**
```

lo        no wireless extensions.

enp4s0    no wireless extensions.

```

(This was solved elsewhere and reason turned to be outdated kernel. Please check it's updated!)

---

