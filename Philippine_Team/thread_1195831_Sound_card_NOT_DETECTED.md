---
title: "Sound card NOT DETECTED"
date: 2009-06-24
forum: Philippine Team
---

### Post by guitar_man on 2009-06-24
Mga sir pag luma ba yung sound card mo pisble bang hindi madetect ng Ubuntu..
Naginstall kasi ako ng Jaunty sa isang lumang kompyuter...MAy sound card naman sya kaya lang yung sound card Jurasic Era...Its NOT a PCI card..

---

### Post by dodimar on 2009-06-24
:)

results ng lspci...

---

### Post by Nhatz on 2009-06-24
> **guitar_man said:**
> Mga sir pag luma ba yung sound card mo pisble bang hindi madetect ng Ubuntu..
Naginstall kasi ako ng Jaunty sa isang lumang kompyuter...MAy sound card naman sya kaya lang yung sound card Jurasic Era...Its NOT a PCI card..

Tingnan mo result ng lshw mo kung nadetect nya.. built in ba sa mobo?

ASTIG!!! :guitar:

---

### Post by guitar_man on 2009-06-24
> WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 256MiB
     *-cpu:0
          product: Pentium II (Klamath)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.3.3
          size: 300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov mmx
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:1
          product: Pentium II (Klamath)
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 6.3.3
          size: 300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov mmx
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 440LX/EX - 82443LX/EX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=32 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440LX/EX - 82443LX/EX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 5c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=66 mingnt=8
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM CDU571-Q
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.1a
                serial: [SONY    CD-ROM CDU571-Q 1.1a
                capabilities: removable audio
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-scsi:0
             description: SCSI storage controller
             product: AHA-2940U/UW / AHA-39xx / AIC-7895
             vendor: Adaptec
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: scsi bus_master scsi-host
             configuration: driver=aic7xxx latency=64 maxlatency=8 mingnt=8 module=aic7xxx
        *-scsi:1
             description: SCSI storage controller
             product: AHA-2940U/UW / AHA-39xx / AIC-7895
             vendor: Adaptec
             physical id: 9.1
             bus info: pci@0000:00:09.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: scsi bus_master scsi-host
             configuration: driver=aic7xxx latency=64 maxlatency=8 mingnt=8 module=aic7xxx
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 10
             serial: 00:0e:2e:8b:c5:06
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.247.238 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:d2:8c:97:75:7b
       capabilities: ethernet physical




eto yung lshw




> 


00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:09.0 SCSI storage controller: Adaptec AHA-2940U/UW / AHA-39xx / AIC-7895 (rev 03)
00:09.1 SCSI storage controller: Adaptec AHA-2940U/UW / AHA-39xx / AIC-7895 (rev 03)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X (rev 5c)




eto lspci

---

