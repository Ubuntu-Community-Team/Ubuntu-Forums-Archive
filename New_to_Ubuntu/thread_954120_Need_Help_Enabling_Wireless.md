---
title: "Need Help Enabling Wireless"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2008-10-20
I recently installed Hardy to dual boot on my Pavilion laptop and cannot detect any wireless networks while using Ubuntu. If anyone could help me out I would appreciate it.

---

### Post by skaldicpoet9 on 2008-10-21
Sorry it's been awhile since I had to do this and I forgot to give you guys this:

results of sudo lshw:

```

skaldicpoet9@Ragnar:~$ sudo lshw 
[sudo] password for skaldicpoet9: 
ragnar                    
    description: Notebook 
    product: HP Pavilion dv2700 Notebook PC 
    vendor: Hewlett-Packard 
    version: F.24 
    serial: 2CE80946J5 
    width: 32 bits 
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp 
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=881D2660-EFC4-11DC-BE76-C519743A7F94 
  *-core 
       description: Motherboard 
       product: 30D6 
       vendor: Wistron 
       physical id: 0 
       version: 81.53 
       slot: &#65533;&#65533;? 
     *-firmware 
          description: BIOS 
          vendor: Hewlett-Packard 
          physical id: 0 
          version: F.24 (04/24/2008) 
          size: 99KiB 
          capacity: 960KiB 
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification 
     *-cpu 
          description: CPU 
          product: AMD Turion(tm) 64 X2 TL-62 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 3 
          bus info: cpu@0 
          version: 15.8.2 
          slot: Socket A 
          size: 2100MHz 
          capacity: 2100MHz 
          width: 64 bits 
          clock: 200MHz 
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq 
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
             size: 1MiB 
             capacity: 2MiB 
             capabilities: synchronous internal write-through unified 
     *-memory:0 
          description: System Memory 
          physical id: b 
          slot: System board or motherboard 
          size: 4GiB 
        *-bank:0 
             description: SODIMM DDR Synchronous 667 MHz (1.5 ns) 
             physical id: 0 
             slot: M1 
             size: 2GiB 
             width: 32 bits 
             clock: 667MHz (1.5ns) 
        *-bank:1 
             description: SODIMM DDR Synchronous 667 MHz (1.5 ns) 
             physical id: 1 
             slot: M2 
             size: 2GiB 
             width: 32 bits 
             clock: 667MHz (1.5ns) 
     *-memory:1 UNCLAIMED 
          description: RAM memory 
          product: MCP67 Memory Controller 
          vendor: nVidia Corporation 
          physical id: 4 
          bus info: pci@0000:00:00.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz (15.2ns) 
          capabilities: ht bus_master cap_list 
          configuration: latency=0 
     *-isa 
          description: ISA bridge 
          product: MCP67 ISA Bridge 
          vendor: nVidia Corporation 
          physical id: 1 
          bus info: pci@0000:00:01.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: isa bus_master 
          configuration: latency=0 
     *-serial UNCLAIMED 
          description: SMBus 
          product: MCP67 SMBus 
          vendor: nVidia Corporation 
          physical id: 1.1 
          bus info: pci@0000:00:01.1 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm cap_list 
          configuration: latency=0 
     *-memory:2 UNCLAIMED 
          description: RAM memory 
          product: MCP67 Memory Controller 
          vendor: nVidia Corporation 
          physical id: 1.2 
          bus info: pci@0000:00:01.2 
          version: a2 
          width: 32 bits 
          clock: 66MHz (15.2ns) 
          configuration: latency=0 
     *-processor UNCLAIMED 
          description: Co-processor 
          product: MCP67 Co-processor 
          vendor: nVidia Corporation 
          physical id: 1.3 
          bus info: pci@0000:00:01.3 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: bus_master 
          configuration: latency=0 maxlatency=1 mingnt=3 
     *-usb:0 
          description: USB Controller 
          product: MCP67 OHCI USB 1.1 Controller 
          vendor: nVidia Corporation 
          physical id: 2 
          bus info: pci@0000:00:02.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm ohci bus_master cap_list 
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd 
     *-usb:1 
          description: USB Controller 
          product: MCP67 EHCI USB 2.0 Controller 
          vendor: nVidia Corporation 
          physical id: 2.1 
          bus info: pci@0000:00:02.1 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: debug pm ehci bus_master cap_list 
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd 
     *-usb:2 
          description: USB Controller 
          product: MCP67 OHCI USB 1.1 Controller 
          vendor: nVidia Corporation 
          physical id: 5 
          bus info: pci@0000:00:04.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm ohci bus_master cap_list 
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd 
     *-usb:3 
          description: USB Controller 
          product: MCP67 EHCI USB 2.0 Controller 
          vendor: nVidia Corporation 
          physical id: 4.1 
          bus info: pci@0000:00:04.1 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: debug pm ehci bus_master cap_list 
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd 
     *-ide:0 
          description: IDE interface 
          product: MCP67 IDE Controller 
          vendor: nVidia Corporation 
          physical id: 6 
          bus info: pci@0000:00:06.0 
          logical name: scsi0 
          version: a1 
          width: 32 bits 
          clock: 66MHz 
          capabilities: ide pm bus_master cap_list emulated 
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd 
        *-cdrom 
             description: DVD-RAM writer 
             product: DVD RW AD-7561A 
             vendor: Optiarc 
             physical id: 0.0.0 
             bus info: scsi@0:0.0.0 
             logical name: /dev/cdrom 
             logical name: /dev/dvd 
             logical name: /dev/scd0 
             logical name: /dev/sr0 
             version: GH09 
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram 
             configuration: ansiversion=5 status=open 
     *-multimedia 
          description: Audio device 
          product: MCP67 High Definition Audio 
          vendor: nVidia Corporation 
          physical id: 7 
          bus info: pci@0000:00:07.0 
          version: a1 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm msi ht bus_master cap_list 
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel 
     *-pci:0 
          description: PCI bridge 
          product: MCP67 PCI Bridge 
          vendor: nVidia Corporation 
          physical id: 8 
          bus info: pci@0000:00:08.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pci ht subtractive_decode bus_master cap_list 
        *-firewire 
             description: FireWire (IEEE 1394) 
             product: R5C832 IEEE 1394 Controller 
             vendor: Ricoh Co Ltd 
             physical id: 9 
             bus info: pci@0000:01:09.0 
             version: 05 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm ohci bus_master cap_list 
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394 
        *-system:0 
             description: SD Host controller 
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter 
             vendor: Ricoh Co Ltd 
             physical id: 9.1 
             bus info: pci@0000:01:09.1 
             version: 22 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: driver=sdhci latency=64 module=sdhci 
        *-system:1 UNCLAIMED 
             description: System peripheral 
             product: R5C592 Memory Stick Bus Host Adapter 
             vendor: Ricoh Co Ltd 
             physical id: 9.2 
             bus info: pci@0000:01:09.2 
             version: 12 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: latency=64 
        *-system:2 UNCLAIMED 
             description: System peripheral 
             product: xD-Picture Card Controller 
             vendor: Ricoh Co Ltd 
             physical id: 9.3 
             bus info: pci@0000:01:09.3 
             version: 12 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: latency=64 
     *-ide:1 
          description: IDE interface 
          product: MCP67 AHCI Controller 
          vendor: nVidia Corporation 
          physical id: 9 
          bus info: pci@0000:00:09.0 
          logical name: scsi3 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: ide pm msi ht bus_master cap_list emulated 
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci 
        *-disk 
             description: ATA Disk 
             product: WDC WD2500BEVS-6 
             vendor: Western Digital 
             physical id: 0.0.0 
             bus info: scsi@3:0.0.0 
             logical name: /dev/sda 
             version: 01.0 
             serial: WD-WXC208308694 
             size: 232GiB (250GB) 
             capabilities: partitioned partitioned:dos 
             configuration: ansiversion=5 signature=8ffe8ffe 
           *-volume:0 
                description: Windows NTFS volume 
                physical id: 1 
                bus info: scsi@3:0.0.0,1 
                logical name: /dev/sda1 
                version: 3.1 
                serial: 460bd577-8fa6-a641-95ab-85a411fc8da4 
                size: 199GiB 
                capacity: 199GiB 
                capabilities: primary bootable ntfs initialized 
                configuration: clustersize=4096 created=2008-07-30 04:32:02 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true 
           *-volume:1 
                description: Extended partition 
                physical id: 2 
                bus info: scsi@3:0.0.0,2 
                logical name: /dev/sda2 
                size: 32GiB 
                capacity: 32GiB 
                capabilities: primary extended partitioned partitioned:extended 
              *-logicalvolume:0 
                   description: Linux filesystem partition 
                   physical id: 5 
                   logical name: /dev/sda5 
                   capacity: 10GiB 
              *-logicalvolume:1 
                   description: Linux swap / Solaris partition 
                   physical id: 6 
                   logical name: /dev/sda6 
                   capacity: 541MiB 
                   capabilities: nofs 
              *-logicalvolume:2 
                   description: Linux filesystem partition 
                   physical id: 7 
                   logical name: /dev/sda7 
                   capacity: 10GiB 
              *-logicalvolume:3 
                   description: Linux swap / Solaris partition 
                   physical id: 8 
                   logical name: /dev/sda8 
                   capacity: 525MiB 
                   capabilities: nofs 
              *-logicalvolume:4 
                   description: Linux filesystem partition 
                   physical id: 9 
                   logical name: /dev/sda9 
                   logical name: / 
                   logical name: /dev/.static/dev 
                   capacity: 10GiB 
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted 
              *-logicalvolume:5 
                   description: Linux swap / Solaris partition 
                   physical id: a 
                   logical name: /dev/sda10 
                   capacity: 502MiB 
                   capabilities: nofs 
     *-network 
          description: Ethernet interface 
          product: MCP67 Ethernet 
          vendor: nVidia Corporation 
          physical id: a 
          bus info: pci@0000:00:0a.0 
          logical name: eth0 
          version: a2 
          serial: 00:1d:72:4d:18:82 
          capacity: 100MB/s 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII 
     *-pci:1 
          description: PCI bridge 
          product: MCP67 PCI Express Bridge 
          vendor: nVidia Corporation 
          physical id: c 
          bus info: pci@0000:00:0c.0 
          version: a2 
          width: 32 bits 
          clock: 33MHz 
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
          configuration: driver=pcieport-driver 
     *-pci:2 
          description: PCI bridge 
          product: MCP67 PCI Express Bridge 
          vendor: nVidia Corporation 
          physical id: d 
          bus info: pci@0000:00:0d.0 
          version: a2 
          width: 32 bits 
          clock: 33MHz 
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
          configuration: driver=pcieport-driver 
        *-network UNCLAIMED 
             description: Network controller 
             product: BCM4310 USB Controller 
             vendor: Broadcom Corporation 
             physical id: 0 
             bus info: pci@0000:04:00.0 
             version: 01 
             width: 64 bits 
             clock: 33MHz 
             capabilities: pm msi pciexpress bus_master cap_list 
             configuration: latency=0 
     *-display UNCLAIMED 
          description: VGA compatible controller 
          product: GeForce 7150M 
          vendor: nVidia Corporation 
          physical id: 12 
          bus info: pci@0000:00:12.0 
          version: a2 
          width: 64 bits 
          clock: 66MHz 
          capabilities: pm msi vga_controller bus_master cap_list 
          configuration: latency=0 
     *-pci:3 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 100 
          bus info: pci@0000:00:18.0 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:4 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Address Map 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 101 
          bus info: pci@0000:00:18.1 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:5 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] DRAM Controller 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 102 
          bus info: pci@0000:00:18.2 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:6 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Miscellaneous Control 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 103 
          bus info: pci@0000:00:18.3 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
          configuration: driver=k8temp module=k8temp 
skaldicpoet9@Ragnar:~$ sudo iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
```

and the wireless card I am using is a Broadcom 4310.

---

