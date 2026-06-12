---
title: "PC freezing randomly"
date: 2017-08-15
forum: New to Ubuntu
---

### Post by ceponatia2 on 2017-08-15
Hi all, me again!

I previously stated that my PC appeared to be freezing after going into hibernation but while working on my last post about my internet connection, my PC froze while I was doing basically nothing. After 3 minutes I was able to move the mouse around but couldn't click anything and the keyboard didn't work so I had to power off manually. IDK if you want me to post my huge long list of hardware specs again but I will just in case.

UBUNTU 16.04.2

[I]```
description: Computer
[I]width: 64 bits
[I]capabilities: vsyscall32
[I]*-core
[I]description: Motherboard
[I]physical id: 0
[I]*-memory
[I]description: System memory
[I]physical id: 0
[I]size: 7914MiB
[I]*-cpu
[I]product: Intel(R) Core(TM) i5-4460 CPU @ 3.20GHz
[I]vendor: Intel Corp.
[I]physical id: 1
[I]bus info: cpu@0
[I]size: 3200MHz
[I]capacity: 3400MHz
[I]width: 64 bits
[I]capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
[I]*-pci
[I]description: Host bridge
[I]product: 4th Gen Core Processor DRAM Controller
[I]vendor: Intel Corporation
[I]physical id: 100
[I]bus info: pci@0000:00:00.0
[I]version: 06
[I]width: 32 bits
[I]clock: 33MHz
[I]configuration: driver=hsw_uncore
[I]resources: irq:0
[I]*-pci:0
[I]description: PCI bridge
[I]product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
[I]vendor: Intel Corporation
[I]physical id: 1
[I]bus info: pci@0000:00:01.0
[I]version: 06
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: pci normal_decode bus_master cap_list
[I]configuration: driver=pcieport
[I]resources: irq:25 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
[I]*-display
[I]description: VGA compatible controller
[I]product: GK208 [GeForce GT 720]
[I]vendor: NVIDIA Corporation
[I]physical id: 0
[I]bus info: pci@0000:01:00.0
[I]version: a1
[I]width: 64 bits
[I]clock: 33MHz
[I]capabilities: vga_controller bus_master cap_list rom
[I]configuration: driver=nouveau latency=0
[I]resources: irq:32 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
[I]*-multimedia
[I]description: Audio device
[I]product: GK208 HDMI/DP Audio Controller
[I]vendor: NVIDIA Corporation
[I]physical id: 0.1
[I]bus info: pci@0000:01:00.1
[I]version: a1
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: bus_master cap_list
[I]configuration: driver=snd_hda_intel latency=0
[I]resources: irq:17 memory:f7080000-f7083fff
[I]*-usb:0
[I]description: USB controller
[I]product: 8 Series/C220 Series Chipset Family USB xHCI
[I]vendor: Intel Corporation
[I]physical id: 14
[I]bus info: pci@0000:00:14.0
[I]version: 05
[I]width: 64 bits
[I]clock: 33MHz
[I]capabilities: xhci bus_master cap_list
[I]configuration: driver=xhci_hcd latency=0
[I]resources: irq:29 memory:f7200000-f720ffff
[I]*-communication
[I]description: Communication controller
[I]product: 8 Series/C220 Series Chipset Family MEI Controller #1
[I]vendor: Intel Corporation
[I]physical id: 16
[I]bus info: pci@0000:00:16.0
[I]version: 04
[I]width: 64 bits
[I]clock: 33MHz
[I]capabilities: bus_master cap_list
[I]configuration: driver=mei_me latency=0
[I]resources: irq:33 memory:f721b000-f721b00f
[I]*-usb:1
[I]description: USB controller
[I]product: 8 Series/C220 Series Chipset Family USB EHCI #2
[I]vendor: Intel Corporation
[I]physical id: 1a
[I]bus info: pci@0000:00:1a.0
[I]version: 05
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: ehci bus_master cap_list
[I]configuration: driver=ehci-pci latency=0
[I]resources: irq:16 memory:f7218000-f72183ff
[I]*-multimedia
[I]description: Audio device
[I]product: 8 Series/C220 Series Chipset High Definition Audio Controller
[I]vendor: Intel Corporation
[I]physical id: 1b
[I]bus info: pci@0000:00:1b.0
[I]version: 05
[I]width: 64 bits
[I]clock: 33MHz
[I]capabilities: bus_master cap_list
[I]configuration: driver=snd_hda_intel latency=0
[I]resources: irq:34 memory:f7210000-f7213fff
[I]*-pci:1
[I]description: PCI bridge
[I]product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
[I]vendor: Intel Corporation
[I]physical id: 1c
[I]bus info: pci@0000:00:1c.0
[I]version: d5
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: pci normal_decode bus_master cap_list
[I]configuration: driver=pcieport
[I]resources: irq:26 ioport:2000(size=4096) memory:e0000000-e01fffff ioport:e0200000(size=2097152)
[I]*-pci:2
[I]description: PCI bridge
[I]product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
[I]vendor: Intel Corporation
[I]physical id: 1c.5
[I]bus info: pci@0000:00:1c.5
[I]version: d5
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: pci normal_decode bus_master cap_list
[I]configuration: driver=pcieport
[I]resources: irq:27 ioport:d000(size=4096) ioport:f2100000(size=1048576)
[I]*-network
[I]description: Ethernet interface
[I]product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
[I]vendor: Realtek Semiconductor Co., Ltd.
[I]physical id: 0
[I]bus info: pci@0000:03:00.0
[I]logical name: enp3s0
[I]version: 09
[I]serial: 44:8a:5b:c1:dd:08
[I]size: 10Mbit/s
[I]capacity: 1Gbit/s
[I]width: 64 bits
[I]clock: 33MHz
[I]capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
[I]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
[I]resources: irq:30 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
[I]*-pci:3
[I]description: PCI bridge
[I]product: 8 Series/C220 Series Chipset Family PCI Express Root Port #8
[I]vendor: Intel Corporation
[I]physical id: 1c.7
[I]bus info: pci@0000:00:1c.7
[I]version: d5
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: pci normal_decode bus_master cap_list
[I]configuration: driver=pcieport
[I]resources: irq:28 ioport:c000(size=4096) memory:f7100000-f71fffff
[I]*-network
[I]description: Wireless interface
[I]product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
[I]vendor: Realtek Semiconductor Co., Ltd.
[I]physical id: 0
[I]bus info: pci@0000:04:00.0
[I]logical name: wlp4s0
[I]version: 00
[I]serial: 9c:ad:97:59:f3:c9
[I]width: 64 bits
[I]clock: 33MHz
[I]capabilities: bus_master cap_list ethernet physical wireless
[I]configuration: broadcast=yes driver=rtl8821ae driverversion=4.10.0-32-generic firmware=N/A ip=10.0.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11
[I]resources: irq:35 ioport:c000(size=256) memory:f7100000-f7103fff
[I]*-usb:2
[I]description: USB controller
[I]product: 8 Series/C220 Series Chipset Family USB EHCI #1
[I]vendor: Intel Corporation
[I]physical id: 1d
[I]bus info: pci@0000:00:1d.0
[I]version: 05
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: ehci bus_master cap_list
[I]configuration: driver=ehci-pci latency=0
[I]resources: irq:23 memory:f7217000-f72173ff
[I]*-isa
[I]description: ISA bridge
[I]product: B85 Express LPC Controller
[I]vendor: Intel Corporation
[I]physical id: 1f
[I]bus info: pci@0000:00:1f.0
[I]version: 05
[I]width: 32 bits
[I]clock: 33MHz
[I]capabilities: isa bus_master cap_list
[I]configuration: driver=lpc_ich latency=0
[I]resources: irq:0
[I]*-storage
[I]description: SATA controller
[I]product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
[I]vendor: Intel Corporation
[I]physical id: 1f.2
[I]bus info: pci@0000:00:1f.2
[I]version: 05
[I]width: 32 bits
[I]clock: 66MHz
[I]capabilities: storage ahci_1.0 bus_master cap_list
[I]configuration: driver=ahci latency=0
[I]resources: irq:31 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7216000-f72167ff
[I]*-serial UNCLAIMED
[I]description: SMBus
[I]product: 8 Series/C220 Series Chipset Family SMBus Controller
[I]vendor: Intel Corporation
[I]physical id: 1f.3
[I]bus info: pci@0000:00:1f.3
[I]version: 05
[I]width: 64 bits
[I]clock: 33MHz
[I]configuration: latency=0
[I]resources: memory:f7215000-f72150ff ioport:f000(size=32)
[I]*-scsi
[I]physical id: 2
[I]logical name: scsi2
[I]capabilities: emulated
[I]*-cdrom
[I]description: DVD-RAM writer
[I]product: DVD-RAM SW830
[I]vendor: MATSHITA
[I]physical id: 0.0.0
[I]bus info: scsi@2:0.0.0
[I]logical name: /dev/cdrom
[I]logical name: /dev/cdrw
[I]logical name: /dev/dvd
[I]logical name: /dev/dvdrw
[I]logical name: /dev/sr0
[I]logical name: /media/brian/RF-MRBTAD
[I]version: 8.83
[I]capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
[I]configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gi d=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
[I]*-medium
[I]physical id: 0
[I]logical name: /dev/cdrom
[I]logical name: /media/brian/RF-MRBTAD
[I]configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gi d=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
[I]*-scsi
[I]physical id: 1
[I]bus info: scsi@6
[I]logical name: scsi6
[I]capabilities: scsi-host
[I]configuration: driver=usb-storage
```
[/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I]
IDK if there's a way to collapse that list so people don't have to scroll past it in every question I post but if there is PLEASE let me know lol. I'll continue looking around online for solutions but it's pretty difficult given my connection drops every 5 minutes and shortly after that my PC totally freezes. :/

