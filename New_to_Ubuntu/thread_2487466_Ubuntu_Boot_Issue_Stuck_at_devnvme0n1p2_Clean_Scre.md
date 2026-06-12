---
title: "Ubuntu Boot Issue: Stuck at /dev/nvme0n1p2: Clean Screen with Bluetooth Error"
date: 2023-06-06
forum: New to Ubuntu
---

### Post by terdes on 2023-06-06
I'm a beginner with Ubuntu. I installed Ubuntu from a USB, and initially, it boots up fine.

However, after some time passes and I try to restart or shut down and start again, the following screen appears, and it doesn't work after that: 
/dev/nvme0n1p2: clean, .../...files, .../...blocks
Bluetooth: malformed MSFT vendor event: 0x02 

No matter how many times I try, I end up with this screen and cannot restart.
I have repeated the process of reinstalling from the USB about four times already.

I searched the internet and tried things like "sudo apt-get update," but it didn't work.
At first, I thought it might be a problem with the Bluetooth settings, so I also tried a pattern without using Bluetooth, but it gets stuck at the same screen. 

I'm tired of building the environment from scratch (though thanks to that, I've gotten a bit used to operating Ubuntu), so if anyone knows the cause, I would appreciate it if you could let me know. 

I'm using the following PC:
Ubuntu 22.04 LTS
CPU: Core i7 13700 BOX (1700/2.1G/30M/C16/T24)
Motherboard: MAG Z790 TOMAHAWK WIFI DDR4 (Z790 ATX DDR4)
Memory: CT2K16G4DFRA32A (DDR4 PC4-25600 16GBx2)
SSD: SN850X WDS100T2X0E (M.2Gen4 1TB)
GPU: NED407T019K9-1043A (RTX4070Ti GamingPro 12G)
Power Supply: TUF-GAMING-850G (ATX 850W80+G)
Case: DEEPCOOL CH510 (E-ATX Glass No Power Supply Black)
Cooler: AK620 (1150-2066 AM2-4 FM1-2+)
Fan: FK120-3 IN 1 (120mm PWM 3PK)
Thermal Grease: OC Master 1g SMZ-01R-01 (High-end) 

Thank you in advance.

---

### Post by MAFoElffen on 2023-06-06
Please post the results of these commands, posted within CODE Tags:
```

uname -r
sudo lshw -c Network

```

---

### Post by terdes on 2023-06-06
Thank you for your reply! Here are the results.

```
uname -r
5.19.0-32-generic


sudo lshw -c Network

*-network                 
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 04
       serial: XXXXXXXXXXX
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=5.19.0-32-generic firmware=2017:888d latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:XXXXXXXXXXX memory:XXXXXXXXXXX
  *-network
       description: Wireless interface
       product: Wi-Fi 6 AX210/AX211/AX411 160MHz
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 1a
       serial: XXXXXXXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.19.0-32-generic firmware=72.daa05125.0 XXXXXXXXXXX ip=XXXXXXXXXXX latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:XXXXXXXXXXX
```

---

### Post by oldfred on 2023-06-06
Very new system.
I normally suggest newest LTS version which is 22.04 which uses 5.19 kernel. So you have 5 years before you have to update.
The interim versions only have 9 months.
But in your case you need latest kernel & drivers and at least 23.04. And then update to 23.10 and later to 24.04 LTS.

Can you boot live installer for 23.04 and see if things work better.
Make sure UEFI firmware & SSD firmware are latest available versions. Even new systems get updates (often more than older ones).
You also need to be sure to install nVidia driver from Ubuntu repository as part  of install. That is using Safe Boot option and choose to install optional restricted drivers. Use wired Ethernet for install.

Be sure to use gpt partitioning & UEFI install.

---

### Post by MAFoElffen on 2023-06-07
When I searched on this error, the last that appears before yours goes south:
```

Bluetooth: malformed MSFT vendor event: 0x02 

```

In your results:
```

description: Wireless interface
product: Wi-Fi 6 AX210/AX211/AX411 160MHz
vendor: Intel Corporation

```
But even though this error is common, that is not preventing other people (getting that error) from booting... Just not being able to do bluetooth on that same Intel AX series of WiFi cards.

What you might do is boot from a LiveUSB, and look at your /var/log/syslog, and see what happened just after that event.

---

