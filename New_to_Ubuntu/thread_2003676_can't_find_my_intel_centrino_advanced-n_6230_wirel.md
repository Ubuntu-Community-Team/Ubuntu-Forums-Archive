---
title: "can't find my intel centrino advanced-n 6230 wireless card"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by chaoticmoss on 2012-06-14
Hi guys,

I have wired networking but no luck with my intel centrino advanced-n 6230 wireless card. Any ideas?

My laptop is running Ubuntu 10.04 LTS using Wubi on Windows 7

Thanks for any advice!!
Tom

ps Having read through some forums, here is some information others have asked for:

```

tom@ubuntu:~$ sudo lshw -C network
[sudo] password for tom: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c7400000-c7401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: f0:bf:97:dc:02:ba
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:3000(size=256) memory:c3404000-c3404fff(prefetchable) memory:c3400000-c3403fff(prefetchable)

```

```

tom@ubuntu:~$ sudo modprobe iwlagn
tom@ubuntu:~$ dmesg | grep iwl
[  359.997894] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  359.997895] iwlagn: Copyright(c) 2003-2010 Intel Corporation

```

---

