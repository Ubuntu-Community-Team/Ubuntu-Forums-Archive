---
title: "Trouble installing Ub-Studio (any version)"
date: 2019-11-19
forum: New to Ubuntu
---

### Post by Durandall on 2019-11-19
Don't want to make myself into a storyteller here, but I'll start off by saying I've "dabbled" in Linux, almost specifically Ubuntu for years now.  I'm 99% sure my first version was Hardy Heron.  So, all I'm saying here is, I've been able to successfully install quite a few distro's with no issues.  Recently I was using Manjaro because I'd had better luck setting up plex with it, and steam seamed to work right out of the box.  But my focus has changed.  Ultimately I'd like to ditch windows all together - for now though, this is what I'm trying to make happen.

Dual boot, Win 10 and Ub-Studio.  Windows for plex and gaming, and Ub-Studio for a/v mixing and just generally furthering my linux experience.

Hardware:
AMD FX-8370
Asus 970 Aura MB
Corsair Vengeance 16gb 
Asus RX480 Strix
2 separate 250GB SSD's (Not in RAID) - purchased with intent of dual-booting
Storage HDD
BD-Rom Drive

I've had Ub-Studio, Pop_OS!, Manjaro, and elementary installed at one time or the other on this exact hardware, along with Win 10.  Lately I've been getting the "black screen" issue.  Happened to me with Manjaro AND Ubuntu.  I burn an ISO, and after I make my choice to Try, or Install - no matter which selection I choose it goes black.

From here on I'll only mention my Ubuntu problems and things I've tried.

I do the nomodeset "fix" at the selection screen, F6 - and I can install Ubuntu, thing is it seems like my gpu isn't set up as it should be.  No audio, HDMI isn't even a choice in the audio mixer.  No proprietary drivers are found.  This is all when I try 18.04 and newer.  Here's something fun.  I found an ISO of 17.04, and it installed like a charm.  I mean perfectly.  I tried to just update to current from that installation and I can't, as it's EOL and the Ubuntu Servers weren't happy about it.  I've formatted my Linux drive and I'm going to do another fresh install of 19.10 - hopefully you guys can get me set up.

OH! - if I try installing from a DVD, it crashes at the end.  Fails to write grub to sda.  I mean, no big deal I guess... but that doesn't happen if I make a USB with Rufus, just thought I'd mention it.

My PC's BIOS has secure boot set to "Other OS" - I created my USB Boot stick following Ubuntu's guide.

I'll update once I have the installation complete.  Thanks for reading/helping.  Any links to posts that have may help are also appreciated.

I am curious what's changed, though.  Why is every Linux distro I try "black screening" on me?  Seemingly out of nowhere.

---

### Post by mörgæs on 2019-11-21
> **Durandall said:**
> 
I'll update once I have the installation complete. 

