---
title: "Slow internet &amp; Wireless"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by bobme on 2012-12-28
Hi every one ...
Thanks for the great o/s.  However I seem to be having issues with the Internet... 
I ran the wireless script you said to run in a older post I looked up.  And I can post it if you think the information will help.
When I open firefox to use the web, it runs very slow.  However things like irc are still working while the web will not. 
Any ideas? 
It also does the same if wired or wireless.
Thanks for reading.

---

### Post by robert shearer on 2012-12-28
some hardware info/specs would help.
Open a terminal ( Ctrl+alt+t)
and enter...
```
sudo lshw
```

and paste the output back here inside code tags.

lshw=list hardware.

---

### Post by bobme on 2012-12-28
```

  *-core
       description: Motherboard
       product: MCP61PM-GM
       vendor: ECS
       physical id: 0
       version: 2.1
       serial: OEM
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 11/26/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Phenom(tm) 9500 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.2.2
          slot: Socket AM2
          size: 1100MHz
          capacity: 3GHz
          width: 64 bits
          clock: 235MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs hw_pstate npt lbrv svm_lock cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: d
          slot: External Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
     *-cpu:1
          physical id: a
          bus info: cpu@1
          version: 15.2.2
          size: 1100MHz
          capacity: 1100MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:2
          physical id: b
          bus info: cpu@2
          version: 15.2.2
          size: 1100MHz
          capacity: 1100MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:3
          physical id: e
          bus info: cpu@3
          version: 15.2.2
          size: 2200MHz
          capacity: 2200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1d00(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:b000(size=4096) memory:fde00000-fdefffff memory:fdd00000-fddfffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fdef0000-fdefffff ioport:bc00(size=8)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1e:90:67:13:e8
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:44 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:fe02b000-fe02bfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: RV610 [Radeon HD 2400 XT]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:43 memory:e0000000-efffffff memory:fdce0000-fdceffff ioport:ac00(size=256) memory:fdc00000-fdc1ffff
        *-multimedia
             description: Audio device
             product: RV610 HDMI Audio [Radeon HD 2350/2400 Series]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:fdcfc000-fdcfffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 101
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:9000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:8000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 10
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500DM002-1BD14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: KC45
             serial: W2AK7WWZ
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=00020f64
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 07bf9cd3-17f7-48c5-aea2-2555790b5ac7
                size: 462GiB
                capacity: 462GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-12-22 14:46:53 filesystem=ext4 lastmountpoint=/ modified=2012-12-27 22:11:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-12-27 22:11:18 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 3069MiB
                capacity: 3069MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3069MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 11
          bus info: usb@1:9
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan1
       serial: 00:14:bf:7c:ca:f5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.5.0-21-generic firmware=1.7 ip=192.168.1.7 link=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by bobme on 2012-12-28
It also does the same thing on my laptop running ubuntu also.
Windows computers run just fine.

---

### Post by thenox on 2013-01-03
Can you install a different browser and see if it runs as slow as Firefox?

---

### Post by Pjotr123 on 2013-01-03
Try disabling power management for your wireless card:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)
(item 2.1, right column)

---

### Post by thenox on 2013-01-03
You might also ping google and post the output.
In a terminal type (w/o quotes) "ping google.com"

---

