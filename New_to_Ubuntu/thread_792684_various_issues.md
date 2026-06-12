---
title: "various issues"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by holnrew on 2008-05-13
Firstly I can't get the wireless to work, it recognises networks and tries to connect, but it keeps asking for the WEP key repeatedly even though I enter the right one. But now I tried installing a driver from intel and I've messed it up a bit, is there a way to roll back?

Secondly I'm using a laptop and the screen brightness controls are mapped to the function keys, the screen is very dim and it hurts my eyes to look at it for too long, is there a way i can reassign this function to the keys? and other things like volume controls.

Also would it be better to install the driver from Intel for the graphics chipset?

Many thanks in advance

---

### Post by Tatty on 2008-05-13
are you typing the WEP key in hex?  I find that for me the network manager will not accept a passphrase for 64bit WEP, so i have to find a hex generator to convert it.

I would love to know if there is a simpler way though.

---

### Post by mapes12 on 2008-05-13
In a Terminal window type:

```
sudo lshw
```

Then post the output code on this thread

---

### Post by holnrew on 2008-05-13
OK, thanks.

```
 description: Notebook
    product: DIXONSXP
    vendor: DIXONSXP
    version: 1.02
    serial: 0000000000
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2
  *-core
       description: Motherboard
       product: DIXONSXP
       vendor: DIXONSXP
       physical id: 0
       slot: Jumper settings can be described here.
     *-firmware
          description: BIOS
          vendor: DIXONSXP
          physical id: 0
          version: 1.02 (07/25/2007)
          size: 96KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot acpi usb smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 1801MHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
          configuration: id=1
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
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back
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
          physical id: 12
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
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
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1801MHz
          capacity: 1801MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
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
             configuration: driver=pcieport-driver
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
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:63:e4:ad
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
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
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 01
                serial: 00:03:0d:71:31:4d
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.6 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
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
             configuration: driver=pcieport-driver
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@0000:0a:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 module=ohci1394
           *-system
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.2
                bus info: pci@0000:0a:04.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=32 module=sdhci
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.3
                bus info: pci@0000:0a:04.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=32
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
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DX09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
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
     *-scsi
          physical id: 2
          bus info: usb@7:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 0H9AT00
             vendor: HTS42126
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 0811
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=ae47f70d
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 3752e9cd-42a7-41ad-84e3-1a65b76bc1ce
                size: 53GiB
                capacity: 53GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-05-14 00:32:34 filesystem=ext3 modified=2008-05-14 00:56:11 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-05-14 00:49:47 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 2384MiB
                capacity: 2384MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2384MiB
                   capabilities: nofs
  *-battery
       description: Lithium Ion Battery
       vendor: 0
       physical id: 1
       version: 0
       serial: 0
       slot: MAIN
       capacity: 31680mWh
       configuration: voltage=14.4V
russell@laptopsenbergen:~$ 


```

---

### Post by holnrew on 2008-05-13
The brightness is no longer a problem, it's at full brightness which is what I like anyway, although adjustment would be nice. 

> are you typing the WEP key in hex? I find that for me the network manager will not accept a passphrase for 64bit WEP, so i have to find a hex generator to convert it.

Where would I be able to obtain one of these?

Thanks in advance... I'm sure I will be returning a lot.

---

