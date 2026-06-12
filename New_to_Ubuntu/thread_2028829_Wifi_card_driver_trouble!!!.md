---
title: "Wifi card driver trouble!!!"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by abissel22 on 2012-07-18
i have installed Backtrack 5 r2 (GNOME) on my toshiba satellite p855-s5200..
 
I have little experience with the command line other than running a server however this time i am clueless. i have no idea what wifi card i have and what drivers i need to get my wireless networking working with backtrack. please help!

---

### Post by anewguy on 2012-07-19
Post back the results of these commands from a terminal window:

lshw -C network

lsusb

lspci

---

### Post by abissel22 on 2012-07-19
> **anewguy said:**
> Post back the results of these commands from a terminal window:

lshw -C network

lsusb

lspci

  root@bt:~# lshw -C network   *-network                       description: Ethernet interface        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0        bus info: pci@0000:01:00.0        logical name: eth0        version: 05        serial: b8:88:e3:14:70:17        size: 100MB/s        capacity: 100MB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s        resources: irq:42 ioport:e000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff   *-network UNCLAIMED        description: Network controller        product: Intel Corporation        vendor: Intel Corporation        physical id: 0        bus info: pci@0000:02:00.0        version: c4        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress cap_list        configuration: latency=0        resources: memory:f7e00000-f7e01fff root@bt:~#    root@bt:~# lsusb Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd  Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub    root@bt:~# lspci 00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09) 00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09) 00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) 00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04) 00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) 00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04) 00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) 00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4) 00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4) 00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) 00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04) 00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04) 00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04) 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 02:00.0 Network controller: Intel Corporation Device 0890 (rev c4) 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)   okay, these are the commanads,

---

### Post by anewguy on 2012-07-19
I took your reply and broke into the appropriate lines (it's just the newline differences between linux and windows):

```
root@bt:~# lshw -C network 
*-network description: Ethernet interface product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
 vendor: Realtek Semiconductor Co., Ltd.
 physical id: 0
 bus info: pci@0000:01:00.0
 logical name: eth0 version: 05
 serial: b8:88:e3:14:70:17
 size: 100MB/s capacity: 100MB/s
 width: 64 bits
 clock: 33MHz 
 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes
 driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
 resources: irq:42
 ioport:e000(size=256)
 memory:f0a04000-f0a04fff
 memory:f0a00000-f0a03fff
 *-network UNCLAIMED description: Network controller
 product: Intel Corporation
 vendor: Intel Corporation
 physical id: 0
 bus info: pci@0000:02:00.0
 version: c4
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress cap_list
 configuration: latency=0
 resources: memory:f7e00000-f7e01fff

 root@bt:~# root@bt:~# lsusb
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root

 hub root@bt:~# lspci
 00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
 00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)
 00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
 00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
 00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
 00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
 00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
 00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
 00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
 00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
 00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
 00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04)
 00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
 02:00.0 Network controller: Intel Corporation Device 0890 (rev c4)
 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01) 


```

The 2nd to last entry:  

02:00.0 Network controller: Intel Corporation Device 0890 (rev c4)

appears to be your wireless controller.

I personally don't know anything about this controller, but from the net it appears to be a new wireless "n" adapter.

I tried searching launchpad for any bug reports but didn't find any (perhaps my search was wrong).  I've seen bug reports for (I think) the 0880, but didn't see any for the 0890.  If you can temporarily hard-wire a connection to the router perhaps you can try additional drivers and see if anything turns up.  It may just be a module that needs to be modprobe'd, but I wouldn't know which one.

Perhaps someone like Wildmanne39 or chili555 might be able to help you a lot better than I can.  I'm sure they'll be around to check this thread.

Sorry I couldn't be of more help.

---

### Post by NikTh on 2012-07-19
Hi , 
open a terminal and copy-paste these commands (from here to your terminal, one at time.) 
```
cat /etc/network/interfaces
rfkill list all
```Post the results back here .
**Put the results inside [CODE] tags , by highlighting the text and click at [SIZE=3]#[/SIZE] symbol on top of message pane.**
Thanks

---

