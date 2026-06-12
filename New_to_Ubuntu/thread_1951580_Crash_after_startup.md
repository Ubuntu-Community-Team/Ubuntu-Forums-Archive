---
title: "Crash after startup"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by roodypoo on 2012-04-02
[LEFT]After I start my computer, there are some small flickering squares on the desktop and when I enter text (no matter where, terminal, firefox, gedit...) and press enter Ubuntu crashes to the login screen. After I log back in there are no problems.

I have no idea where to start.
[/LEFT]

---

### Post by Gleichsnerd on 2012-04-02
Well first things first, what version of Ubuntu are you using? What graphics card are you using? Are you using any proprietary drivers for it?

---

### Post by roodypoo on 2012-04-02
11.10 
Radeon HD 4250
Yes, fgrlx, compiled from source.

More:
```

c@c:~$ sudo lshw
[sudo] password for c: 
c                         
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=A06CE08B-8DFE-D511-9913-BCAEC58D76C4
  *-core
       description: Motherboard
       product: M4A88TD-M/USB3
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MF70ACG01700467
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1201
          date: 07/21/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1090T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1090T Processor
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 3200MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=6 enabledcores=6
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 768KiB
             capacity: 768KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: pipeline-burst internal varies
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS880 PCI to PCI bridge (int gfx)
             vendor: ASUSTeK Computer Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:fe700000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880 [Radeon HD 4250]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:c000(size=256) memory:fe8f0000-fe8fffff memory:fe700000-fe7fffff
           *-multimedia
                description: Audio device
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fe8e8000-fe8ebfff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:fe900000-fe9fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:fe9fe000-fe9fffff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 4)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fea00000-feafffff
           *-ide
                description: IDE interface
                product: VT6415 PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list rom
                configuration: driver=pata_via latency=0
                resources: irq:17 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:feae0000-feaeffff
        *-pci:3
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 5)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: bc:ae:c5:8d:76:c4
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:50 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi4
             logical name: scsi5
             logical name: scsi6
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:19 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fe6ffc00-fe6fffff
           *-disk:0
                description: ATA Disk
                product: OCZ-VERTEX3
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 2.15
                serial: OCZ-YLJ0AIW6A1A6S1O7
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00045e59
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b223b245-73be-49b0-884c-536235774af1
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-03-26 23:29:15 filesystem=ext4 lastmountpoint=/ modified=2012-03-27 22:55:03 mount.fstype=ext4 mount.options=rw,noatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered,discard mounted=2012-04-02 18:07:23 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 41GiB
           *-disk:1
                description: ATA Disk
                product: ST31000333AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/sdb
                version: SD35
                serial: 9TE07NNK
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000651c0
              *-volume:0
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: af17b8e8-605c-4761-b5aa-0fff52dc3935
                   size: 1492KiB
                   capacity: 1495KiB
                   capabilities: primary extended_attributes ext2 initialized
                   configuration: filesystem=ext2 modified=2012-03-18 11:21:01 state=unknown
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sdb2
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /media/part1_
                      capacity: 444GiB
                      configuration: mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 487GiB
           *-cdrom
                description: DVD-RAM writer
                product: iHAS124   B
                vendor: ATAPI
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AL0K
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6fe000-fe6fefff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe6ff800-fe6ff8ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6fd000-fe6fdfff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe6ff400-fe6ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fe6f8000-fe6fbfff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: AR5212/AR5213 Multiprotocol MAC/baseband processor
                vendor: Atheros Communications Inc.
                physical id: 5
                bus info: pci@0000:05:05.0
                logical name: wlan0
                version: 01
                serial: 00:1e:2a:ac:27:68
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.0.0-17-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:20 memory:febf0000-febfffff
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6fc000-fe6fcfff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6f7000-fe6f7fff
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe6ff000-fe6ff0ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by roodypoo on 2012-04-02
more
```

c@c:~$ sudo fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4250  
OpenGL version string: 3.3.11554 Compatibility Profile Context

```

---

### Post by Gleichsnerd on 2012-04-03
Hmm. Puzzling.

Similar symptoms occurred with ATI cards (found on [this thread]("http://ubuntuforums.org/showthread.php?t=1491729")), and the people there said that the graphics memory was being overclocked.

Are you using any overclock software or overclocking your processor? It might be having some residual effect on your graphics card.

---

### Post by roodypoo on 2012-04-03
Thanks for the replies, no overclocking. Everything is stock.

I have removed evry non essential package I could find using debfoster and deborphan.

But the symptoms were happening before I did that.

---

