---
title: "random black boxes on ubuntu 16.04 monitor"
date: 2016-06-22
forum: New to Ubuntu
---

### Post by micahpage on 2016-06-22
I am having random black boxes pop up over my screen on since installing ubuntu 16.04. This happens across the entire screen, not just the browser as shown in the image. Sometimes it will fill the entire screen, sometimes not. If i scroll, the section scolled clears, but the rest remains. They will randomly disappear over time as well. Sometimes they wont show up at all. 

[IMG]http://imgur.com/Llghmf8[/IMG]
[http://imgur.com/Llghmf8](http://imgur.com/Llghmf8)

stats:
```
metulburr@ubuntu:~$ uname -a
Linux ubuntu 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



```

```
metulburr@ubuntu:~$ sudo lshw
[sudo] password for metulburr: 
ubuntu                    
    description: Desktop Computer
    product: CG8350 (To be filled by O.E.M.)
    vendor: ASUSTeK Computer INC.
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=400A94CC-FF5B-D911-986E-BCAEC5EA1CED
  *-core
       description: Motherboard
       product: CG8350
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MT7012007601105
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0902
          date: 02/11/2011
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 1967MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
             configuration: level=2
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 14GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: SLZ3128M8-EDJED
             vendor: Undefined
             physical id: 0
             serial: 000001B
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: SLZ3128M8-EDJED
             vendor: Undefined
             physical id: 1
             serial: 000001A
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: SLZ3128M8-EDJED
             vendor: Undefined
             physical id: 2
             serial: 0000008
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: DBLT8GN128S
             vendor: Undefined
             physical id: 3
             serial: 0000000
             slot: DIMM3
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=snb_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:38 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:39 memory:fe507000-fe50700f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe506000-fe5063ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Mass storage device
                      product: Mass Storage Device
                      vendor: Generic
                      physical id: 1
                      bus info: usb@1:1.1
                      logical name: scsi4
                      version: 1.00
                      serial: 058F63626420
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                    *-disk:0
                         description: SCSI Disk
                         physical id: 0.0.0
                         bus info: scsi@4:0.0.0
                         logical name: /dev/sdb
                         size: 60GiB (64GB)
                         capabilities: partitioned partitioned:dos
                         configuration: logicalsectorsize=512 sectorsize=512
                       *-volume
                            description: Windows FAT volume
                            vendor: mkfs.fat
                            physical id: 1
                            bus info: scsi@4:0.0.0,1
                            logical name: /dev/sdb1
                            logical name: /media/metulburr/8BF9-3EBD
                            version: FAT32
                            serial: 8bf9-3ebd
                            size: 60GiB
                            capacity: 60GiB
                            capabilities: primary fat initialized
                            configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
                    *-disk:1
                         description: SCSI Disk
                         physical id: 0.0.1
                         bus info: scsi@4:0.0.1
                         logical name: /dev/sdc
                         configuration: logicalsectorsize=512 sectorsize=512
                    *-disk:2
                         description: SCSI Disk
                         physical id: 0.0.2
                         bus info: scsi@4:0.0.2
                         logical name: /dev/sdd
                         configuration: logicalsectorsize=512 sectorsize=512
                    *-disk:3
                         description: SCSI Disk
                         physical id: 0.0.3
                         bus info: scsi@4:0.0.3
                         logical name: /dev/sde
                         configuration: logicalsectorsize=512 sectorsize=512
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:40 memory:fe500000-fe503fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:fe400000-fe4fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fe400000-fe407fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-22-generic xhci-hcd
                   physical id: 0
                   bus info: usb@4
                   logical name: usb4
                   version: 4.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-22-generic xhci-hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 4.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: enp5s0
                version: 06
                serial: bc:ae:c5:ea:1c:ed
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:37 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe505000-fe5053ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb:0
                      description: Mass storage device
                      product: My Book 1230
                      vendor: Western Digital
                      physical id: 3
                      bus info: usb@2:1.3
                      logical name: scsi5
                      version: 10.50
                      serial: 574343344530363334383932
                      capabilities: usb-2.10 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=26mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: My Book 1230
                         vendor: WD
                         physical id: 0.0.0
                         bus info: scsi@5:0.0.0
                         logical name: /dev/sdf
                         version: 1050
                         serial: WCC4E0634892
                         size: 3725GiB (4TB)
                         capabilities: partitioned partitioned:dos
                         configuration: ansiversion=6 logicalsectorsize=4096 sectorsize=4096 signature=db4bf07b
                       *-volume UNCLAIMED
                            description: HPFS/NTFS partition
                            physical id: 1
                            bus info: scsi@5:0.0.0,1
                            capacity: 465GiB
                            capabilities: primary
                    *-enclosure UNCLAIMED
                         description: SCSI Enclosure
                         product: SES Device
                         vendor: WD
                         physical id: 0.0.1
                         bus info: scsi@5:0.0.1
                         version: 1050
                         serial: WCC4E0634892
                         configuration: ansiversion=6
                 *-usb:1
                      description: Keyboard
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 7
                      bus info: usb@2:1.7
                      version: 12.01
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
                 *-usb:2
                      description: Keyboard
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 8
                      bus info: usb@2:1.8
                      version: 12.01
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
        *-isa
             description: ISA bridge
             product: H67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:f110(size=8) ioport:f100(size=4) ioport:f0f0(size=8) ioport:f0e0(size=4) ioport:f0d0(size=16) ioport:f0c0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe504000-fe5040ff ioport:f040(size=32)
        *-ide:1
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=16) ioport:f060(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC44
             serial: 5VP72AWX
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=9664c0d1
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 8963e4c6-44cd-4a12-8fdd-b86e99ec3f89
                size: 917GiB
                capacity: 917GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-05-09 08:53:29 filesystem=ext4 lastmountpoint=/ modified=2016-06-03 13:03:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-06-03 13:04:03 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 13GiB
                capacity: 13GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 13GiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DH16ABSH
             vendor: ATAPI
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: YAA1
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power:0 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-power:1 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh



```

```
metulburr@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9664c0d1


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1924345855 1924343808 917.6G 83 Linux
/dev/sda2       1924347902 1953523711   29175810  13.9G  5 Extended
/dev/sda5       1924347904 1953523711   29175808  13.9G 82 Linux swap / Solaris








Disk /dev/sdb: 60.4 GiB, 64826114048 bytes, 126613504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1       32768 126613503 126580736 60.4G  c W95 FAT32 (LBA)




Disk /dev/sdf: 3.7 TiB, 4000752599040 bytes, 976746240 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdb4bf07b


Device     Boot Start       End   Sectors  Size Id Type
/dev/sdf1         256 976746239 976745984  3.7T  7 HPFS/NTFS/exFAT



```

installed packages:
```
metulburr@ubuntu:~$ dpkg --get-selections | grep -v deinstall
a11y-profile-manager-indicator            install
account-plugin-aim                install
account-plugin-facebook                install
account-plugin-flickr                install
account-plugin-google                install
account-plugin-jabber                install
account-plugin-salut                install
account-plugin-yahoo                install
accountsservice                    install
acl                        install
acpi-support                    install
acpid                        install
activity-log-manager                install
adduser                        install
adium-theme-ubuntu                install
adwaita-icon-theme                install
aisleriot                    install
alacarte                    install
alsa-base                    install
alsa-utils                    install
anacron                        install
apg                        install
app-install-data                install
app-install-data-partner            install
apparmor                    install
apport                        install
apport-gtk                    install
apport-symptoms                    install
appstream                    install
apt                        install
apt-transport-https                install
apt-utils                    install
aptdaemon                    install
aptdaemon-data                    install
apturl                        install
apturl-common                    install
argyll                        install
argyll-ref                    install
aspell                        install
aspell-en                    install
at-spi2-core                    install
autotools-dev                    install
avahi-autoipd                    install
avahi-daemon                    install
avahi-utils                    install
bamfdaemon                    install
baobab                        install
base-files                    install
base-passwd                    install
bash                        install
bash-completion                    install
bc                        install
bijiben                        install
bind9-host                    install
binfmt-support                    install
binutils                    install
bleachbit                    install
blt                        install
bluez                        install
bluez-cups                    install
bluez-obexd                    install
bogofilter                    install
bogofilter-bdb                    install
bogofilter-common                install
branding-ubuntu                    install
brasero                        install
brasero-cdrkit                    install
brasero-common                    install
breeze-icon-theme                install
brltty                        install
bsdmainutils                    install
bsdutils                    install
build-essential                    install
busybox-initramfs                install
busybox-static                    install
bzip2                        install
ca-certificates                    install
cabextract                    install
caribou                        install
caribou-antler                    install
cdparanoia                    install
cdrdao                        install
checkbox-converged                install
checkbox-gui                    install
cheese                        install
cheese-common                    install
chromium-browser                install
chromium-browser-l10n                install
chromium-codecs-ffmpeg-extra            install
colord                        install
colord-data                    install
command-not-found                install
command-not-found-data                install
compiz                        install
compiz-core                    install
compiz-gnome                    install
compiz-plugins-default:amd64            install
console-setup                    install
console-setup-linux                install
coreutils                    install
cpio                        install
cpp                        install
cpp-5                        install
cracklib-runtime                install
crda                        install
cron                        install
cups                        install
cups-browsed                    install
cups-bsd                    install
cups-client                    install
cups-common                    install
cups-core-drivers                install
cups-daemon                    install
cups-filters                    install
cups-filters-core-drivers            install
cups-pk-helper                    install
cups-ppdc                    install
cups-server-common                install
curl                        install
dash                        install
dbus                        install
dbus-x11                    install
dc                        install
dconf-cli                    install
dconf-editor                    install
dconf-gsettings-backend:amd64            install
dconf-service                    install
dconf-tools                    install
debconf                        install
debconf-i18n                    install
debhelper                    install
debianutils                    install
deja-dup                    install
deluge                        install
deluge-common                    install
deluge-gtk                    install
desktop-base                    install
desktop-file-utils                install
desmume                        install
dh-python                    install
dh-strip-nondeterminism                install
dictionaries-common                install
diffstat                    install
diffutils                    install
dirmngr                        install
distro-info-data                install
dleyna-renderer                    install
dleyna-server                    install
dmidecode                    install
dmz-cursor-theme                install
dns-root-data                    install
dnsmasq-base                    install
dnsutils                    install
doc-base                    install
docbook-xml                    install
docbook-xsl                    install
dosfstools                    install
dpkg                        install
dpkg-dev                    install
dvd+rw-tools                    install
e2fslibs:amd64                    install
e2fsprogs                    install
ed                        install
efibootmgr                    install
eject                        install
emacsen-common                    install
empathy                        install
empathy-common                    install
enchant                        install
eog                        install
epiphany-browser                install
epiphany-browser-data                install
espeak-data:amd64                install
ethtool                        install
evince                        install
evince-common                    install
evolution                    install
evolution-common                install
evolution-data-server                install
evolution-data-server-common            install
evolution-data-server-online-accounts        install
evolution-plugins                install
example-content                    install
extlinux                    install
fairymax                    install
fakeroot                    install
ffmpeg                        install
file                        install
file-roller                    install
findutils                    install
finger                        install
firefox                        install
firefox-locale-en                install
five-or-more                    install
flashplugin-installer                install
folks-common                    install
fontconfig                    install
fontconfig-config                install
fonts-cantarell                    install
fonts-dejavu                    install
fonts-dejavu-core                install
fonts-dejavu-extra                install
fonts-freefont-ttf                install
fonts-guru                    install
fonts-guru-extra                install
fonts-horai-umefont                install
fonts-kacst                    install
fonts-kacst-one                    install
fonts-khmeros-core                install
fonts-lao                    install
fonts-liberation                install
fonts-lklug-sinhala                install
fonts-lohit-guru                install
fonts-lyx                    install
fonts-nanum                    install
fonts-noto-cjk                    install
fonts-opensymbol                install
fonts-sil-abyssinica                install
fonts-sil-padauk                install
fonts-stix                    install
fonts-symbola                    install
fonts-takao-pgothic                install
fonts-thai-tlwg                    install
fonts-tibetan-machine                install
fonts-tlwg-garuda                install
fonts-tlwg-garuda-ttf                install
fonts-tlwg-kinnari                install
fonts-tlwg-kinnari-ttf                install
fonts-tlwg-laksaman                install
fonts-tlwg-laksaman-ttf                install
fonts-tlwg-loma                    install
fonts-tlwg-loma-ttf                install
fonts-tlwg-mono                    install
fonts-tlwg-mono-ttf                install
fonts-tlwg-norasi                install
fonts-tlwg-norasi-ttf                install
fonts-tlwg-purisa                install
fonts-tlwg-purisa-ttf                install
fonts-tlwg-sawasdee                install
fonts-tlwg-sawasdee-ttf                install
fonts-tlwg-typewriter                install
fonts-tlwg-typewriter-ttf            install
fonts-tlwg-typist                install
fonts-tlwg-typist-ttf                install
fonts-tlwg-typo                    install
fonts-tlwg-typo-ttf                install
fonts-tlwg-umpush                install
fonts-tlwg-umpush-ttf                install
fonts-tlwg-waree                install
fonts-tlwg-waree-ttf                install
fonts-unfonts-core                install
fonts-wqy-microhei                install
foomatic-db-compressed-ppds            install
four-in-a-row                    install
freepats                    install
freerdp-x11                    install
friendly-recovery                install
ftp                        install
fuse                        install
fwupd                        install
fwupdate                    install
fwupdate-signed                    install
g++                        install
g++-5                        install
gawk                        install
gcc                        install
gcc-5                        install
gcc-5-base:amd64                install
gcc-5-base:i386                    install
gcc-6-base:amd64                install
gcc-6-base:i386                    install
gconf-service                    install
gconf-service-backend                install
gconf2                        install
gconf2-common                    install
gcr                        install
gdb                        install
gdbserver                    install
gdisk                        install
gdm3                        install
geany                        install
geany-common                    install
gedit                        install
gedit-common                    install
gedit-plugins                    install
genisoimage                    install
geoclue                        install
geoclue-2.0                    install
geoclue-ubuntu-geoip                install
geoip-database                    install
gettext                        install
gettext-base                    install
ghostscript                    install
ghostscript-x                    install
gimp                        install
gimp-data                    install
gir1.2-accounts-1.0:amd64            install
gir1.2-accountsservice-1.0            install
gir1.2-appindicator3-0.1            install
gir1.2-atk-1.0                    install
gir1.2-atspi-2.0                install
gir1.2-caribou-1.0                install
gir1.2-champlain-0.12:amd64            install
gir1.2-clutter-1.0:amd64            install
gir1.2-clutter-gst-3.0:amd64            install
gir1.2-cogl-1.0:amd64                install
gir1.2-coglpango-1.0:amd64            install
gir1.2-dbusmenu-glib-0.4:amd64            install
gir1.2-dee-1.0                    install
gir1.2-evince-3.0:amd64                install
gir1.2-freedesktop:amd64            install
gir1.2-gck-1:amd64                install
gir1.2-gconf-2.0                install
gir1.2-gcr-3:amd64                install
gir1.2-gdata-0.0:amd64                install
gir1.2-gdesktopenums-3.0            install
gir1.2-gdkpixbuf-2.0:amd64            install
gir1.2-gdm-1.0                    install
gir1.2-geocodeglib-1.0:amd64            install
gir1.2-gfbgraph-0.2:amd64            install
gir1.2-git2-glib-1.0                install
gir1.2-gkbd-3.0:amd64                install
gir1.2-glib-2.0:amd64                install
gir1.2-gmenu-3.0:amd64                install
gir1.2-gnomebluetooth-1.0:amd64            install
gir1.2-gnomedesktop-3.0:amd64            install
gir1.2-gnomekeyring-1.0                install
gir1.2-goa-1.0:amd64                install
gir1.2-grilo-0.2:amd64                install
gir1.2-gst-plugins-base-1.0            install
gir1.2-gstreamer-1.0                install
gir1.2-gtk-2.0                    install
gir1.2-gtk-3.0:amd64                install
gir1.2-gtkchamplain-0.12:amd64            install
gir1.2-gtkclutter-1.0:amd64            install
gir1.2-gtksource-3.0:amd64            install
gir1.2-gucharmap-2.90:amd64            install
gir1.2-gudev-1.0:amd64                install
gir1.2-gweather-3.0:amd64            install
gir1.2-ibus-1.0:amd64                install
gir1.2-javascriptcoregtk-4.0:amd64        install
gir1.2-json-1.0:amd64                install
gir1.2-mediaart-2.0:amd64            install
gir1.2-mutter-3.0                install
gir1.2-networkmanager-1.0:amd64            install
gir1.2-nmgtk-1.0:amd64                install
gir1.2-notify-0.7                install
gir1.2-packagekitglib-1.0            install
gir1.2-pango-1.0:amd64                install
gir1.2-peas-1.0:amd64                install
gir1.2-polkit-1.0                install
gir1.2-rb-3.0:amd64                install
gir1.2-rest-0.7                    install
gir1.2-secret-1:amd64                install
gir1.2-signon-1.0                install
gir1.2-soup-2.4                    install
gir1.2-telepathyglib-0.12            install
gir1.2-telepathylogger-0.2            install
gir1.2-totem-1.0:amd64                install
gir1.2-totem-plparser-1.0:amd64            install
gir1.2-tracker-1.0:amd64            install
gir1.2-udisks-2.0:amd64                install
gir1.2-unity-5.0:amd64                install
gir1.2-upowerglib-1.0                install
gir1.2-vte-2.91:amd64                install
gir1.2-webkit2-4.0:amd64            install
gir1.2-wnck-3.0:amd64                install
gir1.2-xkl-1.0:amd64                install
gir1.2-zeitgeist-2.0                install
gir1.2-zpj-0.0                    install
git                        install
git-core                    install
git-doc                        install
git-man                        install
gjs                        install
gkbd-capplet                    install
gksu                        install
glib-networking:amd64                install
glib-networking-common                install
glib-networking-services            install
gnome                        install
gnome-accessibility-themes            install
gnome-backgrounds                install
gnome-bluetooth                    install
gnome-calculator                install
gnome-calendar                    install
gnome-chess                    install
gnome-clocks                    install
gnome-color-manager                install
gnome-contacts                    install
gnome-control-center                install
gnome-control-center-data            install
gnome-core                    install
gnome-desktop3-data                install
gnome-dictionary                install
gnome-disk-utility                install
gnome-documents                    install
gnome-font-viewer                install
gnome-games                    install
gnome-getting-started-docs            install
gnome-icon-theme                install
gnome-icon-theme-symbolic            install
gnome-keyring                    install
gnome-klotski                    install
gnome-logs                    install
gnome-mahjongg                    install
gnome-maps                    install
gnome-menus                    install
gnome-mines                    install
gnome-music                    install
gnome-nettool                    install
gnome-nibbles                    install
gnome-online-accounts                install
gnome-online-miners                install
gnome-orca                    install
gnome-packagekit                install
gnome-packagekit-data                install
gnome-packagekit-session            install
gnome-photos                    install
gnome-power-manager                install
gnome-robots                    install
gnome-screensaver                install
gnome-screenshot                install
gnome-session                    install
gnome-session-bin                install
gnome-session-canberra                install
gnome-session-common                install
gnome-settings-daemon                install
gnome-settings-daemon-schemas            install
gnome-shell                    install
gnome-shell-common                install
gnome-shell-extension-weather            install
gnome-shell-extensions                install
gnome-software                    install
gnome-software-common                install
gnome-sound-recorder                install
gnome-sudoku                    install
gnome-sushi                    install
gnome-system-log                install
gnome-system-monitor                install
gnome-terminal                    install
gnome-terminal-data                install
gnome-tetravex                    install
gnome-themes-standard:amd64            install
gnome-themes-standard-data            install
gnome-tweak-tool                install
gnome-user-guide                install
gnome-user-share                install
gnome-video-effects                install
gnupg                        install
gnupg-agent                    install
gnupg2                        install
goobox                        install
google-chrome-stable                install
gparted                        install
gpgv                        install
grep                        install
grilo-plugins-0.2-base:amd64            install
grilo-plugins-0.2-extra:amd64            install
groff-base                    install
growisofs                    install
grub-common                    install
grub-gfxpayload-lists                install
grub-pc                        install
grub-pc-bin                    install
grub2-common                    install
gsettings-desktop-schemas            install
gsettings-ubuntu-schemas            install
gsfonts                        install
gstreamer1.0-alsa:amd64                install
gstreamer1.0-clutter-3.0            install
gstreamer1.0-fluendo-mp3:amd64            install
gstreamer1.0-libav:amd64            install
gstreamer1.0-nice:amd64                install
gstreamer1.0-plugins-bad:amd64            install
gstreamer1.0-plugins-bad-faad:amd64        install
gstreamer1.0-plugins-bad-videoparsers:amd64    install
gstreamer1.0-plugins-base:amd64            install
gstreamer1.0-plugins-base-apps            install
gstreamer1.0-plugins-good:amd64            install
gstreamer1.0-plugins-ugly:amd64            install
gstreamer1.0-plugins-ugly-amr:amd64        install
gstreamer1.0-pulseaudio:amd64            install
gstreamer1.0-tools                install
gstreamer1.0-x:amd64                install
gtk2-engines:amd64                install
gtk2-engines-murrine:amd64            install
gtk2-engines-pixbuf:amd64            install
gucharmap                    install
guile-2.0-libs:amd64                install
gvfs:amd64                    install
gvfs-backends                    install
gvfs-bin                    install
gvfs-common                    install
gvfs-daemons                    install
gvfs-fuse                    install
gvfs-libs:amd64                    install
gzip                        install
hamster-applet                    install
hamster-indicator                install
hardening-includes                install
hdparm                        install
hicolor-icon-theme                install
hitori                        install
hoichess                    install
hostname                    install
hplip                        install
hplip-data                    install
htop                        install
hud                        install
humanity-icon-theme                install
hunspell-en-us                    install
hwdata                        install
hyphen-en-us                    install
i965-va-driver:amd64                install
iagno                        install
ibus                        install
ibus-gtk:amd64                    install
ibus-gtk3:amd64                    install
ibus-table                    install
icoutils                    install
ifupdown                    install
iio-sensor-proxy                install
im-config                    install
imagemagick                    install
imagemagick-6.q16                install
imagemagick-common                install
indicator-application                install
indicator-bluetooth                install
indicator-datetime                install
indicator-keyboard                install
indicator-messages                install
indicator-power                    install
indicator-printers                install
indicator-session                install
indicator-sound                    install
info                        install
init                        install
init-system-helpers                install
initramfs-tools                    install
initramfs-tools-bin                install
initramfs-tools-core                install
initscripts                    install
inkscape                    install
inputattach                    install
insserv                        install
install-info                    install
intel-gpu-tools                    install
intel-microcode                    install
intltool-debian                    install
ippusbxd                    install
iproute2                    install
iptables                    install
iputils-arping                    install
iputils-ping                    install
iputils-tracepath                install
irqbalance                    install
isc-dhcp-client                    install
isc-dhcp-common                    install
iso-codes                    install
iucode-tool                    install
iw                        install
javascript-common                install
k3b                        install
k3b-data                    install
kactivities                    install
kate-data                    install
katepart                    install
kbd                        install
kde-runtime                    install
kde-runtime-data                install
kde-style-breeze                install
kde-style-breeze-qt4                install
kdelibs-bin                    install
kdelibs5-data                    install
kdelibs5-plugins                install
kdoctools                    install
kerneloops-daemon                install
keyboard-configuration                install
kino                        install
klibc-utils                    install
kmod                        install
kpackagelauncherqml                install
kpackagetool5                    install
krb5-locales                    install
ktorrent                    install
ktorrent-data                    install
kwayland-data                    install
kwayland-integration:amd64            install
language-pack-en                install
language-pack-en-base                install
language-pack-gnome-en                install
language-pack-gnome-en-base            install
language-selector-common            install
language-selector-gnome                install
laptop-detect                    install
less                        install
liba11y-profile-manager-0.1-0:amd64        install
liba11y-profile-manager-data            install
liba52-0.7.4:amd64                install
libaa1:amd64                    install
libaacs0:amd64                    install
libabw-0.1-1v5:amd64                install
libaccount-plugin-1.0-0:amd64            install
libaccount-plugin-generic-oauth            install
libaccount-plugin-google            install
libaccounts-glib0:amd64                install
libaccounts-qt5-1:amd64                install
libaccountsservice0:amd64            install
libacl1:amd64                    install
libalgorithm-diff-perl                install
libalgorithm-diff-xs-perl            install
libalgorithm-merge-perl                install
libamd2.4.1:amd64                install
libandroid-properties1                install
libao-common                    install
libao4:amd64                    install
libapparmor-perl                install
libapparmor1:amd64                install
libappindicator1                install
libappindicator3-1                install
libappstream-glib8:amd64            install
libappstream3:amd64                install
libapr1:amd64                    install
libaprutil1:amd64                install
libapt-inst2.0:amd64                install
libapt-pkg-perl                    install
libapt-pkg5.0:amd64                install
libarchive-zip-perl                install
libarchive13:amd64                install
libart-2.0-2:amd64                install
libasan2:amd64                    install
libasn1-8-heimdal:amd64                install
libasn1-8-heimdal:i386                install
libasound2:amd64                install
libasound2:i386                    install
libasound2-data                    install
libasound2-dev:amd64                install
libasound2-plugins:amd64            install
libasound2-plugins:i386                install
libaspell15:amd64                install
libasprintf-dev:amd64                install
libasprintf0v5:amd64                install
libass5:amd64                    install
libassuan0:amd64                install
libasyncns0:amd64                install
libasyncns0:i386                install
libatasmart4:amd64                install
libatk-adaptor:amd64                install
libatk-bridge2.0-0:amd64            install
libatk1.0-0:amd64                install
libatk1.0-data                    install
libatk1.0-dev                    install
libatkmm-1.6-1v5:amd64                install
libatm1:amd64                    install
libatomic1:amd64                install
libatspi2.0-0:amd64                install
libattica0.4:amd64                install
libattr1:amd64                    install
libaudio2:amd64                    install
libaudit-common                    install
libaudit1:amd64                    install
libauthen-sasl-perl                install
libavahi-client3:amd64                install
libavahi-client3:i386                install
libavahi-common-data:amd64            install
libavahi-common-data:i386            install
libavahi-common3:amd64                install
libavahi-common3:i386                install
libavahi-core7:amd64                install
libavahi-glib1:amd64                install
libavahi-gobject0:amd64                install
libavahi-ui-gtk3-0:amd64            install
libavc1394-0:amd64                install
libavcodec-extra                install
libavcodec-ffmpeg-extra56:amd64            install
libavdevice-ffmpeg56:amd64            install
libavfilter-ffmpeg5:amd64            install
libavformat-ffmpeg56:amd64            install
libavresample-ffmpeg2:amd64            install
libavutil-ffmpeg54:amd64            install
libbabeltrace-ctf1:amd64            install
libbabeltrace1:amd64                install
libbabl-0.1-0:amd64                install
libbamf3-2:amd64                install
libbasicusageenvironment1:amd64            install
libbdplus0:amd64                install
libbind9-140:amd64                install
libblas-common                    install
libblas3                    install
libblkid1:amd64                    install
libbluetooth3:amd64                install
libbluray1:amd64                install
libbonobo2-0:amd64                install
libbonobo2-common                install
libbonoboui2-0:amd64                install
libbonoboui2-common                install
libboost-date-time1.58.0:amd64            install
libboost-filesystem1.58.0:amd64            install
libboost-iostreams1.58.0:amd64            install
libboost-python1.58.0                install
libboost-system1.58.0:amd64            install
libbrasero-media3-1:amd64            install
libbrlapi0.6:amd64                install
libbs2b0:amd64                    install
libbsd0:amd64                    install
libbsd0:i386                    install
libburn4:amd64                    install
libbz2-1.0:amd64                install
libc-bin                    install
libc-dev-bin                    install
libc6:amd64                    install
libc6:i386                    install
libc6-dbg:amd64                    install
libc6-dev:amd64                    install
libcaca-dev                    install
libcaca0:amd64                    install
libcaca0:i386                    install
libcacard0:amd64                install
libcairo-gobject2:amd64                install
libcairo-perl                    install
libcairo-script-interpreter2:amd64        install
libcairo2:amd64                    install
libcairo2-dev                    install
libcairomm-1.0-1v5:amd64            install
libcamd2.4.1:amd64                install
libcamel-1.2-54:amd64                install
libcanberra-gtk-module:amd64            install
libcanberra-gtk0:amd64                install
libcanberra-gtk3-0:amd64            install
libcanberra-gtk3-module:amd64            install
libcanberra-pulse:amd64                install
libcanberra0:amd64                install
libcap-ng0:amd64                install
libcap2:amd64                    install
libcap2-bin                    install
libcapi20-3:amd64                install
libcapi20-3:i386                install
libcaribou-common                install
libcaribou-gtk-module:amd64            install
libcaribou-gtk3-module:amd64            install
libcaribou0:amd64                install
libcc1-0:amd64                    install
libccolamd2.9.1:amd64                install
libcddb2                    install
libcdio-cdda1:amd64                install
libcdio-paranoia1:amd64                install
libcdio13:amd64                    install
libcdparanoia0:amd64                install
libcdr-0.1-1:amd64                install
libcgi-fast-perl                install
libcgi-pm-perl                    install
libcgmanager0:amd64                install
libchamplain-0.12-0:amd64            install
libchamplain-gtk-0.12-0:amd64            install
libcheese-gtk25:amd64                install
libcheese8:amd64                install
libcholmod3.0.6:amd64                install
libchromaprint0:amd64                install
libcilkrts5:amd64                install
libclass-accessor-perl                install
libclone-perl                    install
libclucene-contribs1v5:amd64            install
libclucene-core1v5:amd64            install
libclutter-1.0-0:amd64                install
libclutter-1.0-common                install
libclutter-gst-2.0-0:amd64            install
libclutter-gst-3.0-0:amd64            install
libclutter-gtk-1.0-0:amd64            install
libcmis-0.5-5v5:amd64                install
libcogl-common                    install
libcogl-pango20:amd64                install
libcogl-path20:amd64                install
libcogl20:amd64                    install
libcolamd2.9.1:amd64                install
libcolord-gtk1:amd64                install
libcolord2:amd64                install
libcolorhug2:amd64                install
libcolumbus1-common                install
libcolumbus1v5:amd64                install
libcomerr2:amd64                install
libcomerr2:i386                    install
libcompizconfig0:amd64                install
libcoverart1:amd64                install
libcoverartcc1v5:amd64                install
libcrack2:amd64                    install
libcroco3:amd64                    install
libcryptsetup4:amd64                install
libcryptui0a:amd64                install
libcrystalhd3:amd64                install
libcups2:amd64                    install
libcups2:i386                    install
libcupscgi1:amd64                install
libcupsfilters1:amd64                install
libcupsimage2:amd64                install
libcupsmime1:amd64                install
libcupsppdc1:amd64                install
libcurl3:amd64                    install
libcurl3-gnutls:amd64                install
libdaemon0:amd64                install
libdata-alias-perl                install
libdatrie1:amd64                install
libdb5.3:amd64                    install
libdb5.3:i386                    install
libdbus-1-3:amd64                install
libdbus-1-3:i386                install
libdbus-glib-1-2:amd64                install
libdbusmenu-glib4:amd64                install
libdbusmenu-gtk3-4:amd64            install
libdbusmenu-gtk4:amd64                install
libdbusmenu-qt2:amd64                install
libdbusmenu-qt5:amd64                install
libdc1394-22:amd64                install
libdca0:amd64                    install
libdconf1:amd64                    install
libde265-0:amd64                install
libdebconfclient0:amd64                install
libdecoration0:amd64                install
libdee-1.0-4:amd64                install
libdevmapper1.02.1:amd64            install
libdfu1:amd64                    install
libdigest-hmac-perl                install
libdirectfb-1.2-9:amd64                install
libdiscid0:amd64                install
libdjvulibre-text                install
libdjvulibre21:amd64                install
libdleyna-connector-dbus-1.0-1:amd64        install
libdleyna-core-1.0-3:amd64            install
libdlrestrictions1                install
libdmapsharing-3.0-2:amd64            install
libdns-export162                install
libdns162:amd64                    install
libdotconf0:amd64                install
libdouble-conversion1v5:amd64            install
libdpkg-perl                    install
libdrm-amdgpu1:amd64                install
libdrm-amdgpu1:i386                install
libdrm-dev:amd64                install
libdrm-intel1:amd64                install
libdrm-intel1:i386                install
libdrm-nouveau2:amd64                install
libdrm-nouveau2:i386                install
libdrm-radeon1:amd64                install
libdrm-radeon1:i386                install
libdrm2:amd64                    install
libdrm2:i386                    install
libdv4:amd64                    install
libdvbpsi10:amd64                install
libdvdnav4:amd64                install
libdvdread4:amd64                install
libe-book-0.1-1:amd64                install
libebackend-1.2-10:amd64            install
libebml4v5:amd64                install
libebook-1.2-16:amd64                install
libebook-contacts-1.2-2:amd64            install
libecal-1.2-19:amd64                install
libedata-book-1.2-25:amd64            install
libedata-cal-1.2-28:amd64            install
libedataserver-1.2-21:amd64            install
libedataserverui-1.2-1:amd64            install
libedit2:amd64                    install
libedit2:i386                    install
libefivar0:amd64                install
libegl1-mesa:amd64                install
libelf1:amd64                    install
libelf1:i386                    install
libemail-valid-perl                install
libenca0:amd64                    install
libenchant1c2a:amd64                install
libencode-locale-perl                install
libeot0:amd64                    install
libepoxy0:amd64                    install
libept1.5.0:amd64                install
liberror-perl                    install
libespeak1:amd64                install
libestr0                    install
libetonyek-0.1-1:amd64                install
libevdev2:amd64                    install
libevdocument3-4:amd64                install
libevent-2.0-5:amd64                install
libevolution                    install
libevview3-3:amd64                install
libexempi3:amd64                install
libexif12:amd64                    install
libexif12:i386                    install
libexiv2-14:amd64                install
libexpat1:amd64                    install
libexpat1:i386                    install
libexpat1-dev:amd64                install
libexporter-tiny-perl                install
libexttextcat-2.0-0:amd64            install
libexttextcat-data                install
libfaad2:amd64                    install
libfakeroot:amd64                install
libfam0                        install
libfarstream-0.2-5:amd64            install
libfcgi-perl                    install
libfcitx-config4:amd64                install
libfcitx-gclient0:amd64                install
libfcitx-utils0:amd64                install
libfdisk1:amd64                    install
libffi6:amd64                    install
libffi6:i386                    install
libfftw3-double3:amd64                install
libfftw3-single3:amd64                install
libfile-basedir-perl                install
libfile-copy-recursive-perl            install
libfile-desktopentry-perl            install
libfile-fcntllock-perl                install
libfile-listing-perl                install
libfile-mimeinfo-perl                install
libfile-stripnondeterminism-perl        install
libflac++6v5:amd64                install
libflac-dev:amd64                install
libflac8:amd64                    install
libflac8:i386                    install
libflite1:amd64                    install
libfluidsynth1:amd64                install
libfolks-eds25:amd64                install
libfolks-telepathy25:amd64            install
libfolks25:amd64                install
libfont-afm-perl                install
libfontconfig1:amd64                install
libfontconfig1:i386                install
libfontconfig1-dev:amd64            install
libfontembed1:amd64                install
libfontenc1:amd64                install
libframe6:amd64                    install
libfreehand-0.1-1:amd64                install
libfreerdp-cache1.1:amd64            install
libfreerdp-client1.1:amd64            install
libfreerdp-codec1.1:amd64            install
libfreerdp-common1.1.0:amd64            install
libfreerdp-core1.1:amd64            install
libfreerdp-crypto1.1:amd64            install
libfreerdp-gdi1.1:amd64                install
libfreerdp-locale1.1:amd64            install
libfreerdp-plugins-standard:amd64        install
libfreerdp-primitives1.1:amd64            install
libfreerdp-rail1.1:amd64            install
libfreerdp-utils1.1:amd64            install
libfreetype6:amd64                install
libfreetype6:i386                install
libfreetype6-dev:amd64                install
libfribidi0:amd64                install
libfuse2:amd64                    install
libfwup0:amd64                    install
libfwupd1:amd64                    install
libgail-3-0:amd64                install
libgail-common:amd64                install
libgail18:amd64                    install
libgbm1:amd64                    install
libgc1c2:amd64                    install
libgcab-1.0-0:amd64                install
libgcc-5-dev:amd64                install
libgcc1:amd64                    install
libgcc1:i386                    install
libgck-1-0:amd64                install
libgconf-2-4:amd64                install
libgcr-3-common                    install
libgcr-base-3-1:amd64                install
libgcr-ui-3-1:amd64                install
libgcrypt20:amd64                install
libgcrypt20:i386                install
libgd3:amd64                    install
libgd3:i386                    install
libgdata-common                    install
libgdata22:amd64                install
libgdbm3:amd64                    install
libgdict-1.0-9:amd64                install
libgdict-common                    install
libgdk-pixbuf2.0-0:amd64            install
libgdk-pixbuf2.0-common                install
libgdk-pixbuf2.0-dev                install
libgdm1                        install
libgee-0.8-2:amd64                install
libgegl-0.3-0:amd64                install
libgeis1:amd64                    install
libgeoclue-2-0:amd64                install
libgeoclue0:amd64                install
libgeocode-glib0:amd64                install
libgeoip1:amd64                    install
libgeonames0:amd64                install
libgettextpo-dev:amd64                install
libgettextpo0:amd64                install
libgexiv2-2:amd64                install
libgfbgraph-0.2-0:amd64                install
libgfortran3:amd64                install
libgif7:amd64                    install
libgif7:i386                    install
libgimp2.0                    install
libgirepository-1.0-1:amd64            install
libgit2-24:amd64                install
libgit2-glib-1.0-0:amd64            install
libgjs0e                    install
libgksu2-0                    install
libgl1-mesa-dev:amd64                install
libgl1-mesa-dri:amd64                install
libgl1-mesa-dri:i386                install
libgl1-mesa-glx:amd64                install
libgl1-mesa-glx:i386                install
libglade2-0:amd64                install
libglapi-mesa:amd64                install
libglapi-mesa:i386                install
libgles1-mesa:amd64                install
libgles2-mesa:amd64                install
libglew1.13:amd64                install
libglewmx1.13:amd64                install
libglib-perl                    install
libglib2.0-0:amd64                install
libglib2.0-bin                    install
libglib2.0-data                    install
libglib2.0-dev                    install
libglibmm-2.4-1v5:amd64                install
libglu1-mesa:amd64                install
libglu1-mesa:i386                install
libglu1-mesa-dev:amd64                install
libgme0:amd64                    install
libgmime-2.6-0:amd64                install
libgmp10:amd64                    install
libgmp10:i386                    install
libgnome-2-0:amd64                install
libgnome-bluetooth13:amd64            install
libgnome-desktop-3-12:amd64            install
libgnome-keyring-common                install
libgnome-keyring0:amd64                install
libgnome-menu-3-0:amd64                install
libgnome2-0:amd64                install
libgnome2-bin                    install
libgnome2-common                install
libgnomecanvas2-0:amd64                install
libgnomecanvas2-common                install
libgnomekbd-common                install
libgnomekbd8:amd64                install
libgnomeui-0:amd64                install
libgnomeui-common                install
libgnomevfs2-0:amd64                install
libgnomevfs2-common                install
libgnomevfs2-extra:amd64            install
libgnutls-openssl27:amd64            install
libgnutls30:amd64                install
libgnutls30:i386                install
libgoa-1.0-0b:amd64                install
libgoa-1.0-common                install
libgoa-backend-1.0-1:amd64            install
libgom-1.0-0:amd64                install
libgom-1.0-common                install
libgomp1:amd64                    install
libgpg-error0:amd64                install
libgpg-error0:i386                install
libgpgme11:amd64                install
libgphoto2-6:amd64                install
libgphoto2-6:i386                install
libgphoto2-l10n                    install
libgphoto2-port12:amd64                install
libgphoto2-port12:i386                install
libgpm2:amd64                    install
libgpm2:i386                    install
libgpod-common                    install
libgpod4:amd64                    install
libgrail6                    install
libgraphite2-3:amd64                install
libgrilo-0.2-1:amd64                install
libgroupsock8:amd64                install
libgs9:amd64                    install
libgs9-common                    install
libgsettings-qt1:amd64                install
libgsf-1-114:amd64                install
libgsf-1-common                    install
libgsf-bin                    install
libgsl2:amd64                    install
libgsm1:amd64                    install
libgsound0:amd64                install
libgssapi-krb5-2:amd64                install
libgssapi-krb5-2:i386                install
libgssapi3-heimdal:amd64            install
libgssapi3-heimdal:i386                install
libgssdp-1.0-3:amd64                install
libgstreamer-plugins-bad1.0-0:amd64        install
libgstreamer-plugins-base1.0-0:amd64        install
libgstreamer-plugins-good1.0-0:amd64        install
libgstreamer1.0-0:amd64                install
libgtk-3-0:amd64                install
libgtk-3-bin                    install
libgtk-3-common                    install
libgtk-vnc-2.0-0:amd64                install
libgtk2-perl                    install
libgtk2.0-0:amd64                install
libgtk2.0-bin                    install
libgtk2.0-common                install
libgtk2.0-dev                    install
libgtkglext1:amd64                install
libgtkmm-2.4-1v5:amd64                install
libgtkmm-3.0-1v5:amd64                install
libgtksourceview-3.0-1:amd64            install
libgtksourceview-3.0-common            install
libgtkspell0                    install
libgtkspell3-3-0:amd64                install
libgtop-2.0-10:amd64                install
libgtop2-common                    install
libgucharmap-2-90-7:amd64            install
libgudev-1.0-0:amd64                install
libguess1:amd64                    install
libgupnp-1.0-4:amd64                install
libgupnp-av-1.0-2                install
libgupnp-dlna-2.0-3                install
libgupnp-igd-1.0-4:amd64            install
libgusb2:amd64                    install
libgutenprint2                    install
libgvnc-1.0-0:amd64                install
libgweather-3-6:amd64                install
libgweather-common                install
libgxps2:amd64                    install
libharfbuzz-dev                    install
libharfbuzz-gobject0:amd64            install
libharfbuzz-icu0:amd64                install
libharfbuzz0b:amd64                install
libhcrypto4-heimdal:amd64            install
libhcrypto4-heimdal:i386            install
libheimbase1-heimdal:amd64            install
libheimbase1-heimdal:i386            install
libheimntlm0-heimdal:amd64            install
libheimntlm0-heimdal:i386            install
libhogweed4:amd64                install
libhogweed4:i386                install
libhpmud0:amd64                    install
libhtml-form-perl                install
libhtml-format-perl                install
libhtml-parser-perl                install
libhtml-tagset-perl                install
libhtml-tree-perl                install
libhttp-cookies-perl                install
libhttp-daemon-perl                install
libhttp-date-perl                install
libhttp-message-perl                install
libhttp-negotiate-perl                install
libhttp-parser2.1:amd64                install
libhud2:amd64                    install
libhunspell-1.3-0:amd64                install
libhx509-5-heimdal:amd64            install
libhx509-5-heimdal:i386                install
libhyphen0:amd64                install
libibus-1.0-5:amd64                install
libical1a:amd64                    install
libice-dev:amd64                install
libice6:amd64                    install
libice6:i386                    install
libicu55:amd64                    install
libicu55:i386                    install
libidl-2-0:amd64                install
libidn11:amd64                    install
libidn11:i386                    install
libido3-0.1-0:amd64                install
libiec61883-0:amd64                install
libieee1284-3:amd64                install
libieee1284-3:i386                install
libijs-0.35:amd64                install
libilmbase12:amd64                install
libimage-magick-perl                install
libimage-magick-q16-perl            install
libimobiledevice6:amd64                install
libindicator3-7                    install
libindicator7                    install
libinput10:amd64                install
libio-html-perl                    install
libio-pty-perl                    install
libio-socket-inet6-perl                install
libio-socket-ssl-perl                install
libio-string-perl                install
libipc-run-perl                    install
libipc-system-simple-perl            install
libisc-export160                install
libisc160:amd64                    install
libisccc140:amd64                install
libisccfg140:amd64                install
libisl15:amd64                    install
libiso9660-8:amd64                install
libisofs6:amd64                    install
libitm1:amd64                    install
libiw30:amd64                    install
libjack-jackd2-0:amd64                install
libjack-jackd2-0:i386                install
libjansson4:amd64                install
libjasper1:amd64                install
libjavascriptcoregtk-3.0-0:amd64        install
libjavascriptcoregtk-4.0-18:amd64        install
libjbig-dev:amd64                install
libjbig0:amd64                    install
libjbig0:i386                    install
libjbig2dec0                    install
libjpeg-dev:amd64                install
libjpeg-turbo8:amd64                install
libjpeg-turbo8:i386                install
libjpeg-turbo8-dev:amd64            install
libjpeg8:amd64                    install
libjpeg8:i386                    install
libjpeg8-dev:amd64                install
libjs-excanvas                    install
libjs-jquery                    install
libjs-jquery-ui                    install
libjson-c2:amd64                install
libjson-c2:i386                    install
libjson-glib-1.0-0:amd64            install
libjson-glib-1.0-common                install
libjte1:amd64                    install
libk3b6                        install
libk3b6-extracodecs                install
libk5crypto3:amd64                install
libk5crypto3:i386                install
libkactivities6                    install
libkate1:amd64                    install
libkatepartinterfaces4                install
libkcddb4                    install
libkcmutils4                    install
libkcompactdisc4                install
libkde3support4                    install
libkdeclarative5                install
libkdecore5                    install
libkdesu5                    install
libkdeui5                    install
libkdewebkit5                    install
libkdnssd4                    install
libkemoticons4                    install
libkeyutils1:amd64                install
libkeyutils1:i386                install
libkf5activities5:amd64                install
libkf5archive5:amd64                install
libkf5attica5:amd64                install
libkf5auth-data                    install
libkf5auth5:amd64                install
libkf5calendarevents5:amd64            install
libkf5codecs-data                install
libkf5codecs5:amd64                install
libkf5completion-data                install
libkf5completion5:amd64                install
libkf5config-bin                install
libkf5config-data                install
libkf5configcore5:amd64                install
libkf5configgui5:amd64                install
libkf5configwidgets-data            install
libkf5configwidgets5:amd64            install
libkf5coreaddons-data                install
libkf5coreaddons5:amd64                install
libkf5crash5:amd64                install
libkf5dbusaddons-bin                install
libkf5dbusaddons-data                install
libkf5dbusaddons5:amd64                install
libkf5declarative-data                install
libkf5declarative5:amd64            install
libkf5globalaccel-bin                install
libkf5globalaccel-data                install
libkf5globalaccel5:amd64            install
libkf5globalaccelprivate5:amd64            install
libkf5guiaddons5:amd64                install
libkf5i18n-data                    install
libkf5i18n5:amd64                install
libkf5iconthemes-bin                install
libkf5iconthemes-data                install
libkf5iconthemes5:amd64                install
libkf5idletime5:amd64                install
libkf5itemviews-data                install
libkf5itemviews5:amd64                install
libkf5jobwidgets-data                install
libkf5jobwidgets5:amd64                install
libkf5kiocore5:amd64                install
libkf5kiowidgets5:amd64                install
libkf5notifications-data            install
libkf5notifications5:amd64            install
libkf5package-data                install
libkf5package5:amd64                install
libkf5plasma5:amd64                install
libkf5plasmaquick5:amd64            install
libkf5quickaddons5:amd64            install
libkf5service-bin                install
libkf5service-data                install
libkf5service5:amd64                install
libkf5sonnet5-data                install
libkf5sonnetcore5:amd64                install
libkf5sonnetui5:amd64                install
libkf5style5:amd64                install
libkf5textwidgets-data                install
libkf5textwidgets5:amd64            install
libkf5waylandclient5:amd64            install
libkf5widgetsaddons-data            install
libkf5widgetsaddons5:amd64            install
libkf5windowsystem-data                install
libkf5windowsystem5:amd64            install
libkf5xmlgui-bin                install
libkf5xmlgui-data                install
libkf5xmlgui5:amd64                install
libkfile4                    install
libkhtml5                    install
libkio5                        install
libkjsapi4                    install
libkjsembed4                    install
libklibc                    install
libkmediaplayer4                install
libkmod2:amd64                    install
libknewstuff3-4                    install
libknotifyconfig4                install
libkntlm4                    install
libkparts4                    install
libkpathsea6:amd64                install
libkpty4                    install
libkrb5-26-heimdal:amd64            install
libkrb5-26-heimdal:i386                install
libkrb5-3:amd64                    install
libkrb5-3:i386                    install
libkrb5support0:amd64                install
libkrb5support0:i386                install
libkrosscore4                    install
libksba8:amd64                    install
libktexteditor4                    install
libktorrent-l10n                install
libktorrent5                    install
libkxmlrpcclient4                install
liblangtag-common                install
liblangtag1:amd64                install
liblapack3                    install
liblcms2-2:amd64                install
liblcms2-2:i386                    install
liblcms2-utils                    install
libldap-2.4-2:amd64                install
libldap-2.4-2:i386                install
libldb1:amd64                    install
liblightdm-gobject-1-0:amd64            install
liblinear3:amd64                install
liblircclient0:amd64                install
liblist-moreutils-perl                install
liblivemedia50:amd64                install
libllvm3.8:amd64                install
libllvm3.8:i386                    install
liblocale-gettext-perl                install
liblouis-data                    install
liblouis9:amd64                    install
liblouisutdml-bin                install
liblouisutdml-data                install
liblouisutdml6:amd64                install
liblqr-1-0:amd64                install
liblsan0:amd64                    install
libltdl7:amd64                    install
libltdl7:i386                    install
liblua5.2-0:amd64                install
liblua5.3-0:amd64                install
liblwp-mediatypes-perl                install
liblwp-protocol-https-perl            install
liblwres141:amd64                install
liblz4-1:amd64                    install
liblzma-dev:amd64                install
liblzma5:amd64                    install
liblzma5:i386                    install
liblzo2-2:amd64                    install
libmad0:amd64                    install
libmad0-dev                    install
libmagic1:amd64                    install
libmagick++-6.q16-5v5:amd64            install
libmagickcore-6.q16-2:amd64            install
libmagickcore-6.q16-2-extra:amd64        install
libmagickwand-6.q16-2:amd64            install
libmail-sendmail-perl                install
libmailtools-perl                install
libmatroska6v5:amd64                install
libmbim-glib4:amd64                install
libmbim-proxy                    install
libmeanwhile1:amd64                install
libmediaart-2.0-0:amd64                install
libmessaging-menu0:amd64            install
libmetacity-private3a:amd64            install
libmhash2:amd64                    install
libmikmod-config                install
libmikmod-dev:amd64                install
libmikmod3:amd64                install
libmimic0:amd64                    install
libminiupnpc10:amd64                install
libmirclient9:amd64                install
libmircommon5:amd64                install
libmirprotobuf3:amd64                install
libmission-control-plugins0:amd64        install
libmjpegutils-2.1-0                install
libmm-glib0:amd64                install
libmms0:amd64                    install
libmng2:amd64                    install
libmnl0:amd64                    install
libmodplug1:amd64                install
libmount1:amd64                    install
libmozjs-24-0v5                    install
libmp3lame0:amd64                install
libmpc3:amd64                    install
libmpcdec6:amd64                install
libmpdec2:amd64                    install
libmpeg2-4:amd64                install
libmpeg2encpp-2.1-0                install
libmpfr4:amd64                    install
libmpg123-0:amd64                install
libmpg123-0:i386                install
libmplex2-2.1-0                    install
libmpx0:amd64                    install
libmspack0:amd64                install
libmspub-0.1-1:amd64                install
libmtdev1:amd64                    install
libmtp-common                    install
libmtp-runtime                    install
libmtp9:amd64                    install
libmusicbrainz5-2:amd64                install
libmusicbrainz5cc2v5:amd64            install
libmutter0g                    install
libmwaw-0.3-3:amd64                install
libmysqlclient20:amd64                install
libmythes-1.2-0:amd64                install
libnatpmp1:amd64                install
libnautilus-extension1a:amd64            install
libncurses5:amd64                install
libncurses5:i386                install
libncursesw5:amd64                install
libncursesw5:i386                install
libndp0:amd64                    install
libneon27-gnutls:amd64                install
libnet-dbus-perl                install
libnet-dns-perl                    install
libnet-domain-tld-perl                install
libnet-http-perl                install
libnet-ip-perl                    install
libnet-libidn-perl                install
libnet-smtp-ssl-perl                install
libnet-ssleay-perl                install
libnetfilter-conntrack3:amd64            install
libnetpbm10                    install
libnettle6:amd64                install
libnettle6:i386                    install
libnewt0.52:amd64                install
libnfnetlink0:amd64                install
libnice10:amd64                    install
libnih-dbus1:amd64                install
libnih1:amd64                    install
libnl-3-200:amd64                install
libnl-genl-3-200:amd64                install
libnl-route-3-200:amd64                install
libnm-glib-vpn1:amd64                install
libnm-glib4:amd64                install
libnm-gtk-common                install
libnm-gtk0:amd64                install
libnm-util2:amd64                install
libnm0:amd64                    install
libnma-common                    install
libnma0:amd64                    install
libnotify-bin                    install
libnotify4:amd64                install
libnpth0:amd64                    install
libnspr4:amd64                    install
libnss-mdns:amd64                install
libnss3:amd64                    install
libnss3-nssdb                    install
libntrack-qt4-1                    install
libntrack0                    install
libnuma1:amd64                    install
libnux-4.0-0                    install
libnux-4.0-common                install
liboauth0:amd64                    install
libodbc1:amd64                    install
libodfgen-0.1-1                    install
libofa0:amd64                    install
libogg-dev:amd64                install
libogg0:amd64                    install
libogg0:i386                    install
libopenal-data                    install
libopenal1:amd64                install
libopenal1:i386                    install
libopencore-amrnb0:amd64            install
libopencore-amrwb0:amd64            install
libopencv-calib3d2.4v5:amd64            install
libopencv-contrib2.4v5:amd64            install
libopencv-core2.4v5:amd64            install
libopencv-features2d2.4v5:amd64            install
libopencv-flann2.4v5:amd64            install
libopencv-highgui2.4v5:amd64            install
libopencv-imgproc2.4v5:amd64            install
libopencv-legacy2.4v5:amd64            install
libopencv-ml2.4v5:amd64                install
libopencv-objdetect2.4v5:amd64            install
libopencv-video2.4v5:amd64            install
libopenexr22:amd64                install
libopenjpeg5:amd64                install
libopus0:amd64                    install
liborbit-2-0:amd64                install
liborbit2:amd64                    install
liborc-0.4-0:amd64                install
liborcus-0.10-0v5:amd64                install
libosmesa6:amd64                install
libosmesa6:i386                    install
liboxideqt-qmlplugin:amd64            install
liboxideqtcore0:amd64                install
liboxideqtquick0:amd64                install
libp11-kit-gnome-keyring:amd64            install
libp11-kit-gnome-keyring:i386            install
libp11-kit0:amd64                install
libp11-kit0:i386                install
libpackagekit-glib2-16:amd64            install
libpagemaker-0.0-0:amd64            install
libpam-gnome-keyring:amd64            install
libpam-modules:amd64                install
libpam-modules-bin                install
libpam-runtime                    install
libpam-systemd:amd64                install
libpam0g:amd64                    install
libpango-1.0-0:amd64                install
libpango-perl                    install
libpango1.0-0:amd64                install
libpango1.0-dev                    install
libpangocairo-1.0-0:amd64            install
libpangoft2-1.0-0:amd64                install
libpangomm-1.4-1v5:amd64            install
libpangox-1.0-0:amd64                install
libpangoxft-1.0-0:amd64                install
libpaper-utils                    install
libpaper1:amd64                    install
libparse-debianchangelog-perl            install
libparted-fs-resize0:amd64            install
libparted2:amd64                install
libpcap0.8:amd64                install
libpci3:amd64                    install
libpciaccess0:amd64                install
libpciaccess0:i386                install
libpcre16-3:amd64                install
libpcre3:amd64                    install
libpcre3:i386                    install
libpcre3-dev:amd64                install
libpcre32-3:amd64                install
libpcrecpp0v5:amd64                install
libpcsclite1:amd64                install
libpeas-1.0-0:amd64                install
libpeas-1.0-0-python3loader            install
libpeas-common                    install
libperl4-corelibs-perl                install
libperl5.22:amd64                install
libperlio-gzip-perl                install
libphonon4:amd64                install
libphonon4qt5-4:amd64                install
libpipeline1:amd64                install
libpixman-1-0:amd64                install
libpixman-1-dev                    install
libplasma3                    install
libplist3:amd64                    install
libplymouth4:amd64                install
libpng12-0:amd64                install
libpng12-0:i386                    install
libpng12-dev:amd64                install
libpolkit-agent-1-0:amd64            install
libpolkit-backend-1-0:amd64            install
libpolkit-gobject-1-0:amd64            install
libpolkit-qt-1-1:amd64                install
libpolkit-qt5-1-1:amd64                install
libpoppler-glib8:amd64                install
libpoppler58:amd64                install
libpopt0:amd64                    install
libportaudio2:amd64                install
libportmidi-dev                    install
libportmidi0                    install
libpostproc-ffmpeg53:amd64            install
libprocps4:amd64                install
libprotobuf-lite9v5:amd64            install
libprotobuf9v5:amd64                install
libproxy-tools                    install
libproxy1-plugin-gsettings:amd64        install
libproxy1-plugin-networkmanager:amd64        install
libproxy1v5:amd64                install
libpst4:amd64                    install
libpthread-stubs0-dev:amd64            install
libpulse-dev:amd64                install
libpulse-mainloop-glib0:amd64            install
libpulse0:amd64                    install
libpulse0:i386                    install
libpulsedsp:amd64                install
libpurple-bin                    install
libpurple0                    install
libpwquality-common                install
libpwquality1:amd64                install
libpyside-py3-1.2:amd64                install
libpyside1.2:amd64                install
libpython-dev:amd64                install
libpython-stdlib:amd64                install
libpython2.7:amd64                install
libpython2.7-dev:amd64                install
libpython2.7-minimal:amd64            install
libpython2.7-stdlib:amd64            install
libpython3-dev:amd64                install
libpython3-stdlib:amd64                install
libpython3.5:amd64                install
libpython3.5-dev:amd64                install
libpython3.5-minimal:amd64            install
libpython3.5-stdlib:amd64            install
libqca2:amd64                    install
libqca2-plugins:amd64                install
libqmi-glib1:amd64                install
libqmi-proxy                    install
libqpdf17:amd64                    install
libqqwing2v5:amd64                install
libqt4-dbus:amd64                install
libqt4-declarative:amd64            install
libqt4-designer:amd64                install
libqt4-help:amd64                install
libqt4-network:amd64                install
libqt4-opengl:amd64                install
libqt4-qt3support:amd64                install
libqt4-script:amd64                install
libqt4-scripttools:amd64            install
libqt4-sql:amd64                install
libqt4-sql-sqlite:amd64                install
libqt4-svg:amd64                install
libqt4-test:amd64                install
libqt4-xml:amd64                install
libqt4-xmlpatterns:amd64            install
libqt5core5a:amd64                install
libqt5dbus5:amd64                install
libqt5feedback5:amd64                install
libqt5gui5:amd64                install
libqt5multimedia5:amd64                install
libqt5network5:amd64                install
libqt5opengl5:amd64                install
libqt5organizer5:amd64                install
libqt5positioning5:amd64            install
libqt5printsupport5:amd64            install
libqt5qml5:amd64                install
libqt5quick5:amd64                install
libqt5quicktest5:amd64                install
libqt5quickwidgets5:amd64            install
libqt5script5:amd64                install
libqt5sql5:amd64                install
libqt5sql5-sqlite:amd64                install
libqt5svg5:amd64                install
libqt5test5:amd64                install
libqt5waylandclient5:amd64            install
libqt5webkit5:amd64                install
libqt5widgets5:amd64                install
libqt5x11extras5:amd64                install
libqt5xml5:amd64                install
libqtcore4:amd64                install
libqtdbus4:amd64                install
libqtgui4:amd64                    install
libqtwebkit4:amd64                install
libquadmath0:amd64                install
libquicktime2:amd64                install
libquvi-scripts                    install
libquvi7:amd64                    install
libraptor2-0:amd64                install
librarian0                    install
librasqal3:amd64                install
libraw1394-11:amd64                install
libraw15:amd64                    install
librdf0:amd64                    install
libreadline6:amd64                install
libreoffice-avmedia-backend-gstreamer        install
libreoffice-base-core                install
libreoffice-calc                install
libreoffice-common                install
libreoffice-core                install
libreoffice-draw                install
libreoffice-gnome                install
libreoffice-gtk                    install
libreoffice-help-en-us                install
libreoffice-impress                install
libreoffice-math                install
libreoffice-ogltrans                install
libreoffice-pdfimport                install
libreoffice-style-breeze            install
libreoffice-style-galaxy            install
libreoffice-writer                install
libresid-builder0c2a                install
librest-0.7-0:amd64                install
librevenge-0.0-0:amd64                install
librhythmbox-core9:amd64            install
libroken18-heimdal:amd64            install
libroken18-heimdal:i386                install
librsvg2-2:amd64                install
librsvg2-common:amd64                install
librtmp1:amd64                    install
librubberband2v5:amd64                install
librygel-core-2.6-2                install
librygel-db-2.6-2                install
librygel-renderer-2.6-2                install
librygel-renderer-gst-2.6-2            install
librygel-server-2.6-2                install
libsamplerate0:amd64                install
libsamplerate0:i386                install
libsane:amd64                    install
libsane:i386                    install
libsane-common                    install
libsane-hpaio:amd64                install
libsasl2-2:amd64                install
libsasl2-2:i386                    install
libsasl2-modules:amd64                install
libsasl2-modules:i386                install
libsasl2-modules-db:amd64            install
libsasl2-modules-db:i386            install
libsbc1:amd64                    install
libschroedinger-1.0-0:amd64            install
libsdl-image1.2:amd64                install
libsdl-image1.2-dev:amd64            install
libsdl-mixer1.2:amd64                install
libsdl-mixer1.2-dev:amd64            install
libsdl-ttf2.0-0:amd64                install
libsdl-ttf2.0-dev:amd64                install
libsdl1.2-dev                    install
libsdl1.2debian:amd64                install
libsdl1.2debian:i386                install
libsdl2-2.0-0:amd64                install
libseccomp2:amd64                install
libsecret-1-0:amd64                install
libsecret-common                install
libselinux1:amd64                install
libselinux1:i386                install
libsemanage-common                install
libsemanage1:amd64                install
libsensors4:amd64                install
libsepol1:amd64                    install
libserf-1-1:amd64                install
libsgutils2-2                    install
libshiboken-py3-1.2v5:amd64            install
libshiboken1.2v5:amd64                install
libshine3:amd64                    install
libshout3:amd64                    install
libsidplay1v5                    install
libsidplay2v5                    install
libsigc++-2.0-0v5:amd64                install
libsignon-extension1:amd64            install
libsignon-glib1:amd64                install
libsignon-plugins-common1:amd64            install
libsignon-qt5-1:amd64                install
libsigsegv2:amd64                install
libslang2:amd64                    install
libslang2:i386                    install
libslang2-dev:amd64                install
libsm-dev:amd64                    install
libsm6:amd64                    install
libsm6:i386                    install
libsmartcols1:amd64                install
libsmbclient:amd64                install
libsmpeg-dev                    install
libsmpeg0:amd64                    install
libsnappy1v5:amd64                install
libsndfile1:amd64                install
libsndfile1:i386                install
libsndio6.1:amd64                install
libsnmp-base                    install
libsnmp30:amd64                    install
libsocket6-perl                    install
libsodium18:amd64                install
libsofia-sip-ua-glib3                install
libsofia-sip-ua0                install
libsolid4                    install
libsonic0:amd64                    install
libsoundtouch1:amd64                install
libsoup-gnome2.4-1:amd64            install
libsoup2.4-1:amd64                install
libsoxr0:amd64                    install
libspandsp2:amd64                install
libspectre1:amd64                install
libspeechd2:amd64                install
libspeex1:amd64                    install
libspeexdsp1:amd64                install
libspeexdsp1:i386                install
libspice-client-glib-2.0-8:amd64        install
libspice-client-gtk-3.0-4:amd64            install
libsqlite3-0:amd64                install
libsqlite3-0:i386                install
libsrtp0                    install
libss2:amd64                    install
libssh-4:amd64                    install
libssh-gcrypt-4:amd64                install
libssh2-1:amd64                    install
libssl1.0.0:amd64                install
libssl1.0.0:i386                install
libstartup-notification0:amd64            install
libstdc++-5-dev:amd64                install
libstdc++6:amd64                install
libstdc++6:i386                    install
libstreamanalyzer0v5                install
libstreams0v5                    install
libsub-name-perl                install
libsuitesparseconfig4.4.6:amd64            install
libsvn1:amd64                    install
libswresample-ffmpeg1:amd64            install
libswscale-ffmpeg3:amd64            install
libsyndication4                    install
libsys-hostname-long-perl            install
libsystemd0:amd64                install
libsystemd0:i386                install
libtag1v5:amd64                    install
libtag1v5-vanilla:amd64                install
libtagc0:amd64                    install
libtalloc2:amd64                install
libtasn1-6:amd64                install
libtasn1-6:i386                    install
libtbb2:amd64                    install
libtcl8.6:amd64                    install
libtdb1:amd64                    install
libtelepathy-farstream3:amd64            install
libtelepathy-glib0:amd64            install
libtelepathy-logger3:amd64            install
libtevent0:amd64                install
libtext-charwidth-perl                install
libtext-iconv-perl                install
libtext-levenshtein-perl            install
libtext-wrapi18n-perl                install
libthai-data                    install
libthai0:amd64                    install
libtheora0:amd64                install
libthreadweaver4                install
libtie-ixhash-perl                install
libtiff5:amd64                    install
libtiff5:i386                    install
libtiff5-dev:amd64                install
libtiffxx5:amd64                install
libtimedate-perl                install
libtimezonemap-data                install
libtimezonemap1:amd64                install
libtinfo5:amd64                    install
libtinfo5:i386                    install
libtinyxml2.6.2v5:amd64                install
libtk8.6:amd64                    install
libtorrent-rasterbar8                install
libtotem-plparser-common            install
libtotem-plparser18:amd64            install
libtotem0:amd64                    install
libtracker-control-1.0-0:amd64            install
libtracker-miner-1.0-0:amd64            install
libtracker-sparql-1.0-0:amd64            install
libtsan0:amd64                    install
libtwolame0:amd64                install
libtxc-dxtn-s2tc0:amd64                install
libtxc-dxtn-s2tc0:i386                install
libubsan0:amd64                    install
libubuntugestures5:amd64            install
libubuntutoolkit5:amd64                install
libudev1:amd64                    install
libudev1:i386                    install
libudisks2-0:amd64                install
libumfpack5.7.1:amd64                install
libunistring0:amd64                install
libunity-action-qt1:amd64            install
libunity-control-center1            install
libunity-core-6.0-9:amd64            install
libunity-misc4                    install
libunity-protocol-private0:amd64        install
libunity-scopes-json-def-desktop        install
libunity-settings-daemon1:amd64            install
libunity-webapps0:amd64                install
libunity9:amd64                    install
libunwind8                    install
libupnp6                    install
libupower-glib3:amd64                install
liburi-perl                    install
liburl-dispatcher1:amd64            install
libusageenvironment3:amd64            install
libusb-0.1-4:amd64                install
libusb-1.0-0:amd64                install
libusb-1.0-0:i386                install
libusbmuxd4:amd64                install
libusbredirhost1:amd64                install
libusbredirparser1:amd64            install
libustr-1.0-1:amd64                install
libutempter0:amd64                install
libuuid-perl                    install
libuuid1:amd64                    install
libuuid1:i386                    install
libv4l-0:amd64                    install
libv4l-0:i386                    install
libv4lconvert0:amd64                install
libv4lconvert0:i386                install
libva-drm1:amd64                install
libva-wayland1:amd64                install
libva-x11-1:amd64                install
libva1:amd64                    install
libvcdinfo0                    install
libvdpau1:amd64                    install
libvisio-0.1-1:amd64                install
libvisual-0.4-0:amd64                install
libvlc5                        install
libvlccore8                    install
libvncclient1:amd64                install
libvo-aacenc0:amd64                install
libvo-amrwbenc0:amd64                install
libvoikko1:amd64                install
libvorbis-dev:amd64                install
libvorbis0a:amd64                install
libvorbis0a:i386                install
libvorbisenc2:amd64                install
libvorbisenc2:i386                install
libvorbisfile3:amd64                install
libvpx3:amd64                    install
libvpx3:i386                    install
libvte-2.91-0:amd64                install
libvte-2.91-common                install
libvte-common                    install
libvte-dev                    install
libvte-doc                    install
libvte9                        install
libwacom-bin                    install
libwacom-common                    install
libwacom2:amd64                    install
libwavpack1:amd64                install
libwayland-client0:amd64            install
libwayland-cursor0:amd64            install
libwayland-egl1-mesa:amd64            install
libwayland-server0:amd64            install
libwbclient0:amd64                install
libwebkit2gtk-4.0-37:amd64            install
libwebkit2gtk-4.0-37-gtk2:amd64            install
libwebkitgtk-3.0-0:amd64            install
libwebkitgtk-3.0-common                install
libwebp-dev:amd64                install
libwebp5:amd64                    install
libwebpdemux1:amd64                install
libwebpmux1:amd64                install
libwebrtc-audio-processing-0:amd64        install
libwhoopsie-preferences0            install
libwhoopsie0:amd64                install
libwildmidi-config                install
libwildmidi1:amd64                install
libwind0-heimdal:amd64                install
libwind0-heimdal:i386                install
libwinpr-crt0.1:amd64                install
libwinpr-dsparse0.1:amd64            install
libwinpr-environment0.1:amd64            install
libwinpr-file0.1:amd64                install
libwinpr-handle0.1:amd64            install
libwinpr-heap0.1:amd64                install
libwinpr-input0.1:amd64                install
libwinpr-interlocked0.1:amd64            install
libwinpr-library0.1:amd64            install
libwinpr-path0.1:amd64                install
libwinpr-pool0.1:amd64                install
libwinpr-registry0.1:amd64            install
libwinpr-rpc0.1:amd64                install
libwinpr-sspi0.1:amd64                install
libwinpr-synch0.1:amd64                install
libwinpr-sysinfo0.1:amd64            install
libwinpr-thread0.1:amd64            install
libwinpr-utils0.1:amd64                install
libwmf-bin                    install
libwmf0.2-7:amd64                install
libwmf0.2-7-gtk                    install
libwnck-3-0:amd64                install
libwnck-3-common                install
libwnck-common                    install
libwnck22:amd64                    install
libwpd-0.10-10:amd64                install
libwpg-0.3-3:amd64                install
libwps-0.4-4:amd64                install
libwrap0:amd64                    install
libwrap0:i386                    install
libwww-perl                    install
libwww-robotrules-perl                install
libx11-6:amd64                    install
libx11-6:i386                    install
libx11-data                    install
libx11-dev:amd64                install
libx11-doc                    install
libx11-protocol-perl                install
libx11-xcb-dev:amd64                install
libx11-xcb1:amd64                install
libx11-xcb1:i386                install
libx264-148:amd64                install
libx265-79:amd64                install
libx86-1:amd64                    install
libxapian22v5:amd64                install
libxatracker2:amd64                install
libxau-dev:amd64                install
libxau6:amd64                    install
libxau6:i386                    install
libxaw7:amd64                    install
libxcb-composite0:amd64                install
libxcb-damage0:amd64                install
libxcb-dri2-0:amd64                install
libxcb-dri2-0:i386                install
libxcb-dri2-0-dev:amd64                install
libxcb-dri3-0:amd64                install
libxcb-dri3-0:i386                install
libxcb-dri3-dev:amd64                install
libxcb-glx0:amd64                install
libxcb-glx0:i386                install
libxcb-glx0-dev:amd64                install
libxcb-icccm4:amd64                install
libxcb-image0:amd64                install
libxcb-keysyms1:amd64                install
libxcb-present-dev:amd64            install
libxcb-present0:amd64                install
libxcb-present0:i386                install
libxcb-randr0:amd64                install
libxcb-randr0-dev:amd64                install
libxcb-render-util0:amd64            install
libxcb-render0:amd64                install
libxcb-render0-dev:amd64            install
libxcb-shape0:amd64                install
libxcb-shape0-dev:amd64                install
libxcb-shm0:amd64                install
libxcb-shm0-dev:amd64                install
libxcb-sync-dev:amd64                install
libxcb-sync1:amd64                install
libxcb-sync1:i386                install
libxcb-util1:amd64                install
libxcb-xf86dri0:amd64                install
libxcb-xfixes0:amd64                install
libxcb-xfixes0-dev:amd64            install
libxcb-xkb1:amd64                install
libxcb-xv0:amd64                install
libxcb1:amd64                    install
libxcb1:i386                    install
libxcb1-dev:amd64                install
libxcomposite-dev                install
libxcomposite1:amd64                install
libxcomposite1:i386                install
libxcursor-dev:amd64                install
libxcursor1:amd64                install
libxcursor1:i386                install
libxdamage-dev:amd64                install
libxdamage1:amd64                install
libxdamage1:i386                install
libxdmcp-dev:amd64                install
libxdmcp6:amd64                    install
libxdmcp6:i386                    install
libxext-dev:amd64                install
libxext6:amd64                    install
libxext6:i386                    install
libxfixes-dev:amd64                install
libxfixes3:amd64                install
libxfixes3:i386                    install
libxfont1:amd64                    install
libxfreerdp-client1.1:amd64            install
libxft-dev                    install
libxft2:amd64                    install
libxi-dev                    install
libxi6:amd64                    install
libxi6:i386                    install
libxinerama-dev:amd64                install
libxinerama1:amd64                install
libxinerama1:i386                install
libxkbcommon-x11-0:amd64            install
libxkbcommon0:amd64                install
libxkbfile1:amd64                install
libxklavier16:amd64                install
libxml-parser-perl                install
libxml-twig-perl                install
libxml-xpathengine-perl                install
libxml2:amd64                    install
libxml2:i386                    install
libxml2-utils                    install
libxmu6:amd64                    install
libxmuu1:amd64                    install
libxpm4:amd64                    install
libxpm4:i386                    install
libxrandr-dev:amd64                install
libxrandr2:amd64                install
libxrandr2:i386                    install
libxrender-dev:amd64                install
libxrender1:amd64                install
libxrender1:i386                install
libxres1:amd64                    install
libxshmfence-dev:amd64                install
libxshmfence1:amd64                install
libxshmfence1:i386                install
libxslt1.1:amd64                install
libxslt1.1:i386                    install
libxss1:amd64                    install
libxt6:amd64                    install
libxt6:i386                    install
libxtables11:amd64                install
libxtst6:amd64                    install
libxv1:amd64                    install
libxvidcore4:amd64                install
libxvmc1:amd64                    install
libxxf86dga1:amd64                install
libxxf86vm-dev:amd64                install
libxxf86vm1:amd64                install
libxxf86vm1:i386                install
libyajl2:amd64                    install
libyaml-0-2:amd64                install
libyaml-libyaml-perl                install
libyaml-tiny-perl                install
libyelp0:amd64                    install
libytnef0:amd64                    install
libzapojit-0.0-0                install
libzbar0:amd64                    install
libzeitgeist-1.0-1:amd64            install
libzeitgeist-2.0-0:amd64            install
libzephyr4:amd64                install
libzmq5:amd64                    install
libzvbi-common                    install
libzvbi0:amd64                    install
light-themes                    install
lightdm                        install
lightsoff                    install
lintian                        install
linux-base                    install
linux-firmware                    install
linux-generic                    install
linux-headers-4.4.0-21                install
linux-headers-4.4.0-21-generic            install
linux-headers-4.4.0-22                install
linux-headers-4.4.0-22-generic            install
linux-headers-4.4.0-24                install
linux-headers-4.4.0-24-generic            install
linux-headers-generic                install
linux-image-4.4.0-21-generic            install
linux-image-4.4.0-22-generic            install
linux-image-4.4.0-24-generic            install
linux-image-extra-4.4.0-21-generic        install
linux-image-extra-4.4.0-22-generic        install
linux-image-extra-4.4.0-24-generic        install
linux-image-generic                install
linux-libc-dev:amd64                install
linux-sound-base                install
locales                        install
login                        install
logrotate                    install
lp-solve                    install
lsb-base                    install
lsb-release                    install
lshw                        install
lsof                        install
ltrace                        install
lua-lpeg:amd64                    install
make                        install
makedev                        install
man-db                        install
manpages                    install
manpages-dev                    install
mawk                        install
mcp-account-manager-uoa                install
media-player-info                install
memtest86+                    install
menu                        install
mercurial                    install
mercurial-common                install
mesa-common-dev:amd64                install
mesa-vdpau-drivers:amd64            install
metacity                    install
metacity-common                    install
mime-support                    install
mlocate                        install
mobile-broadband-provider-info            install
modemmanager                    install
mount                        install
mountall                    install
mousetweaks                    install
mpv                        install
mscompress                    install
mtools                        install
mtr-tiny                    install
multiarch-support                install
mutter                        install
mutter-common                    install
mysql-common                    install
mythes-en-us                    install
nano                        install
nautilus                    install
nautilus-data                    install
nautilus-sendto                    install
nautilus-share                    install
ncurses-base                    install
ncurses-bin                    install
ncurses-term                    install
ndiff                        install
net-tools                    install
netbase                        install
netcat-openbsd                    install
netpbm                        install
network-manager                    install
network-manager-gnome                install
network-manager-pptp                install
network-manager-pptp-gnome            install
nmap                        install
notify-osd                    install
notify-osd-icons                install
ntfs-3g                        install
ntrack-module-libnl-0                install
nux-tools                    install
ocl-icd-libopencl1:amd64            install
ocl-icd-libopencl1:i386                install
odbcinst                    install
odbcinst1debian2:amd64                install
onboard                        install
onboard-data                    install
openoffice.org-hyphenation            install
openprinting-ppds                install
openssh-client                    install
openssh-server                    install
openssh-sftp-server                install
openssl                        install
os-prober                    install
overlay-scrollbar                install
overlay-scrollbar-gtk2:amd64            install
oxideqt-codecs-extra:amd64            install
oxygen-icon-theme                install
oxygen5-icon-theme                install
p11-kit                        install
p11-kit-modules:amd64                install
p11-kit-modules:i386                install
p7zip                        install
p7zip-full                    install
parted                        install
passwd                        install
patch                        install
patchutils                    install
pciutils                    install
pcmciautils                    install
perl                        install
perl-base                    install
perl-modules-5.22                install
phonon:amd64                    install
phonon-backend-gstreamer:amd64            install
phonon-backend-gstreamer-common:amd64        install
pidgin-data                    install
pinentry-gnome3                    install
pkg-config                    install
plainbox-provider-checkbox            install
plainbox-provider-resource-generic        install
plainbox-secure-policy                install
plasma-framework                install
plasma-scriptengine-javascript            install
plymouth                    install
plymouth-label                    install
plymouth-theme-ubuntu-logo            install
plymouth-theme-ubuntu-text            install
pm-utils                    install
po-debconf                    install
polari                        install
policykit-1                    install
policykit-1-gnome                install
policykit-desktop-privileges            install
poppler-data                    install
poppler-utils                    install
popularity-contest                install
powermgmt-base                    install
ppp                        install
pppconfig                    install
pppoeconf                    install
pptp-linux                    install
printer-driver-brlaser                install
printer-driver-c2esp                install
printer-driver-foo2zjs                install
printer-driver-foo2zjs-common            install
printer-driver-gutenprint            install
printer-driver-hpcups                install
printer-driver-min12xxw                install
printer-driver-pnm2ppa                install
printer-driver-postscript-hp            install
printer-driver-ptouch                install
printer-driver-pxljr                install
printer-driver-sag-gdi                install
printer-driver-splix                install
procps                        install
psmisc                        install
pulseaudio                    install
pulseaudio-module-bluetooth            install
pulseaudio-module-x11                install
pulseaudio-utils                install
pyotherside                    install
python                        install
python-appindicator                install
python-apt-common                install
python-attr                    install
python-blinker                    install
python-bs4                    install
python-cairo                    install
python-cffi-backend                install
python-chardet                    install
python-cryptography                install
python-cycler                    install
python-dateutil                    install
python-dbus                    install
python-decorator                install
python-dev                    install
python-enum34                    install
python-flask                    install
python-gconf                    install
python-gi                    install
python-glade2                    install
python-gnome2                    install
python-gobject                    install
python-gobject-2                install
python-gtk2                    install
python-html5lib                    install
python-idna                    install
python-imaging                    install
python-ipaddress                install
python-itsdangerous                install
python-jinja2                    install
python-libtorrent                install
python-lxml                    install
python-markupsafe                install
python-matplotlib                install
python-matplotlib-data                install
python-mechanize                install
python-minimal                    install
python-mysqldb                    install
python-nmap                    install
python-notify                    install
python-numpy                    install
python-openssl                    install
python-pam                    install
python-pil:amd64                install
python-pil.imagetk:amd64            install
python-pkg-resources                install
python-pyasn1                    install
python-pyasn1-modules                install
python-pyatspi                    install
python-pygame                    install
python-pyinotify                install
python-pyorbit                    install
python-pyparsing                install
python-pyside                    install
python-pyside.phonon                install
python-pyside.qtcore                install
python-pyside.qtdeclarative            install
python-pyside.qtgui                install
python-pyside.qthelp                install
python-pyside.qtnetwork                install
python-pyside.qtopengl                install
python-pyside.qtscript                install
python-pyside.qtsql                install
python-pyside.qtsvg                install
python-pyside.qttest                install
python-pyside.qtuitools                install
python-pyside.qtwebkit                install
python-pyside.qtxml                install
python-scipy                    install
python-serial                    install
python-service-identity                install
python-setuptools                install
python-six                    install
python-talloc                    install
python-tk                    install
python-twisted-bin                install
python-twisted-core                install
python-twisted-web                install
python-tz                    install
python-werkzeug                    install
python-wnck                    install
python-xdg                    install
python-zope.interface                install
python2.7                    install
python2.7-dev                    install
python2.7-minimal                install
python3                        install
python3-apport                    install
python3-apt                    install
python3-aptdaemon                install
python3-aptdaemon.gtk3widgets            install
python3-aptdaemon.pkcompat            install
python3-blinker                    install
python3-brlapi                    install
python3-bs4                    install
python3-cairo                    install
python3-cffi-backend                install
python3-chardet                    install
python3-checkbox-support            install
python3-commandnotfound                install
python3-cryptography                install
python3-cups                    install
python3-cupshelpers                install
python3-cycler                    install
python3-dateutil                install
python3-dbus                    install
python3-debian                    install
python3-decorator                install
python3-defer                    install
python3-dev                    install
python3-distupgrade                install
python3-feedparser                install
python3-gdbm:amd64                install
python3-gi                    install
python3-gi-cairo                install
python3-guacamole                install
python3-html5lib                install
python3-httplib2                install
python3-idna                    install
python3-jinja2                    install
python3-jwt                    install
python3-louis                    install
python3-lxml                    install
python3-mako                    install
python3-markupsafe                install
python3-matplotlib                install
python3-minimal                    install
python3-numpy                    install
python3-oauthlib                install
python3-padme                    install
python3-pexpect                    install
python3-pil:amd64                install
python3-pkg-resources                install
python3-plainbox                install
python3-problem-report                install
python3-ptyprocess                install
python3-pyasn1                    install
python3-pyatspi                    install
python3-pycurl                    install
python3-pyparsing                install
python3-pyside                    install
python3-pyside.phonon                install
python3-pyside.qtcore                install
python3-pyside.qtdeclarative            install
python3-pyside.qtgui                install
python3-pyside.qthelp                install
python3-pyside.qtnetwork            install
python3-pyside.qtopengl                install
python3-pyside.qtscript                install
python3-pyside.qtsql                install
python3-pyside.qtsvg                install
python3-pyside.qttest                install
python3-pyside.qtuitools            install
python3-pyside.qtwebkit                install
python3-pyside.qtxml                install
python3-renderpm:amd64                install
python3-reportlab                install
python3-reportlab-accel:amd64            install
python3-requests                install
python3-scipy                    install
python3-setuptools                install
python3-six                    install
python3-software-properties            install
python3-speechd                    install
python3-systemd                    install
python3-tk                    install
python3-tz                    install
python3-uno                    install
python3-update-manager                install
python3-urllib3                    install
python3-xdg                    install
python3-xkit                    install
python3-xlsxwriter                install
python3.5                    install
python3.5-dev                    install
python3.5-minimal                install
qdbus                        install
qml-module-io-thp-pyotherside:amd64        install
qml-module-org-kde-activities:amd64        install
qml-module-org-kde-kquickcontrols:amd64        install
qml-module-org-kde-kquickcontrolsaddons:amd64    install
qml-module-qt-labs-folderlistmodel:amd64    install
qml-module-qt-labs-settings:amd64        install
qml-module-qtfeedback:amd64            install
qml-module-qtgraphicaleffects:amd64        install
qml-module-qtquick-controls:amd64        install
qml-module-qtquick-dialogs:amd64        install
qml-module-qtquick-layouts:amd64        install
qml-module-qtquick-privatewidgets:amd64        install
qml-module-qtquick-window2:amd64        install
qml-module-qtquick2:amd64            install
qml-module-qttest:amd64                install
qml-module-ubuntu-components:amd64        install
qml-module-ubuntu-layouts:amd64            install
qml-module-ubuntu-onlineaccounts:amd64        install
qml-module-ubuntu-performancemetrics:amd64    install
qml-module-ubuntu-test:amd64            install
qml-module-ubuntu-web:amd64            install
qmlscene                    install
qpdf                        install
qt-at-spi:amd64                    install
qtchooser                    install
qtcore4-l10n                    install
qtdeclarative5-accounts-plugin:amd64        install
qtdeclarative5-dev-tools            install
qtdeclarative5-qtquick2-plugin:amd64        install
qtdeclarative5-test-plugin:amd64        install
qtdeclarative5-ubuntu-ui-toolkit-plugin        install
qtdeclarative5-unity-action-plugin:amd64    install
qttranslations5-l10n                install
qtwayland5:amd64                install
quadrapassel                    install
rarian-compat                    install
readline-common                    install
realmd                        install
remmina                        install
remmina-common                    install
remmina-plugin-rdp                install
remmina-plugin-vnc                install
rename                        install
resolvconf                    install
rfkill                        install
rhythmbox                    install
rhythmbox-data                    install
rhythmbox-plugin-cdrecorder            install
rhythmbox-plugin-zeitgeist            install
rhythmbox-plugins                install
rsync                        install
rsyslog                        install
rtkit                        install
rtmpdump                    install
rygel                        install
rygel-playbin                    install
rygel-tracker                    install
samba-libs:amd64                install
sane-utils                    install
sbsigntool                    install
seahorse                    install
seahorse-daemon                    install
secureboot-db                    install
sed                        install
sensible-utils                    install
session-migration                install
session-shortcuts                install
sessioninstaller                install
sgml-base                    install
sgml-data                    install
shared-mime-info                install
shotwell                    install
shotwell-common                    install
signon-keyring-extension            install
signon-plugin-oauth2                install
signon-plugin-password                install
signon-ui                    install
signon-ui-service                install
signon-ui-x11                    install
signond                        install
simple-scan                    install
snapd                        install
sni-qt:amd64                    install
software-properties-common            install
software-properties-gtk                install
sonnet-plugins                    install
sound-theme-freedesktop                install
soundconverter                    install
speech-dispatcher                install
speech-dispatcher-audio-plugins:amd64        install
spice-client-glib-usb-acl-helper        install
squashfs-tools                    install
ssh                        install
ssh-import-id                    install
ssl-cert                    install
steam:i386                    install
strace                        install
subversion                    install
sudo                        install
suru-icon-theme                    install
swell-foop                    install
synaptic                    install
syslinux                    install
syslinux-common                    install
syslinux-legacy                    install
system-config-printer-common            install
system-config-printer-gnome            install
system-config-printer-udev            install
systemd                        install
systemd-sysv                    install
sysv-rc                        install
sysvinit-utils                    install
t1utils                        install
tali                        install
tar                        install
tcl                        install
tcl8.6                        install
tcpd                        install
tcpdump                        install
telepathy-gabble                install
telepathy-haze                    install
telepathy-idle                    install
telepathy-logger                install
telepathy-mission-control-5            install
telepathy-rakia                    install
telepathy-salut                    install
telnet                        install
thermald                    install
thunderbird                    install
thunderbird-gnome-support            install
thunderbird-locale-en                install
thunderbird-locale-en-us            install
time                        install
tk                        install
tk8.6                        install
tk8.6-blt2.5                    install
tmux                        install
tor                        install
tor-geoipdb                    install
torsocks                    install
toshset                        install
totem                        install
totem-common                    install
totem-plugins                    install
tracker                        install
tracker-extract                    install
tracker-gui                    install
tracker-miner-fs                install
transfig                    install
transmission-common                install
transmission-gtk                install
ttf-ancient-fonts-symbola            install
ttf-bitstream-vera                install
ttf-mscorefonts-installer            install
ttf-ubuntu-font-family                install
ttf-wqy-microhei                install
tzdata                        install
ubuntu-artwork                    install
ubuntu-core-launcher                install
ubuntu-desktop                    install
ubuntu-docs                    install
ubuntu-drivers-common                install
ubuntu-keyring                    install
ubuntu-minimal                    install
ubuntu-mobile-icons                install
ubuntu-mono                    install
ubuntu-release-upgrader-core            install
ubuntu-release-upgrader-gtk            install
ubuntu-restricted-addons            install
ubuntu-restricted-extras            install
ubuntu-session                    install
ubuntu-settings                    install
ubuntu-software                    install
ubuntu-sounds                    install
ubuntu-standard                    install
ubuntu-system-service                install
ubuntu-touch-sounds                install
ubuntu-ui-toolkit-theme                install
ubuntu-wallpapers                install
ubuntu-wallpapers-xenial            install
ucf                        install
udev                        install
udisks2                        install
ufw                        install
unattended-upgrades                install
unetbootin                    install
unetbootin-translations                install
unity                        install
unity-accessibility-profiles            install
unity-asset-pool                install
unity-control-center                install
unity-control-center-faces            install
unity-control-center-signon            install
unity-greeter                    install
unity-lens-applications                install
unity-lens-files                install
unity-lens-music                install
unity-lens-photos                install
unity-lens-video                install
unity-schemas                    install
unity-scope-calculator                install
unity-scope-chromiumbookmarks            install
unity-scope-colourlovers            install
unity-scope-devhelp                install
unity-scope-firefoxbookmarks            install
unity-scope-gdrive                install
unity-scope-home                install
unity-scope-manpages                install
unity-scope-openclipart                install
unity-scope-texdoc                install
unity-scope-tomboy                install
unity-scope-video-remote            install
unity-scope-virtualbox                install
unity-scope-yelp                install
unity-scope-zotero                install
unity-scopes-master-default            install
unity-scopes-runner                install
unity-services                    install
unity-settings-daemon                install
unity-tweak-tool                install
unity-webapps-common                install
unity-webapps-qml                install
unity-webapps-service                install
unixodbc                    install
uno-libs3                    install
unoconv                        install
unrar                        install
unzip                        install
update-inetd                    install
update-manager                    install
update-manager-core                install
update-notifier                    install
update-notifier-common                install
upower                        install
upstart                        install
ure                        install
ureadahead                    install
usb-creator-common                install
usb-creator-gtk                    install
usb-modeswitch                    install
usb-modeswitch-data                install
usbmuxd                        install
usbutils                    install
util-linux                    install
uuid-runtime                    install
va-driver-all:amd64                install
vbetool                        install
vcdimager                    install
vdpau-driver-all:amd64                install
vdpau-va-driver:amd64                install
vim                        install
vim-common                    install
vim-runtime                    install
vim-tiny                    install
vinagre                        install
vino                        install
vlc                        install
vlc-data                    install
vlc-nox                        install
vlc-plugin-notify                install
vlc-plugin-samba                install
wamerican                    install
wbritish                    install
webapp-container                install
webbrowser-app                    install
wget                        install
whiptail                    install
whois                        install
whoopsie                    install
whoopsie-preferences                install
wine                        install
wine-gecko2.21:amd64                install
wine-gecko2.21:i386                install
wine-mono0.0.8                    install
wine1.6                        install
wine1.6-amd64                    install
wine1.6-i386:i386                install
winetricks                    install
wireless-regdb                    install
wireless-tools                    install
wodim                        install
wpasupplicant                    install
x11-apps                    install
x11-common                    install
x11-session-utils                install
x11-utils                    install
x11-xkb-utils                    install
x11-xserver-utils                install
x11proto-composite-dev                install
x11proto-core-dev                install
x11proto-damage-dev                install
x11proto-dri2-dev                install
x11proto-fixes-dev                install
x11proto-gl-dev                    install
x11proto-input-dev                install
x11proto-kb-dev                    install
x11proto-randr-dev                install
x11proto-render-dev                install
x11proto-xext-dev                install
x11proto-xf86vidmode-dev            install
x11proto-xinerama-dev                install
xauth                        install
xbitmaps                    install
xboard                        install
xbrlapi                        install
xchat-gnome                    install
xchat-gnome-common                install
xchat-gnome-indicator                install
xcursor-themes                    install
xdg-user-dirs                    install
xdg-user-dirs-gtk                install
xdg-utils                    install
xdiagnose                    install
xfonts-100dpi                    install
xfonts-base                    install
xfonts-encodings                install
xfonts-scalable                    install
xfonts-utils                    install
xinit                        install
xinput                        install
xkb-data                    install
xml-core                    install
xorg                        install
xorg-docs-core                    install
xorg-sgml-doctools                install
xserver-common                    install
xserver-xephyr                    install
xserver-xorg                    install
xserver-xorg-core                install
xserver-xorg-input-all                install
xserver-xorg-input-evdev            install
xserver-xorg-input-synaptics            install
xserver-xorg-input-vmmouse            install
xserver-xorg-input-wacom            install
xserver-xorg-video-all                install
xserver-xorg-video-amdgpu            install
xserver-xorg-video-ati                install
xserver-xorg-video-fbdev            install
xserver-xorg-video-intel            install
xserver-xorg-video-nouveau            install
xserver-xorg-video-qxl                install
xserver-xorg-video-radeon            install
xserver-xorg-video-vesa                install
xserver-xorg-video-vmware            install
xterm                        install
xtrans-dev                    install
xul-ext-ubufox                    install
xz-utils                    install
yelp                        install
yelp-xsl                    install
youtube-dl                    install
zeitgeist-core                    install
zeitgeist-datahub                install
zenity                        install
zenity-common                    install
zip                        install
zlib1g:amd64                    install
zlib1g:i386                    install
zlib1g-dev:amd64                install
zsnes:i386                    install



```

```
metulburr@ubuntu:~$ cat /proc/modules
firewire_ohci 40960 0 - Live 0x0000000000000000
firewire_core 65536 1 firewire_ohci, Live 0x0000000000000000
crc_itu_t 16384 1 firewire_core, Live 0x0000000000000000
btrfs 987136 0 - Live 0x0000000000000000
xor 24576 1 btrfs, Live 0x0000000000000000
raid6_pq 102400 1 btrfs, Live 0x0000000000000000
ufs 73728 0 - Live 0x0000000000000000
qnx4 16384 0 - Live 0x0000000000000000
hfsplus 106496 0 - Live 0x0000000000000000
hfs 57344 0 - Live 0x0000000000000000
minix 36864 0 - Live 0x0000000000000000
ntfs 98304 0 - Live 0x0000000000000000
msdos 20480 0 - Live 0x0000000000000000
jfs 180224 0 - Live 0x0000000000000000
xfs 966656 0 - Live 0x0000000000000000
libcrc32c 16384 1 xfs, Live 0x0000000000000000
cpuid 16384 0 - Live 0x0000000000000000
cdc_acm 36864 0 - Live 0x0000000000000000
nls_iso8859_1 16384 1 - Live 0x0000000000000000
intel_rapl 20480 0 - Live 0x0000000000000000
x86_pkg_temp_thermal 16384 0 - Live 0x0000000000000000
intel_powerclamp 16384 0 - Live 0x0000000000000000
snd_hda_codec_hdmi 53248 1 - Live 0x0000000000000000
coretemp 16384 0 - Live 0x0000000000000000
snd_hda_codec_realtek 81920 1 - Live 0x0000000000000000
snd_hda_codec_generic 77824 1 snd_hda_codec_realtek, Live 0x0000000000000000
snd_hda_intel 36864 3 - Live 0x0000000000000000
snd_hda_codec 135168 4 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel, Live 0x0000000000000000
kvm 536576 0 - Live 0x0000000000000000
snd_hda_core 73728 5 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
snd_hwdep 16384 1 snd_hda_codec, Live 0x0000000000000000
snd_pcm 106496 4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core, Live 0x0000000000000000
eeepc_wmi 16384 0 - Live 0x0000000000000000
snd_seq_midi 16384 0 - Live 0x0000000000000000
irqbypass 16384 1 kvm, Live 0x0000000000000000
joydev 20480 0 - Live 0x0000000000000000
asus_wmi 28672 1 eeepc_wmi, Live 0x0000000000000000
snd_seq_midi_event 16384 1 snd_seq_midi, Live 0x0000000000000000
input_leds 16384 0 - Live 0x0000000000000000
snd_rawmidi 32768 1 snd_seq_midi, Live 0x0000000000000000
sparse_keymap 16384 1 asus_wmi, Live 0x0000000000000000
snd_seq 69632 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
crct10dif_pclmul 16384 0 - Live 0x0000000000000000
snd_seq_device 16384 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
crc32_pclmul 16384 0 - Live 0x0000000000000000
snd_timer 32768 2 snd_pcm,snd_seq, Live 0x0000000000000000
aesni_intel 167936 0 - Live 0x0000000000000000
snd 81920 17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer, Live 0x0000000000000000
aes_x86_64 20480 1 aesni_intel, Live 0x0000000000000000
lrw 16384 1 aesni_intel, Live 0x0000000000000000
soundcore 16384 1 snd, Live 0x0000000000000000
gf128mul 16384 1 lrw, Live 0x0000000000000000
glue_helper 16384 1 aesni_intel, Live 0x0000000000000000
shpchp 36864 0 - Live 0x0000000000000000
ablk_helper 16384 1 aesni_intel, Live 0x0000000000000000
lpc_ich 24576 0 - Live 0x0000000000000000
mei_me 36864 0 - Live 0x0000000000000000
cryptd 20480 2 aesni_intel,ablk_helper, Live 0x0000000000000000
mei 98304 1 mei_me, Live 0x0000000000000000
serio_raw 16384 0 - Live 0x0000000000000000
mac_hid 16384 0 - Live 0x0000000000000000
binfmt_misc 20480 1 - Live 0x0000000000000000
parport_pc 32768 0 - Live 0x0000000000000000
ppdev 20480 0 - Live 0x0000000000000000
lp 20480 0 - Live 0x0000000000000000
parport 49152 3 parport_pc,ppdev,lp, Live 0x0000000000000000
autofs4 40960 2 - Live 0x0000000000000000
ses 20480 0 - Live 0x0000000000000000
enclosure 16384 1 ses, Live 0x0000000000000000
hid_logitech_hidpp 20480 0 - Live 0x0000000000000000
hid_logitech_dj 20480 0 - Live 0x0000000000000000
i915 1208320 8 - Live 0x0000000000000000
psmouse 126976 0 - Live 0x0000000000000000
i2c_algo_bit 16384 1 i915, Live 0x0000000000000000
drm_kms_helper 139264 1 i915, Live 0x0000000000000000
syscopyarea 16384 1 drm_kms_helper, Live 0x0000000000000000
pata_acpi 16384 0 - Live 0x0000000000000000
sysfillrect 16384 1 drm_kms_helper, Live 0x0000000000000000
r8169 81920 0 - Live 0x0000000000000000
sysimgblt 16384 1 drm_kms_helper, Live 0x0000000000000000
usbhid 49152 0 - Live 0x0000000000000000
fb_sys_fops 16384 1 drm_kms_helper, Live 0x0000000000000000
hid 118784 3 hid_logitech_hidpp,hid_logitech_dj,usbhid, Live 0x0000000000000000
drm 360448 10 i915,drm_kms_helper, Live 0x0000000000000000
uas 24576 0 - Live 0x0000000000000000
mii 16384 1 r8169, Live 0x0000000000000000
usb_storage 69632 3 uas, Live 0x0000000000000000
wmi 20480 1 asus_wmi, Live 0x0000000000000000
video 40960 2 asus_wmi,i915, Live 0x0000000000000000
fjes 28672 0 - Live 0x0000000000000000



```

```
metulburr@ubuntu:~$ lspci | grep VGA ; lsmod | grep "kms\|drm" ; find /dev -group video ; \> cat /proc/cmdline ; find /etc/modprobe.d/; cat /etc/modprobe.d/*kms* ; \
> ls /etc/X11/xorg.conf ; glxinfo | grep -i "vendor\|rendering" ; \
> grep LoadModule /var/log/Xorg.0.log
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
drm_kms_helper        139264  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  10 i915,drm_kms_helper
/dev/fb0
/dev/dri/card0
/dev/dri/renderD128
/dev/dri/controlD64
BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=8963e4c6-44cd-4a12-8fdd-b86e99ec3f89 ro quiet splash vt.handoff=7
/etc/modprobe.d/
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/mlx4.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/fbdev-blacklist.conf
/etc/modprobe.d/vmwgfx-fbdev.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/intel-microcode-blacklist.conf
/etc/modprobe.d/blacklist-watchdog.conf
cat: '/etc/modprobe.d/*kms*': No such file or directory
ls: cannot access '/etc/X11/xorg.conf': No such file or directory
The program 'glxinfo' is currently not installed. You can install it by typing:
sudo apt install mesa-utils
[    33.813] (II) LoadModule: "glx"
[    34.223] (II) LoadModule: "intel"
[    34.353] (II) LoadModule: "modesetting"
[    34.386] (II) LoadModule: "fbdev"
[    34.404] (II) LoadModule: "vesa"
[    34.447] (II) LoadModule: "fbdevhw"
[    34.484] (II) LoadModule: "dri2"
[    34.484] (II) LoadModule: "present"
[    34.958] (II) LoadModule: "evdev"
metulburr@ubuntu:~$ 



```

---

