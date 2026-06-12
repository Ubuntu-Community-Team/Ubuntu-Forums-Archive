---
title: "Enable WiFi Sony VGN-NR360 (Hardy 8.04)?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by jjsonp on 2008-07-27
I have tried installing MadWifi without luck, and NDISWrapper as well.

Quite probably I did something wrong in both cases, but in any event I can't get WiFi functioning. The power light on the switch doesn't even come on.

Thanks.

---

### Post by northern lights on 2008-07-27
Can you post the output of ```
sudo lshw -C network
```
Thank you.

---

### Post by jjsonp on 2008-07-27
*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:b9:0f:84
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

When I tried to install MadWiFi I turned off the Atheros Hardware Access Layer if that matters.

---

### Post by jjsonp on 2008-07-28
Bump.

---

### Post by northern lights on 2008-07-29
> **jjsonp said:**
> I tried to install MadWiFiThat's exactly what you need. In Hardy, it should work oob, actually. Do you have 'linux-restricted-modules' installed? If not, do so & retry.

---

### Post by jjsonp on 2008-07-29
Thanks, I will check that when I get home today.

It did not work out of the box...could this be because I am dual-booting? The machine came pre-installed with Vista and I installed Hardy via Wubi.

---

### Post by northern lights on 2008-07-29
> **jjsonp said:**
> It did not work out of the box...could this be because I am dual-booting?
Regular dual booting - no.

> **jjsonp said:**
> I installed Hardy via WubiIt shouldn't either.
It's standalone after all and not a virtual machine.
It residing on a loopmounted drive should not affect hardware drivers.

Actually, since your wireless is working under Windows it probably would if Wubi was a virtual machine...

---

### Post by jjsonp on 2008-07-29
Correct, not running Ubuntu in a VM. 

When I install MadWiFi, do I need to specify the model# of my Atheros card (or chipset?), or will it determine that dynamically?

---

### Post by northern lights on 2008-07-29
> **jjsonp said:**
> Correct, not running Ubuntu in a VMHad read up on it now ;)

> **jjsonp said:**
> When I install MadWiFi, do I need to specify the model# of my Atheros card (or chipset?), or will it determine that dynamically?Nope, no manual specification necessary.

---

