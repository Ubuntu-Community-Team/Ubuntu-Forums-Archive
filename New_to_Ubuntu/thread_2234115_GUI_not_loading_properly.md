---
title: "GUI not loading properly"
date: 2014-07-12
forum: New to Ubuntu
---

### Post by benjstreet on 2014-07-12
I've got an ACER Revo 3600 which I have been running ubuntu since 2010 generally with no problems. When I upgraded to 12.10 I had problems with the GUI - it has an NVIDA ION chip.  I tried loads of different things to fix it from many different threads, and got it to a place where I can get into it by running startx every time I boot.  But in the procee I managed to lose my sound.  I have since upgraded to 14.04 and the problems are the same.  I would love to have the sound back and to get it to boot into the gui automatically.

Any help very gratefully received,

I've run lshw and this is the output:
```
                    description: Desktop Computer
    product: Aspire R3600 (To Be Filled By O.E.M.)
    vendor: Acer
    serial: ****
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=desktop cpus=1 family=To Be Filled By O.E.M. frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=To Be Filled By O.E.M. uuid=00226869-215C-2009-0710-152640000000
  *-core
       description: Motherboard
       product: FMCP7A-ION
       vendor: Acer
       physical id: 0
       serial: xxxx
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R01-A1L
          date: 05/22/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: Intel
          size: 1600MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm
          configuration: cores=1 enabledcores=1 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: FFFFFFFF
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM2
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:4f00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: NVIDIA Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:10 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: NVIDIA Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:fae80000-faefffff
        *-usb:0
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:fae7f000-fae7ffff
        *-usb:1
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fae7ec00-fae7ecff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:21 memory:fae78000-fae7bfff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:22:68:69:21:5c
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.13 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
             resources: irq:20 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=8) ioport:c800(size=4) ioport:c480(size=16) memory:fae76000-fae77fff
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:23
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:faf00000-fbffffff ioport:e0000000(size=436207616)
           *-display
                description: VGA compatible controller
                product: ION VGA
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:ec00(size=128) memory:fafe0000-faffffff
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:22
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:21 memory:feb00000-febfffff
           *-network DISABLED
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 00:26:5e:21:82:f6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.11.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:febf0000-febfffff
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:23
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVT-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 11.0
             serial: WD-WXK0E59AUA01
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=b4906930
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 8dd1c9b1-db42-43d5-9366-b200db097c36
                size: 227GiB
                capacity: 227GiB
                capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2009-09-29 19:03:37 filesystem=ext3 lastmountpoint=/media/8dd1c9b1-db42-43d5-9366-b200db097c36 modified=2014-07-12 18:05:47 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-07-12 18:05:48 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 5153MiB
                capacity: 5153MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5153MiB
                   capabilities: nofs

```

---

### Post by papibe on 2014-07-12
Hi benjstreet.

Try installing the Nvidia proprietary driver from 'Additional Drivers'.

Right now you are using the Nvidia open source driver (nouveau) which doesn't take all advantages of your graphic card.

Hope it helps. Let us know how it goes.
Regards.

---

