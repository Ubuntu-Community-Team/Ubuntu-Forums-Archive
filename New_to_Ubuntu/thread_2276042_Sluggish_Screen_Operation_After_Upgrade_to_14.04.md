---
title: "Sluggish Screen Operation After Upgrade to 14.04"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by John_Mackenzie on 2015-04-30
After clean LTS upgrade to 14.04, have sluggish screen menus, slow slider buttons etc. but UGI still functions - barely.  Suspect video card on this old 32 bit Acer desktop is nearly over loaded.

What diagnostics should I run to investigate the problem further?

I can easily live with Xbuntu or other lighter version of software if the full featured Ubuntu is taxing my hardware.  

Will a lighter version of Ubuntu help solve my problem?

---

### Post by mörgæs on 2015-04-30
> **John_Mackenzie said:**
> 
What diagnostics should I run to investigate the problem further?


Let's begin with the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by John_Mackenzie on 2015-05-02
> **mörgæs said:**
> Let's begin with the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Per Your Request:

                        > computer     description: Desktop Computer     product: Aspire T135     vendor: Acer     version: R01-B4     serial: [REMOVED]     width: 32 bits     capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp     configuration: boot=normal chassis=desktop
cpus=1 uuid=[REMOVED]   *-core        description: Motherboard        product: K8VM800MAE        vendor: Acer        physical id: 0        version: x.x      *-firmware           description: BIOS           vendor: Award Software International,
Inc.           physical id: 0           version: R01-B4           date: 10/17/2005           size: 128KiB           capacity: 448KiB           capabilities: pci pnp apm upgrade
shadowing cdboot bootselect socketedrom edd int13floppy360
int13floppy1200 int13floppy720 int13floppy2880 int5printscreen
int9keyboard int14serial int17printer int10video acpi usb agp
ls120boot zipboot biosbootspecification      *-cpu           description: CPU           product: AMD Sempron(tm) Processor
3000+           vendor: Advanced Micro Devices [AMD]           physical id: 4           bus info: cpu@0           version: 15.12.2           slot: Socket 754           size: 1800MHz           capacity: 4GHz           width: 64 bits           clock: 200MHz           capabilities: boot fpu fpu_exception
wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat
pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64
3dnowext 3dnow pni lahf_lm vmmcall cpufreq         *-cache:0              description: L1 cache              physical id: 8              slot: Internal Cache              size: 128KiB              capacity: 128KiB              capabilities: synchronous internal
write-back         *-cache:1              description: L2 cache              physical id: 9              slot: External Cache              size: 128KiB              capacity: 128KiB              capabilities: synchronous internal
write-back      *-memory           description: System Memory           physical id: 18           slot: System board or motherboard           size: 2GiB         *-bank:0              description: DIMM 400 MHz (2.5 ns)              physical id: 0              slot: A0              size: 1GiB              width: 64 bits              clock: 400MHz (2.5ns)         *-bank:1              description: DIMM 400 MHz (2.5 ns)              physical id: 1              slot: A1              size: 1GiB              width: 64 bits              clock: 400MHz (2.5ns)      *-pci:0           description: Host bridge           product: K8M800 Host Bridge           vendor: VIA Technologies, Inc.           physical id: 100           bus info: pci@0000:00:00.0           version: 00           width: 32 bits           clock: 66MHz           configuration: driver=agpgart-amd64
latency=8           resources: irq:0
memory:e0000000-e3ffffff         *-pci              description: PCI bridge              product: VT8237/8251 PCI bridge
[K8M890/K8T800/K8T890 South]              vendor: VIA Technologies, Inc.              physical id: 1              bus info: pci@0000:00:01.0              version: 00              width: 32 bits              clock: 66MHz              capabilities: pci pm normal_decode
bus_master cap_list              resources: memory:e8000000-e9ffffff
memory:e4000000-e7ffffff            *-display UNCLAIMED                 description: VGA compatible
controller                 product: K8M800/K8N800/K8N800A
[S3 UniChrome Pro]                 vendor: VIA Technologies, Inc.                 physical id: 0                 bus info: pci@0000:01:00.0                 version: 01                 width: 32 bits                 clock: 66MHz                 capabilities: pm agp agp-3.0
vga_controller bus_master cap_list                 configuration: latency=32
mingnt=2                 resources:
memory:e4000000-e7ffffff memory:e8000000-e8ffffff
memory:e9000000-e900ffff         *-communication UNCLAIMED              description: Modem              product: SM56 Data Fax Modem              vendor: Motorola              physical id: b              bus info: pci@0000:00:0b.0              version: 04              width: 32 bits              clock: 33MHz              capabilities: pm generic cap_list              configuration: latency=32
maxlatency=62 mingnt=1              resources: memory:ea000000-ea000fff
ioport:9000(size=256)         *-ide:0              description: IDE interface              product: VIA VT6420 SATA RAID
Controller              vendor: VIA Technologies, Inc.              physical id: f              bus info: pci@0000:00:0f.0              version: 80              width: 32 bits              clock: 33MHz              capabilities: ide pm bus_master
cap_list              configuration: driver=sata_via
latency=32              resources: irq:20
ioport:9400(size=8) ioport:9800(size=4) ioport:9c00(size=8)
ioport:a000(size=4) ioport:a400(size=16) ioport:a800(size=256)         *-ide:1              description: IDE interface              product:
VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE              vendor: VIA Technologies, Inc.              physical id: f.1              bus info: pci@0000:00:0f.1              version: 06              width: 32 bits              clock: 33MHz              capabilities: ide pm bus_master
cap_list              configuration: driver=pata_via
latency=32              resources: irq:20
ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376
ioport:ac00(size=16)         *-usb:0              description: USB controller              product: VT82xxxxx UHCI USB 1.1
Controller              vendor: VIA Technologies, Inc.              physical id: 10              bus info: pci@0000:00:10.0              version: 81              width: 32 bits              clock: 33MHz              capabilities: pm uhci bus_master
cap_list              configuration: driver=uhci_hcd
latency=32              resources: irq:21
ioport:b000(size=32)         *-usb:1              description: USB controller              product: VT82xxxxx UHCI USB 1.1
Controller              vendor: VIA Technologies, Inc.              physical id: 10.1              bus info: pci@0000:00:10.1              version: 81              width: 32 bits              clock: 33MHz              capabilities: pm uhci bus_master
cap_list              configuration: driver=uhci_hcd
latency=32              resources: irq:21
ioport:b400(size=32)         *-usb:2              description: USB controller              product: VT82xxxxx UHCI USB 1.1
Controller              vendor: VIA Technologies, Inc.              physical id: 10.2              bus info: pci@0000:00:10.2              version: 81              width: 32 bits              clock: 33MHz              capabilities: pm uhci bus_master
cap_list              configuration: driver=uhci_hcd
latency=32              resources: irq:21
ioport:b800(size=32)         *-usb:3              description: USB controller              product: VT82xxxxx UHCI USB 1.1
Controller              vendor: VIA Technologies, Inc.              physical id: 10.3              bus info: pci@0000:00:10.3              version: 81              width: 32 bits              clock: 33MHz              capabilities: pm uhci bus_master
cap_list              configuration: driver=uhci_hcd
latency=32              resources: irq:21
ioport:bc00(size=32)         *-usb:4              description: USB controller              product: USB 2.0              vendor: VIA Technologies, Inc.              physical id: 10.4              bus info: pci@0000:00:10.4              version: 86              width: 32 bits              clock: 33MHz              capabilities: pm ehci bus_master
cap_list              configuration: driver=ehci-pci
latency=32              resources: irq:21
memory:ea001000-ea0010ff         *-isa              description: ISA bridge              product: VT8237 ISA bridge
[KT600/K8T800/K8T890 South]              vendor: VIA Technologies, Inc.              physical id: 11              bus info: pci@0000:00:11.0              version: 00              width: 32 bits              clock: 33MHz              capabilities: isa pm bus_master
cap_list              configuration: latency=0         *-multimedia              description: Multimedia audio
controller              product: VT8233/A/8235/8237 AC97
Audio Controller              vendor: VIA Technologies, Inc.              physical id: 11.5              bus info: pci@0000:00:11.5              version: 60              width: 32 bits              clock: 33MHz              capabilities: pm cap_list              configuration: driver=snd_via82xx
latency=0              resources: irq:22
ioport:c000(size=256)         *-network              description: Ethernet interface              product: RTL-8100/8101L/8139 PCI
Fast Ethernet Adapter              vendor: Realtek Semiconductor Co.,
Ltd.              physical id: 13              bus info: pci@0000:00:13.0              logical name: eth0              version: 10              serial: [REMOVED]              size: 100Mbit/s              capacity: 100Mbit/s              width: 32 bits              clock: 33MHz              capabilities: pm bus_master
cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd
autonegotiation              configuration: autonegotiation=on
broadcast=yes driver=8139too driverversion=0.9.28 duplex=full
ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32
multicast=yes port=MII speed=100Mbit/s              resources: irq:18
ioport:c400(size=256) memory:ea002000-ea0020ff      *-pci:1           description: Host bridge           product: K8M800 Host Bridge           vendor: VIA Technologies, Inc.           physical id: 101           bus info: pci@0000:00:00.1           version: 00           width: 32 bits           clock: 33MHz      *-pci:2           description: Host bridge           product: K8M800 Host Bridge           vendor: VIA Technologies, Inc.           physical id: 102           bus info: pci@0000:00:00.2           version: 00           width: 32 bits           clock: 33MHz      *-pci:3           description: Host bridge           product: K8M800 Host Bridge           vendor: VIA Technologies, Inc.           physical id: 103           bus info: pci@0000:00:00.3           version: 00           width: 32 bits           clock: 33MHz      *-pci:4           description: Host bridge           product: K8M800 Host Bridge           vendor: VIA Technologies, Inc.           physical id: 104           bus info: pci@0000:00:00.4           version: 00           width: 32 bits           clock: 33MHz      *-pci:5           description: Host bridge           product: K8M800 Host Bridge           vendor: VIA Technologies, Inc.           physical id: 105           bus info: pci@0000:00:00.7           version: 00           width: 32 bits           clock: 33MHz      *-pci:6           description: Host bridge           product: K8 [Athlon64/Opteron]
HyperTransport Technology Configuration           vendor: Advanced Micro Devices, Inc.
[AMD]           physical id: 106           bus info: pci@0000:00:18.0           version: 00           width: 32 bits           clock: 33MHz      *-pci:7           description: Host bridge           product: K8 [Athlon64/Opteron] Address
Map           vendor: Advanced Micro Devices, Inc.
[AMD]           physical id: 107           bus info: pci@0000:00:18.1           version: 00           width: 32 bits           clock: 33MHz      *-pci:8           description: Host bridge           product: K8 [Athlon64/Opteron] DRAM
Controller           vendor: Advanced Micro Devices, Inc.
[AMD]           physical id: 108           bus info: pci@0000:00:18.2           version: 00           width: 32 bits           clock: 33MHz      *-pci:9           description: Host bridge           product: K8 [Athlon64/Opteron]
Miscellaneous Control           vendor: Advanced Micro Devices, Inc.
[AMD]           physical id: 109           bus info: pci@0000:00:18.3           version: 00           width: 32 bits           clock: 33MHz           configuration: driver=k8temp           resources: irq:0      *-scsi:0           physical id: 1           logical name: scsi0           capabilities: emulated         *-disk              description: ATA Disk              product: WDC WD800JD-22LS              vendor: Western Digital              physical id: 0.0.0              bus info: scsi@0:0.0.0              logical name: /dev/sda              version: 1D06              serial: [REMOVED]              size: 74GiB (80GB)              capabilities: partitioned
partitioned:dos              configuration: ansiversion=5
sectorsize=512 signature=87d236a8            *-volume:0                 description: Windows NTFS volume                 physical id: 1                 bus info: scsi@0:0.0.0,1                 logical name: /dev/sda1                 version: 3.1                 serial: [REMOVED]                 size: 39GiB                 capacity: 39GiB                 capabilities: primary bootable
ntfs initialized                 configuration: clustersize=4096
created=2015-03-19 17:26:48 filesystem=ntfs label=ACER
modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true
state=dirty upgrade_on_mount=true            *-volume:1                 description: Extended partition                 physical id: 2                 bus info: scsi@0:0.0.0,2                 logical name: /dev/sda2                 size: 35GiB                 capacity: 35GiB                 capabilities: primary extended
partitioned partitioned:extended               *-logicalvolume:0                    description: Linux swap /
Solaris partition                    physical id: 5                    logical name: /dev/sda5                    capacity: 1517MiB                    capabilities: nofs               *-logicalvolume:1                    description: Linux filesystem
partition                    physical id: 6                    logical name: /dev/sda6                    logical name: /                    capacity: 33GiB                    configuration:
mount.fstype=ext4
mount.options=rw,relatime,errors=remount-ro,data=ordered
state=mounted      *-scsi:1           physical id: 2           logical name: scsi3           capabilities: emulated         *-cdrom:0              description: SCSI CD-ROM              product: CD-ROM LTN-5291S              vendor: LITE-ON              physical id: 0.0.0              bus info: scsi@3:0.0.0              logical name: /dev/cdrom              logical name: /dev/sr0              version: NRS2              capabilities: removable audio              configuration: ansiversion=5
status=nodisc         *-cdrom:1              description: DVD writer              product: DVD+-RW ND-3530A              vendor: _NEC              physical id: 0.1.0              bus info: scsi@3:0.1.0              logical name: /dev/sr1              version: 103C              serial: [REMOVED]              capabilities: removable audio cd-r
cd-rw dvd dvd-r              configuration: ansiversion=5
status=nodisc      *-scsi:2           physical id: 3           bus info: usb@4:1           logical name: scsi4           capabilities: emulated scsi-host           configuration: driver=usb-storage         *-disk:0              description: SCSI Disk              physical id: 0.0.0              bus info: scsi@4:0.0.0              logical name: /dev/sdb              configuration: sectorsize=512         *-disk:1              description: SCSI Disk              physical id: 0.0.1              bus info: scsi@4:0.0.1              logical name: /dev/sdc              configuration: sectorsize=512         *-disk:2              description: SCSI Disk              physical id: 0.0.2              bus info: scsi@4:0.0.2              logical name: /dev/sdd              configuration: sectorsize=512         *-disk:3              description: SCSI Disk              physical id: 0.0.3              bus info: scsi@4:0.0.3              logical name: /dev/sde              configuration: sectorsize=512