Thanks. Though you have already posted some hardware information please also run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Durandall on 2019-11-22
computer
  ```
  description: Desktop Computer
    product: To be filled by O.E.M. (SKU)
    vendor: To be filled by O.E.M.
    version: To be filled by O.E.M.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 970 PRO GAMING/AURA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1001
          date: 06/07/2017
          size: 64KiB
          capacity: 8MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD FX-8370 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX-8370 Eight-Core Processor
          serial: [REMOVED]
          slot: Socket 942
          size: 1618MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate ssbd ibpb vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold lwp cpufreq
          configuration: cores=8 enabledcores=8 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous Unbuffered (Unregistered) 1333 MHz (0.8 ns)
             product: CMY16GX3M2B2133C11
             vendor: Corsair
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
        *-bank:3
             description: DIMM DDR3 Synchronous Unbuffered (Unregistered) 1333 MHz (0.8 ns)
             product: CMY16GX3M2B2133C11
             vendor: Corsair
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RD9x0/RX980 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:fea00000-feafffff ioport:c0000000(size=270532608)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: c7
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:fea00000-fea3ffff memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:55 memory:fea60000-fea63fff
        *-pci:1
             description: PCI bridge
             product: RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:fe900000-fe9fffff
           *-usb
                description: USB controller
                product: ASM1143 USB 3.1 Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:30 memory:fe900000-fe907fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-23-lowlatency xhci-hcd
                   physical id: 0
                   bus info: usb@8
                   logical name: usb8
                   version: 5.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-23-lowlatency xhci-hcd
                   physical id: 1
                   bus info: usb@9
                   logical name: usb9
                   version: 5.03
                   capabilities: usb-3.10
                   configuration: driver=hub slots=2 speed=10000Mbit/s
        *-pci:2
             description: PCI bridge
             product: RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 memory:fe800000-fe8fffff
           *-usb
                description: USB controller
                product: ASM1042A USB 3.0 Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:39 memory:fe800000-fe807fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-23-lowlatency xhci-hcd
                   physical id: 0
                   bus info: usb@10
                   logical name: usb10
                   version: 5.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: Logitech G710 Keyboard
                      vendor: Logitech
                      physical id: 1
                      bus info: usb@10:1
                      version: 80.01
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=400mA speed=12Mbit/s
                 *-usb:1
                      description: Mouse
                      product: CORSAIR M65 RGB ELITE Gaming Mouse
                      vendor: Corsair
                      physical id: 2
                      bus info: usb@10:2
                      version: 3.24
                      serial: [REMOVED]
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-23-lowlatency xhci-hcd
                   physical id: 1
                   bus info: usb@11
                   logical name: usb11
                   version: 5.03
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:3
             description: PCI bridge
             product: RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:d000(size=4096) memory:fe700000-fe7fffff
           *-network
                description: Ethernet interface
                product: I211 Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 03
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.6.0-k duplex=full firmware=0. 6-1 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:48 memory:fe700000-fe71ffff ioport:d000(size=32) memory:fe720000-fe723fff
        *-sata
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi5
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: sata ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f040(size=8) ioport:f030(size=4) ioport:f020(size=8) ioport:f010(size=4) ioport:f000(size=16) memory:feb0b000-feb0b3ff
           *-disk:0
                description: ATA Disk
                product: SPCC Solid State
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: V2.8
                serial: [REMOVED]
                size: 223GiB (240GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=4f3e8f43-c910-4196-b127-726682f97c0c logicalsectorsize=512 sectorsize=512
              *-volume:0
                   description: Windows NTFS volume
                   vendor: Windows
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: [REMOVED]
                   size: 448MiB
                   capacity: 449MiB
                   capabilities: boot precious nomount ntfs initialized
                   configuration: clustersize=4096 created=2019-08-17 22:55:44 filesystem=ntfs label=Recovery name=Basic data partition state=clean
              *-volume:1
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /boot/efi
                   version: FAT32
                   serial: [REMOVED]
                   size: 93MiB
                   capacity: 99MiB
                   capabilities: boot nomount fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
              *-volume:2
                   description: reserved partition
                   vendor: Windows
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   serial: [REMOVED]
                   capacity: 15MiB
                   capabilities: nofs nomount
                   configuration: name=Microsoft reserved partition
              *-volume:3
                   description: Windows NTFS volume
                   vendor: Windows
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: [REMOVED]
                   size: 222GiB
                   capacity: 222GiB
                   capabilities: ntfs initialized
                   configuration: clustersize=4096 created=2019-08-17 22:55:52 filesystem=ntfs name=Basic data partition state=clean
              *-volume:4
                   description: Windows NTFS volume
                   vendor: Windows
                   physical id: 5
                   bus info: scsi@0:0.0.0,5
                   logical name: /dev/sda5
                   version: 3.1
                   serial: [REMOVED]
                   size: 512MiB
                   capacity: 515MiB
                   capabilities: boot precious nomount ntfs initialized
                   configuration: clustersize=4096 created=2019-08-17 17:59:11 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
                product: BC-12B1ST   b
                vendor: ASUS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 3.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: Samsung SSD 850
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 2B6Q
                serial: [REMOVED]
                size: 232GiB (250GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=5ad94e73-f9e0-47ab-8249-568386c36b75 logicalsectorsize=512 sectorsize=512
              *-volume:0
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   version: FAT32
                   serial: [REMOVED]
                   size: 510MiB
                   capacity: 511MiB
                   capabilities: boot fat initialized
                   configuration: FATs=2 filesystem=fat name=EFI System Partition
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 232GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2019-11-19 22:21:54 filesystem=ext4 lastmountpoint=/ modified=2019-11-22 14:13:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-11-22 14:13:34 state=mounted
           *-disk:2
                description: ATA Disk
                product: Hitachi HUA72303
                vendor: Hitachi
                physical id: 3
                bus info: scsi@5:0.0.0
                logical name: /dev/sdc
                version: AA10
                serial: [REMOVED]
                size: 2794GiB (3TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=3f5e5725-d4bb-42d3-85da-1f676a36cee9 logicalsectorsize=512 sectorsize=512
              *-volume
                   description: Windows NTFS volume
                   vendor: Windows
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: [REMOVED]
                   size: 746GiB
                   capacity: 2794GiB
                   capabilities: ntfs initialized
                   configuration: clustersize=4096 created=2019-07-08 16:26:08 filesystem=ntfs name=Storage state=clean
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb0a000-feb0afff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.3.0-23-lowlatency ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.03
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb09000-feb090ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.3.0-23-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:20 memory:feb08000-feb08fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.3.0-23-lowlatency ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 5.03
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@5:3
                   version: 12.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:feb07000-feb070ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.3.0-23-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
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
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb06000-feb06fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.3.0-23-lowlatency ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 5.03
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:22 memory:feb05000-feb05fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.3.0-23-lowlatency ohci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 5.03
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:23 memory:feb04000-feb040ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.3.0-23-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0b00
          physical id: 5
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0501
          physical id: 8
          capabilities: pnp
          configuration: driver=serial
     *-pnp00:07
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: a
          capabilities: pnp
          configuration: driver=system
```

---

### Post by wildmanne39 on 2019-11-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mörgæs on 2019-11-23
The hardware looks fine. 

Ubuntu Studio is built upon the low-latency kernel. Do you see any difference when comparing a Studio install to installing one of the other Buntus?

---

### Post by Durandall on 2019-11-23
I apologize for not using code tags.  I don't really post to forums often and didn't know how.  Thank you for the instructions.

---

### Post by Durandall on 2019-11-23
I've only ever tried Studio, and vanilla Ubuntu - as far as downloading and installing is concerned.  Usually, and now, actually - I have Studio installed and I'm kind of going between xfce, budgie, and gnome to see which environment I favor the most.  I've tried derivatives such as Pop_os! and elementary - outside of Ubuntu flavors, I've tried manjaro.

My guess, for what it's worth - is the kernel.  Since my fresh install I updated the kernel and now have the most recent stable (non-LL) kernel following this guide ->[https://www.linuxuprising.com/2018/10/2-utilities-to-install-latest-kernel-in.html]("https://www.linuxuprising.com/2018/10/2-utilities-to-install-latest-kernel-in.html")

Same issue continues, black screen after grub selection.

If I do a fresh install of older linux OS's, including studio and vanilla - everything is working fine.  I can't update to current.  So, I guess tonight I'm going to try and install an older kernel on my installed version and see if that works.

---

### Post by Durandall on 2019-11-23
I've just tried 4.20.17, 4.18 - both in generic and low latency.  Same result.  Is it possible 19.10 isn't compatible with older kernels?  I'll install 18.04 LTS and troubleshoot from there.

---

