---
title: "youtube videos lagging"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by seal308 on 2012-04-01
Hello.
I'm using a wired connection with my ubuntu desktop.
I also have a mac book pro in the same room using wireless.

I noticed that the ubuntu machine is lagging when streaming videos while the laptop is not lagging. 
When i say lag i mean the video is jittery and the audio is faster than the video.

Any ideas as to why this would occur? 
How can this be fixed.
Thanks

---

### Post by seal308 on 2012-04-01
these are my specs i think

```
id:glenn-eb1006
       description: Desktop Computer     version: System Version     width: 32 bits     capabilities: smbios-2.5 dmi-2.5      configuration: boot=normal chassis=desktop family=Eee Family sku=To Be Filled By O.E.M. uuid=606A40CC-8EFE-D511-8BB2-002618CCF599                   id:core
          description: Motherboard        product: P5G-EB1006-DHS        vendor: ASUSTeK Computer INC.        physical id: 0
        version: Rev 1.xx        serial: MF7098G01600425        slot: To Be Filled By O.E.M.      
                          id:firmware
             description: BIOS           vendor: American Megatrends Inc.           physical id: 0
           version: 0501           date: 07/31/2009           size: 64KiB           capacity: 960KiB           capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification          
        
                          id:cpu
             description: CPU           product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz           vendor: Intel Corp.           physical id: 4
           bus info: cpu@0
           version: 6.12.2           serial: 0001-06C2-0000-0000-0000-0000           slot: CPU 1           size: 1600MHz           capacity: 3800MHz           width: 32 bits           clock: 133MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq            configuration: cores=1 enabledcores=1 id=1 threads=2         
                                   id:cache:0
                description: L1 cache              physical id: 5
              slot: L1-Cache              size: 24KiB              capacity: 24KiB              capabilities: internal write-back data             
           
                                   id:cache:1
                description: L2 cache              physical id: 6
              slot: L2-Cache              size: 512KiB              capacity: 512KiB              capabilities: internal write-back unified             
           
                                   id:logicalcpu:0
                description: Logical CPU              physical id: 1.1
              width: 32 bits              capabilities: logical             
           
                                   id:logicalcpu:1
                description: Logical CPU              physical id: 1.2
              width: 32 bits              capabilities: logical             
           
        
                          id:memory
             description: System Memory           physical id: e
           slot: System board or motherboard           size: 1GiB         
                                   id:bank:0
                description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)              product: PartNum0              vendor: Manufacturer0              physical id: 0
              serial: SerNum0              slot: DIMM0              size: 1GiB              width: 64 bits              clock: 533MHz (1.9ns)            
           
                                   id:bank:1
                description: DIMM [empty]              product: PartNum1              vendor: Manufacturer1              physical id: 1
              serial: SerNum1              slot: DIMM1            
           
        
                          idci
             description: Host bridge           product: Mobile 945GME Express Memory Controller Hub           vendor: Intel Corporation           physical id: 100
           bus info: pci@0000:00:00.0
           version: 03           width: 32 bits           clock: 33MHz         
                                   id:multimedia
                description: Audio device              product: N10/ICH 7 Family High Definition Audio Controller              vendor: Intel Corporation              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 02              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list               configuration: driver=HDA Intel latency=0              resources: irq:45 memory:fe83c000-fe83ffff            
           
                                   idci:0
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 1              vendor: Intel Corporation              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:40 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:cff00000(size=1048576)            
                                            id:network
                   description: Ethernet interface                 product: RTL8111/8168B PCI Express Gigabit Ethernet controller                 vendor: Realtek Semiconductor Co., Ltd.                 physical id: 0
                 bus info: pci@0000:01:00.0
                 logical name: eth0
                 version: 02                 serial: 00:26:18:cc:f5:99                 size: 1Gbit/s                 capacity: 1Gbit/s                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                  configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.192 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s                 resources: irq:44 ioport:dc00(size=256) memory:fe9ff000-fe9fffff memory:cfff0000-cfffffff memory:fe9c0000-fe9dffff               
              
           
                                   idci:1
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 2              vendor: Intel Corporation              physical id: 1c.1
              bus info: pci@0000:00:1c.1
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:41 ioport:2000(size=4096) memory:fea00000-feafffff ioport:40400000(size=2097152)            
                                            id:network
                   description: Wireless interface                 product: AR9285 Wireless Network Adapter (PCI-Express)                 vendor: Atheros Communications Inc.                 physical id: 0
                 bus info: pci@0000:02:00.0
                 logical name: wlan0
                 version: 01                 serial: 00:25:d3:66:e4:12                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                  configuration: broadcast=yes driver=ath9k driverversion=3.0.0-17-generic firmware=N/A ip=192.168.0.193 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn                 resources: irq:17 memory:feaf0000-feafffff               
              
           
                                   idci:2
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 3              vendor: Intel Corporation              physical id: 1c.2
              bus info: pci@0000:00:1c.2
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:d0000000(size=268435456)            
                                            id:display
                   description: VGA compatible controller                 product: M92 [Mobility Radeon HD 4500/5100 Series]                 vendor: ATI Technologies Inc                 physical id: 0
                 bus info: pci@0000:03:00.0
                 version: 00                 width: 64 bits                 clock: 33MHz                 capabilities: pm pciexpress msi vga_controller bus_master cap_list rom                  configuration: driver=radeon latency=0                 resources: irq:47 memory:d0000000-dfffffff memory:febf0000-febfffff ioport:e800(size=256) memory:febc0000-febdffff               
              
                                            id:multimedia
                   description: Audio device                 product: RV710/730                 vendor: ATI Technologies Inc                 physical id: 0.1
                 bus info: pci@0000:03:00.1
                 version: 00                 width: 64 bits                 clock: 33MHz                 capabilities: pm pciexpress msi bus_master cap_list                  configuration: driver=HDA Intel latency=0                 resources: irq:46 memory:febec000-febeffff               
              
           
                                   id:pci:3
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 4              vendor: Intel Corporation              physical id: 1c.3
              bus info: pci@0000:00:1c.3
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:43 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)            
           
                                   id:usb:0
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #1              vendor: Intel Corporation              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:23 ioport:cc00(size=32)            
           
                                   id:usb:1
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #2              vendor: Intel Corporation              physical id: 1d.1
              bus info: pci@0000:00:1d.1
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:19 ioport:c880(size=32)            
           
                                   id:usb:2
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #3              vendor: Intel Corporation              physical id: 1d.2
              bus info: pci@0000:00:1d.2
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:18 ioport:c800(size=32)            
           
                                   id:usb:3
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #4              vendor: Intel Corporation              physical id: 1d.3
              bus info: pci@0000:00:1d.3
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:16 ioport:c480(size=32)            
           
                                   id:usb:4
                description: USB Controller              product: N10/ICH 7 Family USB2 EHCI Controller              vendor: Intel Corporation              physical id: 1d.7
              bus info: pci@0000:00:1d.7
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pm debug ehci bus_master cap_list               configuration: driver=ehci_hcd latency=0              resources: irq:23 memory:fe83bc00-fe83bfff            
           
                                   idci:4
                description: PCI bridge              product: 82801 Mobile PCI Bridgeid:glenn-eb1006
       description: Desktop Computer     version: System Version     width: 32 bits     capabilities: smbios-2.5 dmi-2.5      configuration: boot=normal chassis=desktop family=Eee Family sku=To Be Filled By O.E.M. uuid=606A40CC-8EFE-D511-8BB2-002618CCF599                   id:core
          description: Motherboard        product: P5G-EB1006-DHS        vendor: ASUSTeK Computer INC.        physical id: 0
        version: Rev 1.xx        serial: MF7098G01600425        slot: To Be Filled By O.E.M.      
                          id:firmware
             description: BIOS           vendor: American Megatrends Inc.           physical id: 0
           version: 0501           date: 07/31/2009           size: 64KiB           capacity: 960KiB           capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification          
        
                          id:cpu
             description: CPU           product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz           vendor: Intel Corp.           physical id: 4
           bus info: cpu@0
           version: 6.12.2           serial: 0001-06C2-0000-0000-0000-0000           slot: CPU 1           size: 1600MHz           capacity: 3800MHz           width: 32 bits           clock: 133MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq            configuration: cores=1 enabledcores=1 id=1 threads=2         
                                   id:cache:0
                description: L1 cache              physical id: 5
              slot: L1-Cache              size: 24KiB              capacity: 24KiB              capabilities: internal write-back data             
           
                                   id:cache:1
                description: L2 cache              physical id: 6
              slot: L2-Cache              size: 512KiB              capacity: 512KiB              capabilities: internal write-back unified             
           
                                   id:logicalcpu:0
                description: Logical CPU              physical id: 1.1
              width: 32 bits              capabilities: logical             
           
                                   id:logicalcpu:1
                description: Logical CPU              physical id: 1.2
              width: 32 bits              capabilities: logical             
           
        
                          id:memory
             description: System Memory           physical id: e
           slot: System board or motherboard           size: 1GiB         
                                   id:bank:0
                description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)              product: PartNum0              vendor: Manufacturer0              physical id: 0
              serial: SerNum0              slot: DIMM0              size: 1GiB              width: 64 bits              clock: 533MHz (1.9ns)            
           
                                   id:bank:1
                description: DIMM [empty]              product: PartNum1              vendor: Manufacturer1              physical id: 1
              serial: SerNum1              slot: DIMM1            
           
        
                          idci
             description: Host bridge           product: Mobile 945GME Express Memory Controller Hub           vendor: Intel Corporation           physical id: 100
           bus info: pci@0000:00:00.0
           version: 03           width: 32 bits           clock: 33MHz         
                                   id:multimedia
                description: Audio device              product: N10/ICH 7 Family High Definition Audio Controller              vendor: Intel Corporation              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 02              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list               configuration: driver=HDA Intel latency=0              resources: irq:45 memory:fe83c000-fe83ffff            
           
                                   id:pci:0
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 1              vendor: Intel Corporation              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:40 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:cff00000(size=1048576)            
                                            id:network
                   description: Ethernet interface                 product: RTL8111/8168B PCI Express Gigabit Ethernet controller                 vendor: Realtek Semiconductor Co., Ltd.                 physical id: 0
                 bus info: pci@0000:01:00.0
                 logical name: eth0
                 version: 02                 serial: 00:26:18:cc:f5:99                 size: 1Gbit/s                 capacity: 1Gbit/s                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                  configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.192 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s                 resources: irq:44 ioport:dc00(size=256) memory:fe9ff000-fe9fffff memory:cfff0000-cfffffff memory:fe9c0000-fe9dffff               
              
           
                                   idci:1
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 2              vendor: Intel Corporation              physical id: 1c.1
              bus info: pci@0000:00:1c.1
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:41 ioport:2000(size=4096) memory:fea00000-feafffff ioport:40400000(size=2097152)            
                                            id:network
                   description: Wireless interface                 product: AR9285 Wireless Network Adapter (PCI-Express)                 vendor: Atheros Communications Inc.                 physical id: 0
                 bus info: pci@0000:02:00.0
                 logical name: wlan0
                 version: 01                 serial: 00:25:d3:66:e4:12                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                  configuration: broadcast=yes driver=ath9k driverversion=3.0.0-17-generic firmware=N/A ip=192.168.0.193 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn                 resources: irq:17 memory:feaf0000-feafffff               
              
           
                                   idci:2
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 3              vendor: Intel Corporation              physical id: 1c.2
              bus info: pci@0000:00:1c.2
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:d0000000(size=268435456)            
                                            id:display
                   description: VGA compatible controller                 product: M92 [Mobility Radeon HD 4500/5100 Series]                 vendor: ATI Technologies Inc                 physical id: 0
                 bus info: pci@0000:03:00.0
                 version: 00                 width: 64 bits                 clock: 33MHz                 capabilities: pm pciexpress msi vga_controller bus_master cap_list rom                  configuration: driver=radeon latency=0                 resources: irq:47 memory:d0000000-dfffffff memory:febf0000-febfffff ioport:e800(size=256) memory:febc0000-febdffff               
              
                                            id:multimedia
                   description: Audio device                 product: RV710/730                 vendor: ATI Technologies Inc                 physical id: 0.1
                 bus info: pci@0000:03:00.1
                 version: 00                 width: 64 bits                 clock: 33MHz                 capabilities: pm pciexpress msi bus_master cap_list                  configuration: driver=HDA Intel latency=0                 resources: irq:46 memory:febec000-febeffff               
              
           
                                   id:pci:3
                description: PCI bridge              product: N10/ICH 7 Family PCI Express Port 4              vendor: Intel Corporation              physical id: 1c.3
              bus info: pci@0000:00:1c.3
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list               configuration: driver=pcieport              resources: irq:43 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)            
           
                                   id:usb:0
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #1              vendor: Intel Corporation              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:23 ioport:cc00(size=32)            
           
                                   id:usb:1
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #2              vendor: Intel Corporation              physical id: 1d.1
              bus info: pci@0000:00:1d.1
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:19 ioport:c880(size=32)            
           
                                   id:usb:2
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #3              vendor: Intel Corporation              physical id: 1d.2
              bus info: pci@0000:00:1d.2
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:18 ioport:c800(size=32)            
           
                                   id:usb:3
                description: USB Controller              product: N10/ICH 7 Family USB UHCI Controller #4              vendor: Intel Corporation              physical id: 1d.3
              bus info: pci@0000:00:1d.3
              version: 02              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master               configuration: driver=uhci_hcd latency=0              resources: irq:16 ioport:c480(size=32)            
           
                                   id:usb:4
                description: USB Controller              product: N10/ICH 7 Family USB2 EHCI Controller              vendor: Intel Corporation              physical id: 1d.7
              bus info: pci@0000:00:1d.7
              version: 02              width: 32 bits              clock: 33MHz              capabilities: pm debug ehci bus_master cap_list               configuration: driver=ehci_hcd latency=0              resources: irq:23 memory:fe83bc00-fe83bfff            
           
                                   id:pci:4
                description: PCI bridge              product: 82801 Mobile PCI Bridge              vendor: Intel Corporation              physical id: 1e
              bus info: pci@0000:00:1e.0
              version: e2              width: 32 bits              clock: 33MHz              capabilities: pci subtractive_decode bus_master cap_list             
           
                                   id:isa
                description: ISA bridge              product: 82801GBM (ICH7-M) LPC Interface Bridge              vendor: Intel Corporation              physical id: 1f
              bus info: pci@0000:00:1f.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: isa bus_master cap_list               configuration: latency=0            
           
                                   id:ide
                description: IDE interface              product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller              vendor: Intel Corporation              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              logical name: scsi0
              version: 02              width: 32 bits              clock: 66MHz              capabilities: ide pm bus_master cap_list emulated               configuration: driver=ata_piix latency=0              resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)            
                                            id:disk
                   description: ATA Disk                 product: Hitachi HTS54321                 vendor: Hitachi                 physical id: 0.0.0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/sda
                 version: FB2O                 serial: 090529FB22005CC5P4EA                 size: 149GiB (160GB)                 capabilities: partitioned partitioned:dos                  configuration: ansiversion=5 signature=cb5bd2b2               
                                                     id:volume:0
                      description: Windows NTFS volume                    physical id: 1
                    bus info: scsi@0:0.0.0,1
                    logical name: /dev/sda1
                    version: 3.1                    serial: b2c91ac4-122b-fb4f-9a32-711e4d19081b                    size: 40GiB                    capacity: 40GiB                    capabilities: primary ntfs initialized                     configuration: clustersize=4096 created=2002-01-07 16:40:15 filesystem=ntfs label=WINXP state=clean                  
                 
                                                     id:volume:1
                      description: Windows NTFS volume                    physical id: 2
                    bus info: scsi@0:0.0.0,2
                    logical name: /dev/sda2
                    version: 3.1                    serial: e487-8525                    size: 9504MiB                    capacity: 9507MiB                    capabilities: primary bootable ntfs initialized                     configuration: clustersize=4096 created=2012-03-28 01:46:38 filesystem=ntfs label=WINXP modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true                  
                 
                                                     id:volume:2
                      description: Windows FAT volume                    vendor: MSDOS5.0                    physical id: 3
                    bus info: scsi@0:0.0.0,3
                    logical name: /dev/sda3
                    version: FAT32                    serial: a8ff-d1e1                    size: 5107MiB                    capacity: 5122MiB                    capabilities: primary fat initialized                     configuration: FATs=2 filesystem=fat                  
                 
                                                     id:volume:3
                      description: Extended partition                    physical id: 4
                    bus info: scsi@0:0.0.0,4
                    logical name: /dev/sda4
                    size: 94GiB                    capacity: 94GiB                    capabilities: primary extended partitioned partitioned:extended                   
                                                              id:logicalvolume:0
                         description: Linux filesystem partition                       physical id: 5
                       logical name: /dev/sda5
                       logical name: /
                       capacity: 93GiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted                     
                    
                                                              id:logicalvolume:1
                         description: Linux swap / Solaris partition                       physical id: 6
                       logical name: /dev/sda6
                       capacity: 1022MiB                       capabilities: nofs                      
                    
                 
              
           
                                   id:serial
                description: SMBus              product: N10/ICH 7 Family SMBus Controller              vendor: Intel Corporation              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 02              width: 32 bits              clock: 33MHz              configuration: latency=0              resources: ioport:400(size=32)            
           
        
                          id:scsi
             physical id: 1
           bus info: usb@1:6
           logical name: scsi2
           capabilities: emulated scsi-host            configuration: driver=usb-storage         
                                   id:disk
                description: SCSI Disk              physical id: 0.0.0
              bus info: scsi@2:0.0.0
              logical name: /dev/sdb
              vendor: Intel Corporation              physical id: 1e
              bus info: pci@0000:00:1e.0
              version: e2              width: 32 bits              clock: 33MHz              capabilities: pci subtractive_decode bus_master cap_list             
           
                                   id:isa
                description: ISA bridge              product: 82801GBM (ICH7-M) LPC Interface Bridge              vendor: Intel Corporation              physical id: 1f
              bus info: pci@0000:00:1f.0
              version: 02              width: 32 bits              clock: 33MHz              capabilities: isa bus_master cap_list               configuration: latency=0            
           
                                   id:ide
                description: IDE interface              product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller              vendor: Intel Corporation              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              logical name: scsi0
              version: 02              width: 32 bits              clock: 66MHz              capabilities: ide pm bus_master cap_list emulated               configuration: driver=ata_piix latency=0              resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)            
                                            id:disk
                   description: ATA Disk                 product: Hitachi HTS54321                 vendor: Hitachi                 physical id: 0.0.0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/sda
                 version: FB2O                 serial: 090529FB22005CC5P4EA                 size: 149GiB (160GB)                 capabilities: partitioned partitioned:dos                  configuration: ansiversion=5 signature=cb5bd2b2               
                                                     id:volume:0
                      description: Windows NTFS volume                    physical id: 1
                    bus info: scsi@0:0.0.0,1
                    logical name: /dev/sda1
                    version: 3.1                    serial: b2c91ac4-122b-fb4f-9a32-711e4d19081b                    size: 40GiB                    capacity: 40GiB                    capabilities: primary ntfs initialized                     configuration: clustersize=4096 created=2002-01-07 16:40:15 filesystem=ntfs label=WINXP state=clean                  
                 
                                                     id:volume:1
                      description: Windows NTFS volume                    physical id: 2
                    bus info: scsi@0:0.0.0,2
                    logical name: /dev/sda2
                    version: 3.1                    serial: e487-8525                    size: 9504MiB                    capacity: 9507MiB                    capabilities: primary bootable ntfs initialized                     configuration: clustersize=4096 created=2012-03-28 01:46:38 filesystem=ntfs label=WINXP modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true                  
                 
                                                     id:volume:2
                      description: Windows FAT volume                    vendor: MSDOS5.0                    physical id: 3
                    bus info: scsi@0:0.0.0,3
                    logical name: /dev/sda3
                    version: FAT32                    serial: a8ff-d1e1                    size: 5107MiB                    capacity: 5122MiB                    capabilities: primary fat initialized                     configuration: FATs=2 filesystem=fat                  
                 
                                                     id:volume:3
                      description: Extended partition                    physical id: 4
                    bus info: scsi@0:0.0.0,4
                    logical name: /dev/sda4
                    size: 94GiB                    capacity: 94GiB                    capabilities: primary extended partitioned partitioned:extended                   
                                                              id:logicalvolume:0
                         description: Linux filesystem partition                       physical id: 5
                       logical name: /dev/sda5
                       logical name: /
                       capacity: 93GiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted                     
                    
                                                              id:logicalvolume:1
                         description: Linux swap / Solaris partition                       physical id: 6
                       logical name: /dev/sda6
                       capacity: 1022MiB                       capabilities: nofs                      
                    
                 
              
           
                                   id:serial
                description: SMBus              product: N10/ICH 7 Family SMBus Controller              vendor: Intel Corporation              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 02              width: 32 bits              clock: 33MHz              configuration: latency=0              resources: ioport:400(size=32)            
           
        
                          id:scsi
             physical id: 1
           bus info: usb@1:6
           logical name: scsi2
           capabilities: emulated scsi-host            configuration: driver=usb-storage         
                                   id:disk
                description: SCSI Disk              physical id: 0.0.0
              bus info: scsi@2:0.0.0
              logical name: /dev/sdb
```

