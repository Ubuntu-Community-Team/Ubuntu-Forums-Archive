---
title: "nForce2 Ultra 400: do I need a network driver ?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by MarcioAB on 2008-10-02
Hello, I'm trying to move from Windows to Ubuntu and I just installed Ubuntu 8.04 in a systems with an Asus A7N8X-E Deluxe (nForce2 Ultra 400), but network is not working and it seems the reason is no driver.

On nVidia page for Linux nForce drivers
( [http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html) )
I can download a pack that I suppose contain drivers in directories for several Linux distributions (Fedora5, RedHat3U6, 3U7 ... 4U4, SLES9_SP2, SP3, SLES10 and SuSE10) but no Ubuntu.

The page says: NVIDIA also provides pre-compiled storage (sata_nv) and Ethernet (forcedeth) driver disc images, bla, bla.
I'm not familiar with this terminology.

How to make the network to work ? or what/how should be my next step from here ?

Thank you
Marcio

---

### Post by cariboo on 2008-10-03
Could you please post the output of:

```
sudo lshw
```

You will have to do this in a Applications-->Accessories-->Terminal, and post the output in your next post. This will show use the details of the nic and we should be able to tell what driver it needs

---

### Post by MarcioAB on 2008-10-03
Thank you, ( and btw, very nice command ! )

As a curious, in the network description I see "driver=forcedeth driverversion=0.61". I suppose it means this driver is already installed, but "it seems the network does not exist". 


debora
    description: Desktop Computer
    product: A7N8X-E
    vendor: ASUSTeK Computer INC.
    version: REV 2.xx
    serial: xxxxxxxxxxx
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: A7N8X-E
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 2.xx
       serial: xxxxxxxxxxx
       slot: Serial Port 1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A7N8X-E Deluxe ACPI BIOS Rev 1013 (11/12/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2083MHz
          capacity: 3GHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous external write-back data
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 1GiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: DDR1
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DDR2
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DDR3
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:0e:a6:3d:a0:f6
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0 maxlatency=12 mingnt=1
        *-multimedia:1
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-storage
                description: RAID bus controller
                product: SiI 3112 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: b
                bus info: pci@0000:01:0b.0
                logical name: scsi0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list emulated
                configuration: driver=sata_sil latency=32 module=sata_sil
              *-disk
                   description: ATA Disk
                   product: ST3160023AS
                   vendor: Seagate
                   physical id: 0.0.0
                   bus info: scsi@0:0.0.0
                   logical name: /dev/sda
                   version: 3.18
                   serial: 3JS0FEQF
                   size: 149GiB (160GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=330a7e97
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@0:0.0.0,1
                      logical name: /dev/sda1
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0
                      serial: ed7be9e4-4c86-412a-bc93-1a73f80074a7
                      size: 146GiB
                      capacity: 146GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-10-02 18:38:40 filesystem=ext3 modified=2008-10-02 18:54:49 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-10-02 18:51:26 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: scsi@0:0.0.0,2
                      logical name: /dev/sda2
                      size: 2957MiB
                      capacity: 2957MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sda5
                         capacity: 2957MiB
                         capabilities: nofs
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-M1212
                vendor: TOSHIBA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1R08
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV28 [GeForce4 Ti 4200 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
     *-scsi
          physical id: 1
          bus info: usb@3:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: DataTraveler 2.0
             vendor: Kingston
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: PMAP
             size: 984MiB (1031MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 984MiB (1031MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   vendor: *5>+kIHC
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/KINGSTON
                   version: FAT16
                   serial: 648d-4b9f
                   size: 983MiB
                   capacity: 983MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=KINGSTON mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted

---

