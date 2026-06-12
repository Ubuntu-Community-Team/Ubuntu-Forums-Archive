---
title: "the graphic dont feel the smooth"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by blake7 on 2012-01-05
i have a ibm x60
it does not feel very smooth for exampal the iplayer when played in the lastest windows works with out any problem and in fact windows runs very well indeed. much to my surprise but ubuntu just feels slow is there any simple things i could try frist to make the feel as smooth as windows


thank you

---

### Post by Anstice on 2012-01-05
What spec is your machine and what version of Ubuntu are you running? 
I have the X60 and it works perfectly with 10.10. I only tried 11.04 onwards for a few days but that still ran well.

---

### Post by wildmanne39 on 2012-01-05
Hi, please post the results of:
```
sudo lshw
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by blake7 on 2012-01-09
thank you
```
oh-thinkpad-x61s          
    description: Notebook
    version: ThinkPad X61s
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 family=ThinkPad X61s frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=8D198701-49C0-11CB-B992-89BD53D46215
  *-core
       description: Motherboard
       product: 766634G
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZDXF79R20L
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7NET25WW (1.06 )
          date: 07/02/2007
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: None
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 4MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f8000000-f80fffff memory:e0000000-efffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8100000-f81fffff
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:16:d3:cc:60:80
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:42 memory:f8200000-f821ffff memory:f8225000-f8225fff ioport:1840(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:f8426400-f84267ff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:f8220000-f8223fff
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
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f4000000-f5ffffff ioport:f8500000(size=1048576)
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
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f6000000-f7ffffff ioport:f8600000(size=1048576)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 61
                serial: 00:13:e8:d9:5f:5d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-14-generic firmware=228.61.2.24 ip=192.168.0.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:44 memory:f7f00000-f7f01fff
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f8426800-f8426bff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:4000(size=16384) memory:d4000000-d7efffff ioport:d8000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:05:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00706050-b0070604f irq:16 memory:d7eff000-d7efffff ioport:4000(size=256) ioport:4400(size=256) memory:d8000000-dbffffff memory:60000000-63ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:17 memory:d7efe800-d7efefff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:05:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:d7efe400-d7efe4ff
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c10(size=16) ioport:1c00(size=16)
           *-disk
                description: ATA Disk
                product: HITACHI HTS54166
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SBBI
                serial: SB2B41SLCAJL4E
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1d9af8fc
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: d2935091-d987-5148-b21e-047f37ea8d32
                   size: 40GiB
                   capacity: 40GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-03-18 04:20:40 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 14GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1508MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD/CDRW UJDA775
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CB03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
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
             resources: memory:f8426c00-f8426cff ioport:1c20(size=32)
```

---

### Post by Mark Phelps on 2012-01-09
The ThinkWIKI web pages provide a massive amount of info regarding the use of ThinkPads.

The page below is to the link for your PC for the graphics:

[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100]("http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100")

---

### Post by blake7 on 2012-01-09
cheers i look into that

---

### Post by wildmanne39 on 2012-01-09
Hi, from your system specs if you are using 11.04 or 11.10 ubuntu you may want to log in as classic no effects to get better performance.
Thanks

---

