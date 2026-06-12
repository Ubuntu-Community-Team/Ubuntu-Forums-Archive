---
title: "Dell E1525FPg monitor, GeForce 6150SE, 'Cannot display this video mode'"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by mathemagician5 on 2014-03-24
Installed ubuntu 12.04 on old Dell windows vista, AMD 64 Live! and I'm getting a black screen with "Cannot Display This Video Mode".  I hit enter then ubuntu boots to log in screen, I'm unable to log in and it goes to a blank purple screen.

Please help.

---

### Post by mörgæs on 2014-03-25
Hi, welcome to the fora.

Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by rofik on 2014-03-25
Slow , . . Not Panic . . this blank Purple Is default . . Go to boot , wait 20s

. . 
. . or not happening . . At Startup press Up or down key . . And in menu grup selec Ubuntu recovery

---

### Post by mathemagician5 on 2014-03-29
What do I do next in Ubuntu recovery?

---

### Post by mathemagician5 on 2014-03-29
How do I bring up a terminal without getting past the log in screen.  Thank you for your patience with me.  I was able to get to Ubuntu recovery on start up.

---

### Post by mörgæs on 2014-03-29
You can do it from a live boot or (maybe) press Ctrl + Alt + F1 to get to a terminal.

---

### Post by mathemagician5 on 2014-03-29
> **mörgæs said:**
> Hi, welcome to the fora.

Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

Sorry, what is "CODE tags"?  opened terminal, entered "sudo lshw -sanitize > lshw.txt" and nothing happened.  Do I need to look for the code tags?

Again thank you for your assistance.

---

### Post by mathemagician5 on 2014-03-29
> **mörgæs said:**
> Hi, welcome to the fora.

Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

