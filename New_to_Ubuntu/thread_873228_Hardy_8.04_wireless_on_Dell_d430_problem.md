---
title: "Hardy 8.04 wireless on Dell d430 problem"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by CaptSammy on 2008-07-28
I had Gutsy running fine, but decided to install Hardy clean. Unfortunately the wireless now does not work. It lists the networks, but when I try to connect it times out. What happened to Ubuntu, seems to have went backwards in functionality with this release. Anyone know a work around? I install 64bit desktop.

---

### Post by mdw1982 on 2008-07-28
> **CaptSammy said:**
> I had Gutsy running fine, but decided to install Hardy clean. Unfortunately the wireless now does not work. It lists the networks, but when I try to connect it times out. What happened to Ubuntu, seems to have went backwards in functionality with this release. Anyone know a work around? I install 64bit desktop.

Hi Sammy,

I just did my install this morning on a Dell Inspiron 1501 (AMD 64). I had to connect it to the network via ethernet cable in order to download the necessary packages:
- bc-fwcutter
- ndiswrapper

Once that was done I installed **Jockey**:
Hardware Drivers
GNOME user interface and desktop integration for driver management.

That last package made it easy to install the Windows Broadcom drivers for the wireless chipset. (not sure which one you've got on your lappy.)

When that was done I enabled the driver, restarted the machine and connected to the wireless access point.

---

### Post by CaptSammy on 2008-07-28
I would like to find the reason 8.04 dropped support for my card. As a last resort I'll give the ndisdriver a go. I am NOT using any type of security on my wireless and it worked fine in 7.10. Downloading another copy of 7.10 since 8.04 isnt ready for prime time. Output from my system is as follows:


lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:7f:fb:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:02:0c:18
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.27a ip=192.168.2.14 latency=0 module=tg3 multicast=yes

---

### Post by CaptSammy on 2008-07-29
Confirmed, 7.10 works like a charm, even after the massive subsequent update.  If you are running a iwl3945 compatible wireless, and just cant get 8.04 to work with it, upgrade to 7.10.

---

### Post by aklrobin on 2008-07-29
> **CaptSammy said:**
> I would like to find the reason 8.04 dropped support for my card. As a last resort I'll give the ndisdriver a go. I am NOT using any type of security on my wireless and it worked fine in 7.10. Downloading another copy of 7.10 since 8.04 isnt ready for prime time. Output from my system is as follows:


lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:7f:fb:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:02:0c:18
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.27a ip=192.168.2.14 latency=0 module=tg3 multicast=yes

I had the same problem as you initially. But simply download all available updates solved it. I didn't have to do any adjustments. I'm kinda new to Ubuntu, 8.04 is my first try. But my from my experience, IPW3945 will work with 8.04. Restart is recommended after installing the updates.
If you have a hard switch on the laptop that turns wireless on and off, it might pay to flick that a few times. I have a Acer Travelmate 8200, the LED indicator doesn't really come on under Ubuntu, but the switch does work.

---