---

### Post by JC Cheloven on 2012-04-01
Hi, just a few thoughts:

- When posting some output from a command, please use the 'code' tags to enclose it (the # button at the top of the editing area). You'll get a nice scrollable area instead of that large listing.

- Flash (the technology used by default by youtube and many other video sites), has a rather poor support from its owner (Adobe) under linux. This may cause issues in combination with some specific hardware. The package providing this proprietary software is 'flashplugin-installer'. Please check if it's this one what you have installed. 

- There is a free alternative to play flash. It's called 'gnash', and you can inatsll it from the repositories, to replace the proprietary counterpart. Unfortunately, you should not expect a significant (if any) practical improvement using this. But it's free though.

- Youtube have in beta state the html5 streaming mode, which is somehow the replacement of flash that the free software world is awaiting. You can try it out: in the youtube page scroll down to the bottom, click on 'try something new', and choose html5 from there. You'll be using that instead of flash on youtube from this moment onwards. You may miss some unfinished feature, and minor bugs, but I'd say it's worth to try.

- [disregard]Someone taking the plunge of fixing your exact issue with flash, will surely want to know what model your graphics card is. You can post the oupout of 'lspci' at terminal to anticipate that.[/disregard]
EDIT: sorry, I see: VGA compatible controller product: M92 [Mobility Radeon HD 4500/5100 Series] vendor: ATI Technologies Inc 

Cheers
JC

---

### Post by seal308 on 2012-04-02
K thx

but i dont get the last part of what you said "sorry, I see: VGA compatible controller product: M92 [Mobility Radeon HD 4500/5100 Series] vendor: ATI Technologies Inc "

how do i check if i have that plugin?
what does that mean. Is my graphics card ok?
I switched to html5 for youtube. Works great but it doesn't work with video with ads.
Sorry again about the code, i'm total newbie.

```
id:glenn-eb1006
description: Desktop Computer version: System Version width: 32 bits capabilities: smbios-2.5 dmi-2.5 configuration: boot=normal chassis=desktop family=Eee Family sku=To Be Filled By O.E.M. uuid=606A40CC-8EFE-D511-8BB2-002618CCF599 id:core
description: Motherboard product: P5G-EB1006-DHS vendor: ASUSTeK Computer INC. physical id: 0
version: Rev 1.xx serial: MF7098G01600425 slot: To Be Filled By O.E.M. 
id:firmware
description: BIOS vendor: American Megatrends Inc. physical id: 0
version: 0501 date: 07/31/2009 size: 64KiB capacity: 960KiB capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification 

id:cpu
description: CPU product: Intel(R) Atom(TM) CPU N270 @ 1.60GHz vendor: Intel Corp. physical id: 4
bus info: cpu@0
version: 6.12.2 serial: 0001-06C2-0000-0000-0000-0000 slot: CPU 1 size: 1600MHz capacity: 3800MHz width: 32 bits clock: 133MHz capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq configuration: cores=1 enabledcores=1 id=1 threads=2 
id:cache:0
description: L1 cache physical id: 5
slot: L1-Cache size: 24KiB capacity: 24KiB capabilities: internal write-back data 

id:cache:1
description: L2 cache physical id: 6
slot: L2-Cache size: 512KiB capacity: 512KiB capabilities: internal write-back unified 

id:logicalcpu:0
description: Logical CPU physical id: 1.1
width: 32 bits capabilities: logical 

id:logicalcpu:1
description: Logical CPU physical id: 1.2
width: 32 bits capabilities: logical 


id:memory
description: System Memory physical id: e
slot: System board or motherboard size: 1GiB 
id:bank:0
description: DIMM DDR2 Synchronous 533 MHz (1.9 ns) product: PartNum0 vendor: Manufacturer0 physical id: 0
serial: SerNum0 slot: DIMM0 size: 1GiB width: 64 bits clock: 533MHz (1.9ns) 

id:bank:1
description: DIMM [empty] product: PartNum1 vendor: Manufacturer1 physical id: 1
serial: SerNum1 slot: DIMM1 


idci
description: Host bridge product: Mobile 945GME Express Memory Controller Hub vendor: Intel Corporation physical id: 100
bus info: pci@0000:00:00.0
version: 03 width: 32 bits clock: 33MHz 
id:multimedia
description: Audio device product: N10/ICH 7 Family High Definition Audio Controller vendor: Intel Corporation physical id: 1b
bus info: pci@0000:00:1b.0
version: 02 width: 64 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list configuration: driver=HDA Intel latency=0 resources: irq:45 memory:fe83c000-fe83ffff 

idci:0
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 1 vendor: Intel Corporation physical id: 1c
bus info: pci@0000:00:1c.0
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:40 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:cff00000(size=1048576) 
id:network
description: Ethernet interface product: RTL8111/8168B PCI Express Gigabit Ethernet controller vendor: Realtek Semiconductor Co., Ltd. physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: 02 serial: 00:26:18:cc:f5:99 size: 1Gbit/s capacity: 1Gbit/s width: 64 bits clock: 33MHz capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.192 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s resources: irq:44 ioport:dc00(size=256) memory:fe9ff000-fe9fffff memory:cfff0000-cfffffff memory:fe9c0000-fe9dffff 


idci:1
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 2 vendor: Intel Corporation physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:41 ioport:2000(size=4096) memory:fea00000-feafffff ioport:40400000(size=2097152) 
id:network
description: Wireless interface product: AR9285 Wireless Network Adapter (PCI-Express) vendor: Atheros Communications Inc. physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01 serial: 00:25:d3:66:e4:12 width: 64 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=ath9k driverversion=3.0.0-17-generic firmware=N/A ip=192.168.0.193 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn resources: irq:17 memory:feaf0000-feafffff 


idci:2
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 3 vendor: Intel Corporation physical id: 1c.2
bus info: pci@0000:00:1c.2
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:d0000000(size=268435456) 
id:display
description: VGA compatible controller product: M92 [Mobility Radeon HD 4500/5100 Series] vendor: ATI Technologies Inc physical id: 0
bus info: pci@0000:03:00.0
version: 00 width: 64 bits clock: 33MHz capabilities: pm pciexpress msi vga_controller bus_master cap_list rom configuration: driver=radeon latency=0 resources: irq:47 memory:d0000000-dfffffff memory:febf0000-febfffff ioport:e800(size=256) memory:febc0000-febdffff 

id:multimedia
description: Audio device product: RV710/730 vendor: ATI Technologies Inc physical id: 0.1
bus info: pci@0000:03:00.1
version: 00 width: 64 bits clock: 33MHz capabilities: pm pciexpress msi bus_master cap_list configuration: driver=HDA Intel latency=0 resources: irq:46 memory:febec000-febeffff 


idci:3
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 4 vendor: Intel Corporation physical id: 1c.3
bus info: pci@0000:00:1c.3
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:43 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152) 

id:usb:0
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #1 vendor: Intel Corporation physical id: 1d
bus info: pci@0000:00:1d.0
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:23 ioport:cc00(size=32) 

id:usb:1
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #2 vendor: Intel Corporation physical id: 1d.1
bus info: pci@0000:00:1d.1
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:19 ioport:c880(size=32) 

id:usb:2
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #3 vendor: Intel Corporation physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:18 ioport:c800(size=32) 

id:usb:3
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #4 vendor: Intel Corporation physical id: 1d.3
bus info: pci@0000:00:1d.3
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:16 ioport:c480(size=32) 

id:usb:4
description: USB Controller product: N10/ICH 7 Family USB2 EHCI Controller vendor: Intel Corporation physical id: 1d.7
bus info: pci@0000:00:1d.7
version: 02 width: 32 bits clock: 33MHz capabilities: pm debug ehci bus_master cap_list configuration: driver=ehci_hcd latency=0 resources: irq:23 memory:fe83bc00-fe83bfff 

idci:4
description: PCI bridge product: 82801 Mobile PCI Bridgeid:glenn-eb1006
description: Desktop Computer version: System Version width: 32 bits capabilities: smbios-2.5 dmi-2.5 configuration: boot=normal chassis=desktop family=Eee Family sku=To Be Filled By O.E.M. uuid=606A40CC-8EFE-D511-8BB2-002618CCF599 id:core
description: Motherboard product: P5G-EB1006-DHS vendor: ASUSTeK Computer INC. physical id: 0
version: Rev 1.xx serial: MF7098G01600425 slot: To Be Filled By O.E.M. 
id:firmware
description: BIOS vendor: American Megatrends Inc. physical id: 0
version: 0501 date: 07/31/2009 size: 64KiB capacity: 960KiB capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification 

id:cpu
description: CPU product: Intel(R) Atom(TM) CPU N270 @ 1.60GHz vendor: Intel Corp. physical id: 4
bus info: cpu@0
version: 6.12.2 serial: 0001-06C2-0000-0000-0000-0000 slot: CPU 1 size: 1600MHz capacity: 3800MHz width: 32 bits clock: 133MHz capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq configuration: cores=1 enabledcores=1 id=1 threads=2 
id:cache:0
description: L1 cache physical id: 5
slot: L1-Cache size: 24KiB capacity: 24KiB capabilities: internal write-back data 

id:cache:1
description: L2 cache physical id: 6
slot: L2-Cache size: 512KiB capacity: 512KiB capabilities: internal write-back unified 

id:logicalcpu:0
description: Logical CPU physical id: 1.1
width: 32 bits capabilities: logical 

id:logicalcpu:1
description: Logical CPU physical id: 1.2
width: 32 bits capabilities: logical 


id:memory
description: System Memory physical id: e
slot: System board or motherboard size: 1GiB 
id:bank:0
description: DIMM DDR2 Synchronous 533 MHz (1.9 ns) product: PartNum0 vendor: Manufacturer0 physical id: 0
serial: SerNum0 slot: DIMM0 size: 1GiB width: 64 bits clock: 533MHz (1.9ns) 

id:bank:1
description: DIMM [empty] product: PartNum1 vendor: Manufacturer1 physical id: 1
serial: SerNum1 slot: DIMM1 


idci
description: Host bridge product: Mobile 945GME Express Memory Controller Hub vendor: Intel Corporation physical id: 100
bus info: pci@0000:00:00.0
version: 03 width: 32 bits clock: 33MHz 
id:multimedia
description: Audio device product: N10/ICH 7 Family High Definition Audio Controller vendor: Intel Corporation physical id: 1b
bus info: pci@0000:00:1b.0
version: 02 width: 64 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list configuration: driver=HDA Intel latency=0 resources: irq:45 memory:fe83c000-fe83ffff 

idci:0
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 1 vendor: Intel Corporation physical id: 1c
bus info: pci@0000:00:1c.0
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:40 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:cff00000(size=1048576) 
id:network
description: Ethernet interface product: RTL8111/8168B PCI Express Gigabit Ethernet controller vendor: Realtek Semiconductor Co., Ltd. physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: 02 serial: 00:26:18:cc:f5:99 size: 1Gbit/s capacity: 1Gbit/s width: 64 bits clock: 33MHz capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.192 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s resources: irq:44 ioport:dc00(size=256) memory:fe9ff000-fe9fffff memory:cfff0000-cfffffff memory:fe9c0000-fe9dffff 


idci:1
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 2 vendor: Intel Corporation physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:41 ioport:2000(size=4096) memory:fea00000-feafffff ioport:40400000(size=2097152) 
id:network
description: Wireless interface product: AR9285 Wireless Network Adapter (PCI-Express) vendor: Atheros Communications Inc. physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01 serial: 00:25:d3:66:e4:12 width: 64 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=ath9k driverversion=3.0.0-17-generic firmware=N/A ip=192.168.0.193 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn resources: irq:17 memory:feaf0000-feafffff 


idci:2
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 3 vendor: Intel Corporation physical id: 1c.2
bus info: pci@0000:00:1c.2
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:d0000000(size=268435456) 
id:display
description: VGA compatible controller product: M92 [Mobility Radeon HD 4500/5100 Series] vendor: ATI Technologies Inc physical id: 0
bus info: pci@0000:03:00.0
version: 00 width: 64 bits clock: 33MHz capabilities: pm pciexpress msi vga_controller bus_master cap_list rom configuration: driver=radeon latency=0 resources: irq:47 memory:d0000000-dfffffff memory:febf0000-febfffff ioport:e800(size=256) memory:febc0000-febdffff 

id:multimedia
description: Audio device product: RV710/730 vendor: ATI Technologies Inc physical id: 0.1
bus info: pci@0000:03:00.1
version: 00 width: 64 bits clock: 33MHz capabilities: pm pciexpress msi bus_master cap_list configuration: driver=HDA Intel latency=0 resources: irq:46 memory:febec000-febeffff 


idci:3
description: PCI bridge product: N10/ICH 7 Family PCI Express Port 4 vendor: Intel Corporation physical id: 1c.3
bus info: pci@0000:00:1c.3
version: 02 width: 32 bits clock: 33MHz capabilities: pci pciexpress msi pm normal_decode bus_master cap_list configuration: driver=pcieport resources: irq:43 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152) 

id:usb:0
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #1 vendor: Intel Corporation physical id: 1d
bus info: pci@0000:00:1d.0
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:23 ioport:cc00(size=32) 

id:usb:1
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #2 vendor: Intel Corporation physical id: 1d.1
bus info: pci@0000:00:1d.1
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:19 ioport:c880(size=32) 

id:usb:2
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #3 vendor: Intel Corporation physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:18 ioport:c800(size=32) 

id:usb:3
description: USB Controller product: N10/ICH 7 Family USB UHCI Controller #4 vendor: Intel Corporation physical id: 1d.3
bus info: pci@0000:00:1d.3
version: 02 width: 32 bits clock: 33MHz capabilities: uhci bus_master configuration: driver=uhci_hcd latency=0 resources: irq:16 ioport:c480(size=32) 

id:usb:4
description: USB Controller product: N10/ICH 7 Family USB2 EHCI Controller vendor: Intel Corporation physical id: 1d.7
bus info: pci@0000:00:1d.7
version: 02 width: 32 bits clock: 33MHz capabilities: pm debug ehci bus_master cap_list configuration: driver=ehci_hcd latency=0 resources: irq:23 memory:fe83bc00-fe83bfff 

idci:4
description: PCI bridge product: 82801 Mobile PCI Bridge vendor: Intel Corporation physical id: 1e
bus info: pci@0000:00:1e.0
version: e2 width: 32 bits clock: 33MHz capabilities: pci subtractive_decode bus_master cap_list 

id:isa
description: ISA bridge product: 82801GBM (ICH7-M) LPC Interface Bridge vendor: Intel Corporation physical id: 1f
bus info: pci@0000:00:1f.0
version: 02 width: 32 bits clock: 33MHz capabilities: isa bus_master cap_list configuration: latency=0 

id:ide
description: IDE interface product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller vendor: Intel Corporation physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi0
version: 02 width: 32 bits clock: 66MHz capabilities: ide pm bus_master cap_list emulated configuration: driver=ata_piix latency=0 resources: irq:19 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:ffa0(size=16) 
id:disk
description: ATA Disk product: Hitachi HTS54321 vendor: Hitachi physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: FB2O serial: 090529FB22005CC5P4EA size: 149GiB (160GB) capabilities: partitioned partitioned:dos configuration: ansiversion=5 signature=cb5bd2b2 
id:volume:0
description: Windows NTFS volume physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
version: 3.1 serial: b2c91ac4-122b-fb4f-9a32-711e4d19081b size: 40GiB capacity: 40GiB capabilities: primary ntfs initialized configuration: clustersize=4096 created=2002-01-07 16:40:15 filesystem=ntfs label=WINXP state=clean 

id:volume:1
description: Windows NTFS volume physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
version: 3.1 serial: e487-8525 size: 9504MiB capacity: 9507MiB capabilities: primary bootable ntfs initialized configuration: clustersize=4096 created=2012-03-28 01:46:38 filesystem=ntfs label=WINXP modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true 

id:volume:2
description: Windows FAT volume vendor: MSDOS5.0 physical id: 3
bus info: scsi@0:0.0.0,3
logical name: /dev/sda3
version: FAT32 serial: a8ff-d1e1 size: 5107MiB capacity: 5122MiB capabilities: primary fat initialized configuration: FATs=2 filesystem=fat 

id:volume:3
description: Extended partition physical id: 4
bus info: scsi@0:0.0.0,4
logical name: /dev/sda4
size: 94GiB capacity: 94GiB capabilities: primary extended partitioned partitioned:extended 
id:logicalvolume:0
description: Linux filesystem partition physical id: 5
logical name: /dev/sda5
logical name: /
capacity: 93GiB configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted 

id:logicalvolume:1
description: Linux swap / Solaris partition physical id: 6
logical name: /dev/sda6
capacity: 1022MiB capabilities: nofs 




id:serial
description: SMBus product: N10/ICH 7 Family SMBus Controller vendor: Intel Corporation physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 02 width: 32 bits clock: 33MHz configuration: latency=0 resources: ioport:400(size=32) 


id:scsi
physical id: 1
bus info: usb@1:6
logical name: scsi2
capabilities: emulated scsi-host configuration: driver=usb-storage 
id:disk
description: SCSI Disk physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sdb
vendor: Intel Corporation physical id: 1e
bus info: pci@0000:00:1e.0
version: e2 width: 32 bits clock: 33MHz capabilities: pci subtractive_decode bus_master cap_list 

id:isa
description: ISA bridge product: 82801GBM (ICH7-M) LPC Interface Bridge vendor: Intel Corporation physical id: 1f
bus info: pci@0000:00:1f.0
version: 02 width: 32 bits clock: 33MHz capabilities: isa bus_master cap_list configuration: latency=0 

id:ide
description: IDE interface product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller vendor: Intel Corporation physical id: 1f.2
bus info: pci@0000:00:1f.2
logical name: scsi0
version: 02 width: 32 bits clock: 66MHz capabilities: ide pm bus_master cap_list emulated configuration: driver=ata_piix latency=0 resources: irq:19 ioport:1f0(size= ioport:3f6 ioport:170(size= ioport:376 ioport:ffa0(size=16) 
id:disk
description: ATA Disk product: Hitachi HTS54321 vendor: Hitachi physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: FB2O serial: 090529FB22005CC5P4EA size: 149GiB (160GB) capabilities: partitioned partitioned:dos configuration: ansiversion=5 signature=cb5bd2b2 
id:volume:0
description: Windows NTFS volume physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
version: 3.1 serial: b2c91ac4-122b-fb4f-9a32-711e4d19081b size: 40GiB capacity: 40GiB capabilities: primary ntfs initialized configuration: clustersize=4096 created=2002-01-07 16:40:15 filesystem=ntfs label=WINXP state=clean 

id:volume:1
description: Windows NTFS volume physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
version: 3.1 serial: e487-8525 size: 9504MiB capacity: 9507MiB capabilities: primary bootable ntfs initialized configuration: clustersize=4096 created=2012-03-28 01:46:38 filesystem=ntfs label=WINXP modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true 

id:volume:2
description: Windows FAT volume vendor: MSDOS5.0 physical id: 3
bus info: scsi@0:0.0.0,3
logical name: /dev/sda3
version: FAT32 serial: a8ff-d1e1 size: 5107MiB capacity: 5122MiB capabilities: primary fat initialized configuration: FATs=2 filesystem=fat 

id:volume:3
description: Extended partition physical id: 4
bus info: scsi@0:0.0.0,4
logical name: /dev/sda4
size: 94GiB capacity: 94GiB capabilities: primary extended partitioned partitioned:extended 
id:logicalvolume:0
description: Linux filesystem partition physical id: 5
logical name: /dev/sda5
logical name: /
capacity: 93GiB configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted 

id:logicalvolume:1
description: Linux swap / Solaris partition physical id: 6
logical name: /dev/sda6
capacity: 1022MiB capabilities: nofs 




id:serial
description: SMBus product: N10/ICH 7 Family SMBus Controller vendor: Intel Corporation physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 02 width: 32 bits clock: 33MHz configuration: latency=0 resources: ioport:400(size=32) 


id:scsi
physical id: 1
bus info: usb@1:6
logical name: scsi2
capabilities: emulated scsi-host configuration: driver=usb-storage 
id:disk
description: SCSI Disk physical id: 0.0.0
bus info: scsi@2:0.0.0
logical name: /dev/sdb
```

---

### Post by JC Cheloven on 2012-04-02
> **seal308 said:**
> K thx but i dont get the last part of what you said "sorry, I see: VGA compatible controller product: M92 [Mobility Radeon HD 4500/5100 Series] vendor: ATI Technologies Inc "
Oh, don't worry. I was asking you for your graphics card model, then realized that this info was already present in the long output, so I edited my post to say sorry, and transcribed what your card model is :)

> how do i check if i have that plugin?
Well, you more than likely have it if you saw youtube before. Anyway, let's go the quick'n'dirty way. Try to install it, if it is already installed, you will be told; if it's not installed, it will be installed, which is good for you to try. So run ```
sudo apt-get install flashplugin-installer
```

> what does that mean. Is my graphics card ok?
Yes it should be ok, as for ubuntu. It is supported by the catalyst driver. Please check with the 'additional drivers' utility if it is installed and in use (may appear as 'fglrx'). But please note: this does not guarantee that you're safe from issues with something like flash.

> I switched to html5 for youtube. Works great but it doesn't work with video with ads. Yep, as noticed [here]("http://www.youtube.com/html5"), videos with advertisement fall back to the flash playback mode.

---

