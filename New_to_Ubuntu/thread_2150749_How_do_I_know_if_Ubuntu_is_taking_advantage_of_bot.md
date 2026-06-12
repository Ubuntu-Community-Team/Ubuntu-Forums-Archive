---
title: "How do I know if Ubuntu is taking advantage of both video cards in my computer?"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by TaiwanTom on 2013-06-02
I have 2 Nvidia graphics cards in my machine and 2 monitors.  Each card has 2 DVI ports.  Before I installed Ubuntu I was running Windows.  With Windows I had the monitors connected to 2 DVI ports on different cards, not on the same card.  

When I installed Ubuntu it wouldnt recognize my second monitor until I plugged it into the other DVI port on the first video card that my primary monitor is connected to. 

This probably shouldnt matter as long as the computer is distributing the video rendering across both of them. But I'm not sure it's doing that.  Any ideas how to know for sure, and if not how to get both of them in action?

---

### Post by TaiwanTom on 2013-06-02
```
description: Desktop Computer
    product: System Product Name ()
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=46D1881E-126F-B6BE-4A0F-2A5548A3DEF1
  *-core
       description: Motherboard
       product: StrikerExtreme
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS StrikerExtreme ACPI BIOS Revision 1102
          date: 03/28/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
          slot: Socket 775
          size: 2665MHz
          capacity: 3800MHz
          width: 64 bits                                                                                            
          clock: 266MHz                                                                                             
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow                         
        *-cache:0                                                                                                   
             description: L1 cache                                                                                  
             physical id: b                                                                                         
             slot: L1 Cache                                                                                         
             size: 32KiB                                                                                            
             capacity: 32KiB                                                                                        
             capabilities: synchronous internal write-back data                                                     
        *-cache:1                                                                                                   
             description: L2 cache                                                                                  
             physical id: c                                                                                         
             slot: L2 Cache                                                                                         
             size: 4MiB                                                                                             
             capacity: 4MiB                                                                                         
             capabilities: synchronous internal write-back unified                                                  
     *-memory                                                                                                       
          description: System Memory                                                                                
          physical id: 41
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: DIMM_A1
             size: 1GiB
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM_A2
             size: 1GiB
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: DIMM_B1
             size: 1GiB
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: DIMM_B2
             size: 1GiB
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: C55 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.6
             bus info: pci@0000:00:00.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.7
             bus info: pci@0000:00:00.7
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:11 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:12 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:13 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:14 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:15 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:16 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: C55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:ea000000-edffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G80 [GeForce 8800 Ultra]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:ec000000-ecffffff memory:d0000000-dfffffff memory:ea000000-ebffffff ioport:df00(size=128) memory:edfe0000-edffffff
        *-pci:1
             description: PCI bridge
             product: C55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:b000(size=4096) memory:efc00000-efcfffff ioport:ef900000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: C55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:a000(size=4096) memory:efe00000-efefffff ioport:efd00000(size=1048576)
        *-memory:17 UNCLAIMED
             description: RAM memory
             product: MCP55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: ht bus_master cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP55 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP55 SMBus
             vendor: NVIDIA Corporation
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:11 ioport:ff00(size=64) ioport:1c00(size=64) ioport:1c80(size=64)
        *-memory:18 UNCLAIMED
             description: RAM memory
             product: MCP55 Memory Controller
             vendor: NVIDIA Corporation
             physical id: a.2
             bus info: pci@0000:00:0a.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB controller
             product: MCP55 USB Controller
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:effff000-efffffff
        *-usb:1
             description: USB controller
             product: MCP55 USB Controller
             vendor: NVIDIA Corporation
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:efffe000-efffe0ff
        *-ide:0
             description: IDE interface
             product: MCP55 IDE
             vendor: NVIDIA Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-ide:1
             description: IDE interface
             product: MCP55 SATA Controller
             vendor: NVIDIA Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: scsi0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi ht bus_master cap_list emulated
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f700(size=16) memory:efffd000-efffdfff
           *-cdrom
                description: DVD-RAM writer
                product: iHAS324   B
                vendor: ATAPI
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: AL14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:2
             description: IDE interface
             product: MCP55 SATA Controller
             vendor: NVIDIA Corporation
             physical id: e.1
             bus info: pci@0000:00:0e.1
             logical name: scsi2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi ht bus_master cap_list emulated
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:f200(size=16) memory:efffc000-efffcfff
           *-disk
                description: ATA Disk
                product: WDC WD10EZEX-00R
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 80.0
                serial: WD-WCC1S0126987
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3095c1a0
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: f40f4e61-1b91-b94e-a8a1-14ad27d52e84
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-12-15 20:49:00 filesystem=ntfs label=Windows modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 1906c9d3-d4f1-4ba7-a353-697c31aa43f4
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2012-12-16 12:58:45 filesystem=ext3 modified=2012-12-16 13:10:49 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered mounted=2013-06-02 15:58:38 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 7629MiB
                   capacity: 7629MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 7629MiB
                      capabilities: nofs
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /media/FilesPrime
                   version: 3.1
                   serial: ec428ec5-ab91-a04e-adbf-f4110fd72f67
                   size: 728GiB
                   capacity: 729GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-12-17 05:46:11 filesystem=ntfs label=Files Prime mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-ide:3
             description: IDE interface
             product: MCP55 SATA Controller
             vendor: NVIDIA Corporation
             physical id: e.2
             bus info: pci@0000:00:0e.2
             logical name: scsi4
             logical name: scsi5
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi ht bus_master cap_list emulated
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:23 ioport:f100(size=8) ioport:f000(size=4) ioport:ef00(size=8) ioport:ee00(size=4) ioport:ed00(size=16) memory:efffb000-efffbfff
           *-cdrom
                description: DVD-RAM writer
                product: iHAS324   B
                vendor: ATAPI
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr1
                version: AL14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST3500320AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/sdc
                version: SD15
                serial: 9QM9JN0A
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eb1b52ee
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdc1
                   logical name: /media/sdc1
                   version: 3.1
                   serial: 2ee92b57-3b4d-3045-9189-4b3132ce5bb1
                   size: 292GiB
                   capacity: 292GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-12-17 10:22:18 filesystem=ntfs label=Movies mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sdc2
                   logical name: /media/Linux
                   version: 3.1
                   serial: dca0376e-634b-bf48-bff3-803be3336f3f
                   size: 172GiB
                   capacity: 172GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-12-17 15:22:28 filesystem=ntfs label=Backup mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-pci:3
             description: PCI bridge
             product: MCP55 PCI bridge
             vendor: NVIDIA Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:efb00000-efbfffff memory:efa00000-efafffff
           *-network
                description: Ethernet interface
                product: VT6105/VT6106S [Rhine-III]
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:04:06.0
                logical name: eth0
                version: 86
                serial: ac:f1:df:3f:01:99
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.123 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
                resources: irq:16 ioport:cc00(size=256) memory:efbff000-efbff0ff memory:efbe0000-efbeffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@0000:04:0b.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:19 memory:efbfe000-efbfe7ff ioport:cf00(size=128)
        *-multimedia
             description: Audio device
             product: MCP55 High Definition Audio
             vendor: NVIDIA Corporation
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ht bus_master cap_list
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:20 memory:efff0000-efff3fff
        *-bridge:0
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: NVIDIA Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: eth1
             version: a2
             serial: 00:1a:92:54:f3:ac
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:49 memory:efffa000-efffafff ioport:ec00(size=8) memory:efff9000-efff90ff memory:efff8000-efff800f
        *-bridge:1
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: NVIDIA Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth2
             version: a2
             serial: 00:1a:92:54:f9:85
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:50 memory:efff7000-efff7fff ioport:eb00(size=8) memory:efff6000-efff60ff memory:efff5000-efff500f
        *-pci:4
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:9000(size=4096) memory:ef800000-ef8fffff ioport:ef700000(size=1048576)
        *-pci:5
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:8000(size=4096) memory:ef600000-ef6fffff ioport:ef500000(size=1048576)
        *-pci:6
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:7000(size=4096) memory:ef400000-ef4fffff ioport:ef300000(size=1048576)
        *-pci:7
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:6000(size=4096) memory:ef200000-ef2fffff ioport:ef100000(size=1048576)
           *-storage
                description: Mass storage controller
                product: SiI 3132 Serial ATA Raid II Controller
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list rom
                configuration: driver=sata_sil24 latency=0
                resources: irq:16 memory:ef2ff000-ef2ff07f memory:ef2f8000-ef2fbfff ioport:6f00(size=128) memory:ef200000-ef27ffff
        *-pci:8
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:5000(size=4096) memory:ef000000-ef0fffff ioport:eef00000(size=1048576)
        *-pci:9
             description: PCI bridge
             product: MCP55 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:48 ioport:4000(size=4096) memory:e6000000-e9ffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G80 [GeForce 8800 Ultra]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:e8000000-e8ffffff memory:c0000000-cfffffff memory:e6000000-e7ffffff ioport:4f00(size=128) memory:e9000000-e901ffff
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdb
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=4e0d56c5
           *-volume:0 UNCLAIMED
                description: EFI GPT partition
                physical id: 1
                bus info: scsi@10:0.0.0,1
                capacity: 200MiB
                capabilities: primary nofs
           *-volume:1
                description: HPFS/NTFS partition
                physical id: 2
                bus info: scsi@10:0.0.0,2
                logical name: /dev/sdb2
                capacity: 297GiB
                capabilities: primary
```

---

### Post by 3rdalbum on 2013-06-02
You might need some advice from somebody who has actually used SLI, but my understanding is that if you've installed the Nvidia driver (from Software Sources program) you will be using both cards.

---

### Post by Mark Phelps on 2013-06-02
My guess would be, since (1) it didn't see the monitor using the 2nd card, and (2) you now have both monitors connected to the same card -- that the second card is not being used.  I believe you have to be running special drivers to utilize SLI. But, I don't run SLI, so I could be wrong.

---

### Post by TaiwanTom on 2013-06-03
Thanks a lot for your help, how would I go about running SLI?  And if my drivers are not the correct ones, where would I find and how would I change them?

---

### Post by Mark Phelps on 2013-06-03
Sorry, don't personally use SLI or Nvidia cards.  You will need to read through the details in the link about enabling SLI -- doesn't look like a simple process:  [https://wiki.archlinux.org/index.php/NVIDIA#Enabling_SLI]("https://wiki.archlinux.org/index.php/NVIDIA#Enabling_SLI")

---

### Post by TaiwanTom on 2013-06-04
Thanks i'll try to tackle this today.

---