---

### Post by quixotic-cynic on 2015-05-02
Hopefully mörgæs can deal with the output of sudo lshw -sanitize > lshw.txt

In the meantime you might want to run the terminal application "top" to see what processes are occupying your CPU.

One of the lightest desktop environments on Ubuntu is LXDE/Lubuntu. You can install Lubuntu with ```
sudo apt-get install lubuntu-desktop
``` You can then run Lubuntu from your login screen by clicking the circle (with the Ubuntu logo in it) and choosing the appropriate option.

---

### Post by mörgæs on 2015-05-03
It would be easier to deal with the output if it were enclosed in CODE tags. John, please edit the post (and go for the advanced options).

Nevertheless we found out that this is old stuff so I agree on the Lubuntu recommendation. See the link in my signature for more info.

---

### Post by John_Mackenzie on 2015-05-03
Sorry, morgaes, copy/paste somehow lost tabs/indents.   Here is lshw file again.

```
computer
    description: Desktop Computer
    product: Aspire T135
    vendor: Acer
    version: R01-B4
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: K8VM800MAE
       vendor: Acer
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: R01-B4
          date: 10/17/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 754
          size: 1800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM 400 MHz (2.5 ns)
             physical id: 1
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:e8000000-e9ffffff memory:e4000000-e7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:e4000000-e7ffffff memory:e8000000-e8ffffff memory:e9000000-e900ffff
        *-communication UNCLAIMED
             description: Modem
             product: SM56 Data Fax Modem
             vendor: Motorola
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=32 maxlatency=62 mingnt=1
             resources: memory:ea000000-ea000fff ioport:9000(size=256)
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:20 ioport:9400(size=8) ioport:9800(size=4) ioport:9c00(size=8) ioport:a000(size=4) ioport:a400(size=16) ioport:a800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ac00(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:b000(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:b400(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:b800(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:bc00(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:ea001000-ea0010ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:c000(size=256)
        *-network
             description: Ethernet interface
             product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:18 ioport:c400(size=256) memory:ea002000-ea0020ff
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JD-22LS
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1D06
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=87d236a8
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 39GiB
                capacity: 39GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-03-19 17:26:48 filesystem=ntfs label=ACER modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 35GiB
                capacity: 35GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1517MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 33GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom:0
             description: SCSI CD-ROM
             product: CD-ROM LTN-5291S
             vendor: LITE-ON
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: NRS2
             capabilities: removable audio
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: DVD writer
             product: DVD+-RW ND-3530A
             vendor: _NEC
             physical id: 0.1.0
             bus info: scsi@3:0.1.0
             logical name: /dev/sr1
             version: 103C
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@4:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
```

