---
title: "DVD drive not recognized."
date: 2013-04-10
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-10
Ubuntu was recognizing the DVD any time I inserted a disk and closed it up but now, it isn't. I have installed WINE and drivers for Atheros ethernet since then but don't know if that is causing my issues.

How do I go about getting Ubuntu to see the drive and make it accessible?](*,)

This is what I get when I use lshw in terminal to look around:

```
ubuntu
    description: Notebook
    product: Satellite C855 (PSC72U-01600C)
    vendor: TOSHIBA
    version: PSC72U-01600C
    serial: 5C265949Q
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=Dakar 10F/FG sku=PSC72U-01600C uuid=831A4A50-A058-11E1-83B4-00266C17DA3A
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: MP
       serial: 1
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: 6.60
          date: 01/14/2013
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2370M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2370M CPU @ 2.40GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: b
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 8
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273CH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 0086C211
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: Empty
             slot: DIMM2
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:b8000000-b83fffff memory:b0000000-b7ffffff ioport:4000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:b8600000-b860ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:b8614000-b861400f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:b8619000-b86193ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:b8610000-b8613fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:b8500000-b85fffff
           *-network
                description: Ethernet interface
                product: AR8162 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 10
                serial: 00:26:6c:17:da:3a
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx ip=10.5.4.20 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:42 memory:b8500000-b853ffff ioport:3000(size=128)
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:b8400000-b84fffff
           *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 44:6d:57:92:21:c6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-17-generic firmware=N/A ip=192.168.0.202 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:2000(size=256) memory:b8400000-b8403fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b8618000-b86183ff
        *-isa
             description: ISA bridge
             product: HM76 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:b8617000-b86177ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b8615000-b86150ff ioport:4040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD0
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: AX00
             serial: 32ORT3VKT
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=ac1454cd
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 423f-0bf5
                size: 1498MiB
                capacity: 1500MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-08-12 03:50:10 filesystem=ntfs label=System state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /host
                version: 3.1
                serial: 466aecc1-0cbd-c340-8938-992104fe3b33
                size: 450GiB
                capacity: 451GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-08-12 03:51:12 filesystem=ntfs label=TI106401W0D mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: c034-c227
                size: 13GiB
                capacity: 13GiB
                capabilities: primary hidden ntfs initialized
                configuration: clustersize=4096 created=2012-04-09 21:05:43 filesystem=ntfs label=HDDRECOVERY state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SN-208AB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: TO03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-scsi:2
          physical id: 3
          bus info: usb@1:1.1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=rts5139
        *-disk
             description: SCSI Disk
             product: xD/SD/M.S.
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 3
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
```

---

### Post by alhefner on 2013-04-10
Anyone?

---

### Post by alhefner on 2013-04-11
OK, seems that if the DVD contains only what is already in the "home" folder, then the system ignores it... Anyway, that's how it seems to be working.

---

