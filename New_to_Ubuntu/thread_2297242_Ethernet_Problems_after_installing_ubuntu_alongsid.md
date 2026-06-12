---
title: "Ethernet Problems after installing ubuntu alongside windows 8.1 on two different HDD"
date: 2015-10-02
forum: New to Ubuntu
---

### Post by Puneet_Gupta on 2015-10-02
My ethernet adapter is malfunctioning since I have installed ubuntu on a different HDD alongside windows 8.1 . The ethernet adapter sometimes works and sometimes it doesn't when I switch on my PC. If I switch on my PC, and it is not working then I have to switch off the whole power supply and then drain the residual power on the PC by pressing the power button, after which the ethernet adapter starts working 8/10 times. Both the windows and ubuntu loses time when the ethernet adapter is not working on startup. And if I only use one OS then the ethernet adapter is working just fine. Please help me as it is too irritating to keep switching your PC on and off until the ethernet adapter starts working.

---

### Post by cariboo on 2015-10-02
It would help a lot if you told us which version of Ubuntu you are using, and what ethernet adapter and driver you use. To check on the adapter and driver, in a terminal type the following command:

```
sudo lshw -C network
```

the output should look similar to this:

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 09
       serial: e0:3f:49:a4:8d:f7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.0.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
```

In the above output I have bolded the driver my system uses.

---

### Post by Puneet_Gupta on 2015-10-03
Here is the code and I am using ubuntu 14.04.3 LTS :

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: 94:de:80:ff:e5:f3
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **[B]driver=r8169**[/B] driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:27 ioport:d000(size=256) memory:f7800000-f7800fff memory:ea100000-ea103fff

---

