---
title: "Wish to know if trackpad is working or not, if yes how to repair it."
date: 2012-01-27
forum: New to Ubuntu
---

### Post by ask_ on 2012-01-27
Hello, 

I am using Ubuntu 11.10 on a Sony Vaio laptop. I also have Windows Vista on it. The trackpad on the laptop isn't working since Vista days. I am a beginner in these matters somewhat, so I don't know if it is a hardware issue or a software driver issue. Hence I would like to confirm which of it is the problem. I will post the results of lspci command and lshw command run with sudo privileges . Please let me know what else command results I must post. If it is hardware problem i.e if it is damaged I have no way but to use  a USB mouse. 
If it is software problem please help me out with it.

lspci :-
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

lshw :-
```

    description: Notebook
    version: J0031WP4
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 family=N/A sku=N/A uuid=85A7CF80-0EBE-11DC-80A5-001A805BA842
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0121S5
          date: 12/19/2007
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: N/A
          size: 2501MHz
          capacity: 2501MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:fc000000-fc0fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fc100000-fc1fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fc504000-fc5043ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:fc500000-fc503fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f6000000-f7ffffff ioport:f0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f8000000-f9ffffff ioport:f2000000(size=33554432)
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 61
                serial: 00:1d:e0:b7:aa:93
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-14-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:f8000000-f8001fff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:fa000000-fbffffff ioport:f4000000(size=33554432)
           *-network
                description: Ethernet interface
                product: 88E8055 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 12
                serial: 00:1a:80:5b:a8:42
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:fa000000-fa003fff ioport:4000(size=256) memory:f4000000-f401ffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:c8000000-c9ffffff ioport:cc000000(size=33554432)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fc504400-fc5047ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:6000(size=4096) memory:fc200000-fc2fffff ioport:80000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:09:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:fc204000-fc204fff ioport:6000(size=256) ioport:6400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:09:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
                resources: irq:21 memory:fc206000-fc2067ff memory:fc200000-fc203fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:09:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:22 memory:fc205000-fc205fff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-852S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.90
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:1c00(size=8) ioport:18f4(size=4) ioport:18f8(size=8) ioport:18f0(size=4) ioport:18e0(size=16) ioport:18d0(size=16)
           *-disk
                description: ATA Disk
                product: FUJITSU MHY2250B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K41LT8126945
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=38d1a245
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: f275-60d8
                   size: 9532MiB
                   capacity: 9534MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-02-06 19:14:54 filesystem=ntfs label=Recovery state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 48bf9eb3-06a5-cc49-84bc-6b5fb90a6de8
                   size: 59GiB
                   capacity: 59GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-02-06 19:14:58 filesystem=ntfs label=local disk modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 164GiB
                   capacity: 164GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 135GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 26GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2038MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:84000000-840000ff ioport:1c20(size=32)
```

Thanks in advance.

---

### Post by ask_ on 2012-01-29
I am unable to see the trackpad in system settings , so does than mean it is a hardware problem ?

---

### Post by BC59 on 2012-01-29
Check here if you it helps you:
[http://dharmendralinuxdiary.blogspot.com/2011/11/ubuntu-1110-touchpad-problem.html](http://dharmendralinuxdiary.blogspot.com/2011/11/ubuntu-1110-touchpad-problem.html)

---

