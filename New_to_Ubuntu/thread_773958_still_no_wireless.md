---
title: "still no wireless"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by smile-its-smiley on 2008-04-29
i have hardy installed and a realtek rtl 8187b wireless card built in. ive tried using windows drivers and it said they installed correctly but i am not able to pick up wireless in the network manager.

---

### Post by Michael.Godawski on 2008-04-29
Can you please post the result of 

```
sudo lshw -C network
```

to check if the drivers are really active.

---

### Post by smile-its-smiley on 2008-04-29
adminaccount@adminaccount-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:9c:c1:e3
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
adminaccount@adminaccount-laptop:~$

---

### Post by pedro_orange on 2008-04-29
> **smile-its-smiley said:**
> adminaccount@adminaccount-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:a0:d1:9c:c1:e3
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
adminaccount@adminaccount-laptop:~$

Looks like an Ethernet driver to me. I would imagine your wireless card is not installed correctly.

Have you tried using ndiswrapper along with the Windows driver?

---

### Post by smile-its-smiley on 2008-04-29
i think so see the screen shot

---

### Post by master5o1 on 2008-04-29
There used to be a bug in *a* realtek wireless driver that meant that you had to blacklist the oss driver somewhere...

Although, I would suggest doing that still to force ndiswrapper over the realtek one... However, I am unsure of how to do it now.

---

### Post by smile-its-smiley on 2008-05-01
thanks for your help ive just successfully got my wireless card working using ndiswrapper and a windows 98 driver i found on [http://members.driverguide.com/driver/detail.php?driverid=1165168](http://members.driverguide.com/driver/detail.php?driverid=1165168) and i simple added
 %RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200 into the .inf files int the following section:
 IDs for 98SE/ME/2K/XP and IDs for X64

---

