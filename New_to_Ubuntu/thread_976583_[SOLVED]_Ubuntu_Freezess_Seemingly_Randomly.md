---
title: "[SOLVED] Ubuntu Freezess Seemingly Randomly"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by EPrips on 2008-11-09
So I've just started using Ubuntu and I like it so far. The only issue is that it seems to freeze if I use it continually. I can't determine what causes the freeze, since there doesn't seem to be one particular thing that causes the freeze. From now on I'll keep track of what I was doing when the freeze occured, but does anyone have any preliminary ideas?

---

### Post by Ryadt on 2008-11-09
Just check the output of ```
top
``` to see which process causes the freeze. Try to post the output when it happens.

---

### Post by MasterSander on 2008-11-09
does it totally freeze or are you able to switch to terminal (ctrl+alt+f1) ? Anyway my ubuntu froze sometimes when I tried to playing a video with VLC, I had to switch to openGL output

---

### Post by EPrips on 2008-11-09
I've never tried switching to terminal. So next time it freezes try to go to terminal and then get the output of top?

---

### Post by Ryadt on 2008-11-09
You don't need to exit gui. You can have the terminal open during the session with 'top' running.
Try to see what process is causing the issue from the 'top' output and try to post it here.

---

### Post by mapes12 on 2008-11-09
Can we have a look at your configuration please? In Terminal: ```
sudo lshw
```

and post the output here.

---

### Post by nhasian on 2008-11-09
I enabled the linux-backports-modules-intrepid and no more lockups.

in a terminal type

```
sudo apt-get install linux-backports-modules-intrepid
```

> System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 

---

### Post by EPrips on 2008-11-09
Well it fronze again and I was unable to load up terminal. Here is the output of sudo lshw:

    description: Notebook
    product: HP Pavilion dv6700 Notebook PC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF8244CPS
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4638-3234-3443-5053-001E6884EAA2
  *-core
       description: Motherboard
       product: 30D2
       vendor: Quanta
       physical id: 0
       version: 79.2E
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.57 (05/21/2008)
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: U2E1
          size: 2501MHz
          capacity: 2501MHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida cpufreq
          configuration: id=0
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
             size: 6MiB
             capacity: 6MiB
             capabilities: burst external write-back
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
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 2501MHz
          capacity: 2501MHz
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
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8400M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 61
                serial: 00:1f:3b:c5:50:7b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=128.237.254.0 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 01
                serial: 00:1e:68:84:ea:a2
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:09:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:09:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:09:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=32 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:09:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 9.4
                bus info: pci@0000:09:09.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
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
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T20N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WC05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2250B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8909
                serial: K617T852BKDH
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3c7ad93e
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a4df86fe-1b6b-f04d-86af-a5acc4839a2c
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-07-06 17:42:31 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: da1b99b8-5f56-5b42-a03b-0099b631902c
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-06-19 11:10:07 filesystem=ntfs label=HP_RECOVERY state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 68GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3027MiB
                      capabilities: nofs
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
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:29:d3:18:4f:83
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
eric@eric-laptop:~$

---

### Post by EPrips on 2008-11-09
Just froze again. I just left it idle in Firefox and eventually it froze. I didn't have top open, however now I'm just gonna leave it open. The top entry seems to be alternating between xorg and firefox.

---

### Post by EPrips on 2008-11-09
I've avoided leaving my PC idle with Firefox open, and instead have left it idle with Firefox minimized, and have yet to have a freeze. Perhaps the freezing has something to do with Firefox being left open?

---

### Post by EPrips on 2008-11-09
Bump

---

### Post by EPrips on 2008-11-09
Haven't frozen up in a while, although I've been trying to avoid leaving firefox open while I'm not using my PC.

---

### Post by nhasian on 2008-11-10
Enable the linux-backports-modules-intrepid and you will have no more lockups.

in a terminal type

```
sudo apt-get install linux-backports-modules-intrepid
```

> System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 

---

### Post by EPrips on 2008-11-10
> **nhasian said:**
> Enable the linux-backports-modules-intrepid and you will have no more lockups.

in a terminal type

```
sudo apt-get install linux-backports-modules-intrepid
```

I enabled them the first time you posted, and have since had only one freeze. So either they are working or I've just avoided what I believe to be the cause of the freezing (leaving firefox open while not using my pc).

---