---

### Post by TheFu on 2017-08-15
What do the log files say?  That is always the first place to look for any issues.

As for posting specs, it is mostly useless.  Saying i5/8G and nvidia GeForce GT 720 with nouveau is probably sufficient - unless the logs point to a specific hw issue.  Only then would the limited lshw output FOR ONLY THAT hardware be useful.

---

### Post by ceponatia2 on 2017-08-16
I'll get the log files when I get home. I disabled the monitor sleep mode to see if that helped and I still get freezing at random times but it doesn't seem like it's the whole PC that's freezing. I was watching a movie on Netflix last night and the display froze on the same frame but the audio kept going. No keyboard or mouse input did anything.

---

### Post by TheFu on 2017-08-16
Which kernel is being used?  I'm on 4.10.x using on-board Intel graphics and while the audio and/or video stuttering happens whenever the system gets busy (or whenever firefox sucks 100+% of the CPU) every few minutes.  

My stuttering issues all started when 4.10.x was installed.  Prior to that, on the 4.4 kernel, any full screen video playback would completely lock up the system after about 3-10 minutes.  But stuttering didn't happen and firefox CPU abuse didn't appear to lock up the entire system like it does under 4.10.

My logs are showing an ethernet issue during these lock up. I use an external USB3-to-GigE adapter. It has been used for over 2 years without any issues, so this is somehow tied to the newer kernel.

---

### Post by ceponatia2 on 2017-08-16
I'll have to check the kernel when I get home from work at 5. I use Chrome instead of Firefox (my Firefox browser won't play certain videos I need for school and Chrome does) and my connection is wifi but I will say I do have some connection problems with the wifi. My system freezing happens even when I'm not in a browser though. Even when I'm not doing ANYTHING at all.

---

### Post by ceponatia2 on 2017-08-18
My kernel version is 4.10.0-32-generic

My log file output is here: [http://paste.ubuntu.com/25339201/](http://paste.ubuntu.com/25339201/)

I also noticed I am receiving between 2 and 3 system errors when I boot up. Typing this fast because my system will freeze any second. :D

---

