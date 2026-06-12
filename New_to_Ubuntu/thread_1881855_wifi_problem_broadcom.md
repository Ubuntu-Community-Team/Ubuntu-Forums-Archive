---
title: "wifi problem broadcom"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by LukaHr on 2011-11-16
I'm on ubuntu 11.10. I restart my pc and wifi not working any more. When i go to System settings/Additional drivers get message " this driver is activated but not in use" for Broadcom STA proprietary wireless driver.

when i go:
```
sudo iwconfig
```get
```
lo        no wireless extensions.
eth0      no wireless extensions.
```used to be wlan0 there to.

when i go
```
sudo lshw -C Network
```get
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:68:75:6e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.21 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d1500000-d1503fff
```I try with
```
gksudo gedit /etc/modules
```and in file add wp
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wp
```but nothing happens with this.
i try to reinstall driver from system settings and from terminal.

---

### Post by LukaHr on 2011-11-16
try with this but didn't work

```
deactivating the STA broadcom driver, and installing the b43-firmware package
```

---

### Post by bkratz on 2011-11-16
First for the STA driver it would have been adding wl not wp in the etc/modules file mentioned in post 1. Secondly, perhaps this may help.

[http://ubuntuforums.org/showpost.php?p=11446022&postcount=2](http://ubuntuforums.org/showpost.php?p=11446022&postcount=2)


to use those directions the first thing would be to install synaptic package manager.

---

### Post by LukaHr on 2011-11-17
i solved in most difficult way, reinstall ubuntu! :) Transfer settings to another hard and copy in new installation! I waste whole day with that wifi and one hour to install it fresh. but now I see that wp/wl might set up things! sucker, hehe!

---

### Post by bkratz on 2011-11-17
> **LukaHr said:**
> i solved in most difficult way, reinstall ubuntu! :) Transfer settings to another hard and copy in new installation! I waste whole day with that wifi and one hour to install it fresh. but now I see that wp/wl might set up things! sucker, hehe!



Well, glad you got it going, enjoy!

---

