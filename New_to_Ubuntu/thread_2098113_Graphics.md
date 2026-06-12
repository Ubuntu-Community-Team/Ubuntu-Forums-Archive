---
title: "Graphics?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-25
My new Ubuntu install doesn't show Intel 945GM Grahics driver in settings, any suggestions?

Thanks.

---

### Post by Pjotr123 on 2012-12-25
Nothing wrong, probably. Create a comprehensive hardware list like this:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

In that document you can also check the video driver.

---

### Post by Yezinki on 2012-12-25
```
vaio@VGC-LS1:~$ sudo lshw
[sudo] password for vaio: 
Sorry, try again.
[sudo] password for vaio: 
vgc-ls1                   
    description: Notebook
    product: VGC-LS1 (N/A)
    vendor: Sony Corporation
    version: C3LMKZHR
    serial: 28243230-3001856
    width: 32 bits
    capabilities: smbios-2.40 dmi-2.40 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 family=N/A sku=N/A uuid=C97E3540-29C3-11DB-8104-0013A94B18F6
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: Bank 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0062W2
          date: 09/13/2006
          size: 101KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: N/A
          size: 1833MHz
          capacity: 1833MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: SODIMM1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous
             physical id: 1
             slot: SODIMM2
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
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
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dc300000-dc37ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:dc380000-dc3bffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:dc3c0000-dc3c3fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:d8000000-d9ffffff ioport:d2000000(size=33554432)
           *-network
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:13:a9:4b:18:f6
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:43 memory:d8000000-d8003fff ioport:2000(size=256)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:d6000000-d7ffffff ioport:d0000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:da000000-dbffffff ioport:d4000000(size=33554432)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:18 memory:da000000-da003fff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:dc5c4000-dc5c43ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:dc000000-dc2fffff ioport:80000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:08:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:84000000-84000fff ioport:5800(size=256) ioport:5400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@0000:08:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=3
                resources: irq:16 memory:dc215000-dc2157ff memory:dc210000-dc213fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:08:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:18 memory:dc214000-dc214fff
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: Fujitsu Limited.
                vendor: Fujitsu Limited.
                physical id: 5
                bus info: pci@0000:08:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64 maxlatency=64 mingnt=16
                resources: ioport:5000(size=256) memory:dc000000-dc1fffff memory:dc200000-dc20ffff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GMA-4080N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 0H37
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:18d0(size=8) ioport:18c4(size=4) ioport:18c8(size=8) ioport:18c0(size=4) ioport:18b0(size=16) memory:dc5c4400-dc5c47ff
           *-disk
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAV2K841553
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=34734b0d
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 86c10b8f-4159-49ad-886f-74160059f2e2
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-12-25 13:23:36 filesystem=ext4 lastmountpoint=/ modified=2012-12-25 13:38:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-12-26 00:11:46 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 811ef2a4-f668-4b93-89ef-c3fb7b99d069
                   size: 263GiB
                   capacity: 263GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-12-25 13:23:38 filesystem=ext4 lastmountpoint=/home modified=2012-12-26 00:11:47 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-12-26 00:11:47 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 360b6903-2b2a-4139-9c94-2c09c59393fc
                   size: 5212MiB
                   capacity: 5212MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:12:c4:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-35-generic-pae firmware=508.1084 ip=192.168.1.3 link=yes multicast=yes wireless=IEEE 802.11bg
vaio@VGC-LS1:~$ 

```

---

### Post by Pjotr123 on 2012-12-25
Runs on the i915, like it should. All is well.

**configuration: driver=i915** latency=0

```
 *-display
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dc300000-dc37ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:dc380000-dc3bffff
```

---

### Post by Yezinki on 2012-12-25
Thanks Pjotr123 but while running Zorin it displays Intel 945GM x86/MMX/SSE2 in Details > Graphics?

---

### Post by Pjotr123 on 2012-12-25
> **Yezinki said:**
> Thanks Pjotr123 but while running Zorin it displays Intel 945GM x86/MMX/SSE2 in Details > Graphics?

Nice for Zorin, but does it really matter?  :biggrin:

---

### Post by Yezinki on 2012-12-25
Thanks again Pjotr123 for your expert advice. :D

---

### Post by Cheesemill on 2012-12-25
This is a known bug in the System settings application. Some users have found that installing the mesa-utils package causes the information to be shown correctly (Zorin probably has this package installed by default)..
```
sudo apt-get install mesa-utils
```

---

### Post by Yezinki on 2012-12-25
Should I try installing this Cheesemill?

Thanks.

---

### Post by Cheesemill on 2012-12-25
It can't hurt and it may well fix the issue with System Settings quoting the graphics as 'Unknown' so yes, go for it.

---

### Post by Yezinki on 2012-12-25
Thanks Cheesemill it works.......

---

