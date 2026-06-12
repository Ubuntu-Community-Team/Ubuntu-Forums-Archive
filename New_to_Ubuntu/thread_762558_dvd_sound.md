---
title: "dvd sound"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by racgus on 2008-04-22
for some reason i don't have any sound. i've checked all possible options i can think of. the sound for the system itself isn't even working. can someone give me some ideas.

---

### Post by Michael.Godawski on 2008-04-22
What is your sound card? Can you please post the result of the terminal command:
```
sudo lshw
```

Did you checked the sound with the terminal command:
```
alsamixer
```

---

### Post by sayakb on 2008-04-22
At a terminal:
```
sudo apt-get install linux-backports-modules
```

---

### Post by racgus on 2008-04-22
> **Michael.Godawski said:**
> What is your sound card? Can you please post the result of the terminal command:
```
sudo lshw
```
 description: Notebook
    product: VGN-FS640_W
    vendor: Sony Corporation
    version: C300D7FU
    serial: 28198233-3448124
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: boot=normal chassis=notebook uuid=B932AA40-DF2D-11D4-8224-00014A5F9018
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0040J1 (03/11/2005)
          size: 110KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.13.8
          slot: N/A
          size: 1596MHz
          capacity: 1596MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 6
             slot: L3 Cache
             capabilities: burst data
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: SODIMM DDR 100 MHz (10.0 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM1
             size: 256MiB
             width: 32 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: SODIMM DDR 100 MHz (10.0 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM2
             size: 256MiB
             width: 32 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI7420 CardBus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:06:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:06:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
                vendor: Texas Instruments
                physical id: 3.3
                bus info: pci@0000:06:03.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:06:04.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:09:dc:6f
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.255.200.110 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth0
                version: 03
                serial: 00:01:4a:5f:90:18
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: HITACHI_DK23FA-8
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00M3
                serial: A2ND24
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=38fc268d
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 0ab553e5-0775-4aad-8de3-a4dd6293635f
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-03-15 21:08:43 filesystem=ext3 modified=2008-04-22 19:48:51 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-04-22 19:48:51 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1443MiB
                   capacity: 1443MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1443MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: UJ-840D
                vendor: MATSHITA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0


Did you checked the sound with the terminal command:
```
alsamixer
```

yes, everything is at 100%

---

### Post by racgus on 2008-04-22
sorry i kind of got everything jammed into the quote by accident. does that help you to come to any conclusions.

---

### Post by racgus on 2008-04-22
> **LinuxIsInnovation said:**
> At a terminal:
```
sudo apt-get install linux-backports-modules
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules

any thoughts?

---