computer
    description: Desktop Computer
    product: GX615AA-ABA s3300f (GX615AA#ABA)
    vendor: HP-Pavilion
    version: Chassis Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=103C_53316J sku=GX615AA#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Acacia
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.02
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.07
          date: 10/11/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.11.2
          slot: Socket AM2
          size: 1800MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: HYMP112U64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: HYMP112U64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: a
          bus info: cpu@1
          version: 15.11.2
          size: 1800MHz
          capacity: 1800MHz
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
          physical id: b
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
          resources: irq:7 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
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
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
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
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
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
          resources: ioport:c000(size=4096) memory:fde00000-fdefffff memory:fdb00000-fdbfffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323 [TrueFire] 1394a Controller
             vendor: LSI Corporation
             physical id: 5
             bus info: pci@0000:01:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fdeff000-fdefffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:fdee0000-fdeeffff ioport:cc00(size=8)
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
          resources: irq:22 memory:fe028000-fe02bfff
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
          serial: [REMOVED]
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:41 memory:fe02d000-fe02dfff ioport:ec00(size=8)
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
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
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
          resources: irq:40 ioport:b000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: latency=0
          resources: memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: d
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-H653N
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 0609
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: e
          bus info: usb@1:10
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdb
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdc
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdd
     *-scsi:2
          physical id: f
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sde
             version: 3.CH
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00031a68
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sde1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-03-24 14:42:24 filesystem=ext4 lastmountpoint=/ modified=2014-03-24 16:21:56 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-03-24 16:41:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sde2
                size: 1917MiB
                capacity: 1917MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sde5
                   capacity: 1917MiB
                   capabilities: nofs
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:9
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.11.0-18-generic firmware=1.7 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by mathemagician5 on 2014-03-29
I'm ready to convert my windows xp dell to Ubuntu.  Do you inticipate any issues with memory, graphics cards, etc.  Thank you ! Here is my information;

computer
    description: Space-saving Computer
    product: Dimension 2400
    vendor: Winbond Electronics
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=space-saving cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0C2425
       vendor: Winbond Electronics
       physical id: 0
       version: A01
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A05
          date: 12/02/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2666MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fe900000-feafffff
           *-usb:0
                description: USB controller
                product: OHCI USB Controller
                vendor: NEC Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci-pci latency=64 maxlatency=42 mingnt=1
                resources: irq:16 memory:fe9fb000-fe9fbfff
           *-usb:1
                description: USB controller
                product: OHCI USB Controller
                vendor: NEC Corporation
                physical id: 4.1
                bus info: pci@0000:01:04.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci-pci latency=64 maxlatency=42 mingnt=1
                resources: irq:17 memory:fe9fc000-fe9fcfff
           *-usb:2
                description: USB controller
                product: uPD72010x USB 2.0 Controller
                vendor: NEC Corporation
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci-pci latency=64 maxlatency=34 mingnt=16
                resources: irq:18 memory:fe9faf00-fe9fafff
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64
                resources: irq:17 memory:fe9fd000-fe9fdfff ioport:dfa0(size=16)
           *-multimedia
                description: Multimedia audio controller
                product: [SB Live! Value] EMU10k1X
                vendor: Creative Labs
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_emu10k1x latency=64 maxlatency=20 mingnt=2
                resources: irq:18 ioport:dfe0(size=32)
           *-input
                description: Input device controller
                product: [SB Live! Value] Input device controller
                vendor: Creative Labs
                physical id: 6.1
                bus info: pci@0000:01:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:df98(size=8)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3120026A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.16
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=9dc96e9e
           *-volume:0
                description: Windows FAT volume
                vendor: Winbond Electronics
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT16
                serial: [REMOVED]
                size: 31MiB
                capacity: 31MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=DellUtility
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2004-03-10 04:25:50 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD+RW ND-2100AD
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 104E
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-scsi:2
          physical id: 3
          bus info: usb@1:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 1906MiB (1998MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=42c15f25
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: [REMOVED]
                size: 1905MiB
                capacity: 1905MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:3
          physical id: 4
          bus info: usb@2:3
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=5eefb759
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/Fagan Drive
                version: 3.1
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-11-04 16:48:31 filesystem=ntfs label=Fagan Drive mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted

---

### Post by mathemagician5 on 2014-03-29
> **mörgæs said:**
> You can do it from a live boot or (maybe) press Ctrl + Alt + F1 to get to a terminal.

I was able to open the terminal in the boot process and I posted my computer information above.

---

### Post by mörgæs on 2014-03-29
Please stop multiposting. Threads merged.
Code tags are available in the advanced editor. Please edit the posts.

---

### Post by mathemagician5 on 2014-03-29
```
computer
    description: Desktop Computer
    product: GX615AA-ABA s3300f (GX615AA#ABA)
    vendor: HP-Pavilion
    version: Chassis Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=103C_53316J sku=GX615AA#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Acacia
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.02
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.07
          date: 10/11/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect  socketedrom edd int13floppy360 int13floppy1200 int13floppy720  int13floppy2880 int5printscreen int9keyboard int14serial int17printer  int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.11.2
          slot: Socket AM2
          size: 1800MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2  ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16  lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: HYMP112U64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: HYMP112U64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: a
          bus info: cpu@1
          version: 15.11.2
          size: 1800MHz
          capacity: 1800MHz
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
          physical id: b
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
          resources: irq:7 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
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
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
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
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
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
          resources: ioport:c000(size=4096) memory:fde00000-fdefffff memory:fdb00000-fdbfffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323 [TrueFire] 1394a Controller
             vendor: LSI Corporation
             physical id: 5
             bus info: pci@0000:01:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fdeff000-fdefffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:fdee0000-fdeeffff ioport:cc00(size=8)
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
          resources: irq:22 memory:fe028000-fe02bfff
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
          serial: [REMOVED]
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes  driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20  mingnt=1 multicast=yes port=MII
          resources: irq:41 memory:fe02d000-fe02dfff ioport:ec00(size=8)
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
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4)  ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16)  memory:fe02c000-fe02cfff
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
          resources: irq:40 ioport:b000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: latency=0
          resources: memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: d
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-H653N
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 0609
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: e
          bus info: usb@1:10
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdb
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdc
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdd
     *-scsi:2
          physical id: f
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sde
             version: 3.CH
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00031a68
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sde1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink extents ext4 ext2  initialized
                configuration: created=2014-03-24 14:42:24  filesystem=ext4 lastmountpoint=/ modified=2014-03-24 16:21:56  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2014-03-24 16:41:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sde2
                size: 1917MiB
                capacity: 1917MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sde5
                   capacity: 1917MiB
                   capabilities: nofs
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:9
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb  driverversion=3.11.0-18-generic firmware=1.7 ip=[REMOVED] link=yes  multicast=yes wireless=IEEE 802.11bg
```

---

### Post by mathemagician5 on 2014-03-29
Sorry, I'm not multipositng, it's a second computer.  It would be great if you could assist with both.  I'll post the second computer in code tags also.  Thank you.

---

### Post by mathemagician5 on 2014-03-29
Second computer, looking to install Ubuntu to replace windows xp.  Don't feel I should dual boot due to lack of continued support from microsoft.

```
computer
    description: Space-saving Computer
    product: Dimension 2400
    vendor: Winbond Electronics
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=enabled boot=normal  chassis=space-saving cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0C2425
       vendor: Winbond Electronics
       physical id: 0
       version: A01
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A05
          date: 12/02/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot  bootselect edd int13floppytoshiba int5printscreen int9keyboard  int14serial int17printer acpi usb ls120boot biosbootspecification  netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2666MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr  sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fe900000-feafffff
           *-usb:0
                description: USB controller
                product: OHCI USB Controller
                vendor: NEC Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci-pci latency=64 maxlatency=42 mingnt=1
                resources: irq:16 memory:fe9fb000-fe9fbfff
           *-usb:1
                description: USB controller
                product: OHCI USB Controller
                vendor: NEC Corporation
                physical id: 4.1
                bus info: pci@0000:01:04.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci-pci latency=64 maxlatency=42 mingnt=1
                resources: irq:17 memory:fe9fc000-fe9fcfff
           *-usb:2
                description: USB controller
                product: uPD72010x USB 2.0 Controller
                vendor: NEC Corporation
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci-pci latency=64 maxlatency=34 mingnt=16
                resources: irq:18 memory:fe9faf00-fe9fafff
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64
                resources: irq:17 memory:fe9fd000-fe9fdfff ioport:dfa0(size=16)
           *-multimedia
                description: Multimedia audio controller
                product: [SB Live! Value] EMU10k1X
                vendor: Creative Labs
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_emu10k1x latency=64 maxlatency=20 mingnt=2
                resources: irq:18 ioport:dfe0(size=32)
           *-input
                description: Input device controller
                product: [SB Live! Value] Input device controller
                vendor: Creative Labs
                physical id: 6.1
                bus info: pci@0000:01:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:df98(size=8)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=64  link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:fe9fe000-fe9fffff memory:fea00000-fea03fff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6  ioport:170(size=8) ioport:376 ioport:ffa0(size=16)  memory:feb7fc00-feb7ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3120026A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.16
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=9dc96e9e
           *-volume:0
                description: Windows FAT volume
                vendor: Winbond Electronics
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT16
                serial: [REMOVED]
                size: 31MiB
                capacity: 31MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=DellUtility
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2004-03-10 04:25:50 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD+RW ND-2100AD
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 104E
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-scsi:2
          physical id: 3
          bus info: usb@1:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 1906MiB (1998MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=42c15f25
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: [REMOVED]
                size: 1905MiB
                capacity: 1905MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat  mount.options=ro,noatime,fmask=0022,dmask=0022,cod   epage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro  state=mounted
     *-scsi:3
          physical id: 4
          bus info: usb@2:3
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=5eefb759
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/Fagan Drive
                version: 3.1
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-11-04  16:48:31 filesystem=ntfs label=Fagan Drive mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,g   roup_id=0,default_permissions,allow_other,blksize=  4096 state=mounted
```

---

### Post by mörgæs on 2014-03-29
Sorry! Let's take a look at both of them.

For the Dimension 2400 I suggest a plain Lubuntu 13.10. You will see some strange graphics at first, but it's easy to correct. Just follow these instructions:
[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html)

---

### Post by mathemagician5 on 2014-03-29
Ok, great will try that on my Dimension 2400.  The problem on the HP-Pavilion is no longer "Cannot display this video mode" the monitor, it will go to the login screen after I hit "enter".  Unless i press the "up or down" button and enter a recovery menu as suggested by @rofik I cannot login (there is a login screen for 10 seconds, keyboard doesn't type, mouse won't move) and the screen goes blank purple.

---

### Post by mörgæs on 2014-03-29
For the combination GeForce 6150SE / nForce 430 and your error message there are quite a few hits in Google, but mostly for old software. 

Before we dig deeper into the problem, does it also appear in 13.10? Remember to check 'restricted drivers' during the install.

Adding 'nomodeset' as a boot option is also worth trying.

---

