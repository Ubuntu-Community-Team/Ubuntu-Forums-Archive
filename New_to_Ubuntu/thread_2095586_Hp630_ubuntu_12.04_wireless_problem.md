---
title: "Hp630 ubuntu 12.04 wireless problem"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by MarcoFenaroli on 2012-12-17
Hi,

I've installed Ubuntu 12.04 few days ago. Now I've problem with my wireless (previously had functioned). 
Can you help me please?

Thank's

---

### Post by GordThompson on 2012-12-17
Please run the following command in a Terminal window and tell us what it says.

```
nm-tool
```

---

### Post by MarcoFenaroli on 2012-12-17
NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        B4:B5:2F:32:5C:E9

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.21.190.170
    Prefix:          16 (255.255.0.0)
    Gateway:         10.21.0.1

    DNS:             192.167.20.238
    DNS:             192.167.20.239

---

### Post by GordThompson on 2012-12-17
Hmm. Your wireless adapter doesn't show up in there at all. Please show us the output from

```
sudo lshw -class network
```

---

### Post by MarcoFenaroli on 2012-12-17
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: b4:b5:2f:32:5c:e9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.21.190.170 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c250ffff

---

### Post by GordThompson on 2012-12-17
Okay, your wireless adapter is there but is not being claimed by any drivers. First, try loading any "Additional Drivers" using the instructions here:

[http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)

(If a wireless adapter driver appears in the list then click the "Activate" button.) 

Post back here and let us know how it went.

---

### Post by MarcoFenaroli on 2012-12-17
It returns:

No proprietary drivers era in use on this system.

---

### Post by GordThompson on 2012-12-17
> **MarcoFenaroli said:**
> It returns:

No proprietary drivers era in use on this system.
...and it doesn't show you any drivers that you could activate?

(And, just to clarify, are you posting from that same machine via the wired network connection?)

---

### Post by MarcoFenaroli on 2012-12-17
> **GordThompson said:**
> ...and it doesn't show you any drivers that you could activate?

No driver is shown

> **GordThompson said:**
> 
(And, just to clarify, are you posting from that same machine via the wired network connection?)

exactly

---

### Post by GordThompson on 2012-12-17
Please post your kernel version displayed by the command

```
uname -r
```

---

### Post by MarcoFenaroli on 2012-12-17
3.2.0-34-generic-pae

---

### Post by GordThompson on 2012-12-17
Okay, let's try installing the backport package and see if it has anything for you:

First, do...

```
sudo apt-get update
```...followed by...

```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```When that's done, restart your machine. If your wireless adapter is still unrecognized, try the "Additional Drivers" applet again.

Let us know how it goes!

---