---

### Post by John_Mackenzie on 2015-05-03
I will try other lighter versions of software.  

My main goal is to run LinuxCNC - an apt for controlling motor movements of a 4-axis milling machine via parallel port connection to other motor drive electronics.  But the screen is used to display machine movements - and monitor the milling process.  I cannot tolerate screen time delays to apply this apt.  

With Ub 14.04 installed, even in Terminal, I experience 2 sec delays in registering keystrokes and actually seeing the strokes on screen.  Sudo commands in Terminal request password - which I furnish - and the command is executed before any password key strokes are ever displayed.  I suppose that the CPU is processing my keystrokes fairly rapidly, but that the video is maxed out trying to follow.  

Do you think I will be able to remedy the problem with Lubuntu?

---

### Post by Vladlenin5000 on 2015-05-04
I'm afraid your biggest problem is the "S3 UniChrome Pro". This has always been "bad" even in Windows with proprietary drivers, even when this was current hardware.
I've tested it many times (different machines) and if there's a reliable way to make it work acceptably with any Ubuntu newer than 12.04 I haven't found it yet.

Lubuntu - or any other flavor with a _DE that doesn't require 3D acceleration_ - should give better results, obviously, but don't expect miracles. That graphics chip is horrible, to say the least.

---

### Post by John_Mackenzie on 2015-05-05
Installed Lubuntu, and system works satisfactorily.  

Looks like to run the full-blown Ubun 14.04, better hardware, esp video, is required.  

Thx everyone for your advice & comment.

---

### Post by mastablasta on 2015-05-05
if this is laptop you are out of luck, if this is a desktop you can maybe get some used GPU.

Another option is Xubuntu (also uses 2D to draw the desktop). there are also many windows managers available such as icewm. windows managers are not as integrated as desktop but they work fine and much faster on lower GPU. there are some Linux distros designed specifically for old hardware (antix, ToriOS, Slitaz...). they look more simple but get the job done.

---

