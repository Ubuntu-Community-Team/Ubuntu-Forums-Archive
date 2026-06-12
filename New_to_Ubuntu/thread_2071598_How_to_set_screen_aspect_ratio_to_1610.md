---
title: "How to set screen aspect ratio to 16:10?"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Gussn on 2012-10-15
Hello, I have a LG Flatron L177WS. 

I am having blurred image.

There is a site that diagnosed my problem: my screen aspect ratio is currently 16:9 and my monitor would work better with 16:10. 

The site that diagnosed it is [http://www.lagom.nl/lcd-test/display_settings.php](http://www.lagom.nl/lcd-test/display_settings.php)

And here's what it says:

```
Resolution: **1280x720**   (720p 16:9)
Description: HDTV format, not common for computer monitors. (as of 2007)
Note: your screen is too small to display the images without rescaling. (at least 1024x768 recommended)
Note:  your resolution does not have a common 5:4 (1.25), 4:3 (1.33), or 16:10  (1.6) aspect ratio, which means that images can be distorted. Your  aspect ratio is: 1.78.
Color depth: 24 bits (Truecolor, Millions of colors)[/QUOTE]I believe my screen will display correctly if I manage to set the aspect ratio to 16:10. But I can't find this option in the "system settings -> display" section. And my monitor does not have to option to manually force the aspect ratio to 16:10.

Is there any way to fix it?

By the way here's my system's info:

 [QUOTE]description: Desktop Computer
    product: GN545AA-AC4 a6230br (GN545AA#AC4)
    vendor: HP-Pavilion
    serial: BRG733016Y
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=103C_53316J sku=GN545AA#AC4 uuid=2C385C49-70A3-DB11-8710-1BD5617EA5B5
  *-core
       description: Motherboard
       product: Lucknow
       vendor: Foxconn
       physical id: 0
       version: 1.0
       serial: P82110BEPUV3
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: v5.08
          date: 07/06/2007
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back instruction
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
          physical id: e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 1331 MHz (0.8 ns)
             product: M3 78T2953CZ3-CD5
             vendor: Samsung
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1331MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: ht cpufreq
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
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:ffa80000-ffafffff ioport:ec00(size=8) memory:d0000000-dfffffff memory:ffa40000-ffa7ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:41 memory:ffa3c000-ffa3ffff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:40200000-403fffff ioport:40400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:b000(size=4096) memory:ff700000-ff7fffff ioport:40000000(size=2097152)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:78:d4:71:95
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:40 ioport:b800(size=256) memory:ff7ff000-ff7fffff memory:ff7c0000-ff7dffff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e000(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:dc00(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d880(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa3bc00-ffa3bfff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:ff800000-ff8fffff
           *-communication UNCLAIMED
                description: Modem
                product: SM56 Data Fax Modem
                vendor: Motorola
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic cap_list
                configuration: latency=64 maxlatency=62 mingnt=1
                resources: memory:ff8ff000-ff8fffff ioport:c800(size=256)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:e880(size=8) ioport:e800(size=4) ioport:e480(size=8) ioport:e400(size=4) ioport:e080(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD3200AAJS-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 12.0
                serial: WD-WCAPZ0751631
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1549f232
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ffe9fa2c-a1ec-4b33-bab0-c1e3f35dd153
                   size: 223GiB
                   capacity: 223GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-10-14 21:52:20 filesystem=ext4 lastmountpoint=/ modified=2012-10-14 22:08:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-10-15 21:05:27 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: da1b99b8-5f56-5b42-a03b-0099b631902c
                   size: 6544MiB
                   capacity: 6565MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-06-19 12:10:07 filesystem=ntfs label=FACTORY_IMAGE state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 67GiB
                   capacity: 67GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 49GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 18GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-H653L
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 0514
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
```

---

### Post by shreepads on 2012-10-16
Which OS & version are you using? Are you using the integrated Intel graphics with the default drivers? (Can't see a dedicated graphics card mentioned above)

How is the monitor plugged into the system, DVI/ DVI-D cable or VGA? Or something else?

Please paste output from xrandr

---

### Post by mips on 2012-10-16
> **Gussn said:**
> Hello, I have a LG Flatron L177WS. 

I am having blurred image.

There is a site that diagnosed my problem: my screen aspect ratio is currently 16:9 and my monitor would work better with 16:10. 

The site that diagnosed it is [http://www.lagom.nl/lcd-test/display_settings.php](http://www.lagom.nl/lcd-test/display_settings.php)

And here's what it says:

I believe my screen will display correctly if I manage to set the aspect ratio to 16:10. But I can't find this option in the "system settings -> display" section. And my monitor does not have to option to manually force the aspect ratio to 16:10.


Don't believe everything you read on the net, **that site is WRONG!**

The [LG L177WS]("https://docs.google.com/viewer?a=v&q=cache:UB3ojg2PDNoJ:www.lg.com/lgecs.downloadFile.ldwf%3FDOC_ID%3DKROWM000161050%26ORIGINAL_NAME_b1_a1%3DL177WS-ENG.PDF%26FILE_NAME%3DKROWM000161050.pdf%26TC%3DDwnCmd+&hl=en&gl=za&pid=bl&srcid=ADGEESgCeEWqE8fFqp0W3tEEVytJUozMPTiGUcPBx8z99XZydrYBOJUHhzM-ZO8Qbl3n7pIXdha7XdbZyOaLK0JWvJlzexEO1KxFDyrzFXsFP-hWe91wNeAYVv_RJNcj0TXT343QIWCY&sig=AHIEtbTUSQcLaIzmX3BCn_FVN39Eok6Ldg") has a LCD panel with a native resolution of 1280x720 which makes it a [16:9 aspect ratio]("http://en.wikipedia.org/wiki/Display_resolution#Computer_monitors") display.

So make sure Ubuntu is set to 1280x720 resolution and all should be good. If you still have issues consult the monitor manual I linked to and double check the monitor config from it's onboard menu as you might have features like stretching or somehting like that enabled. If you still have issues then look at your font anti-aliasing & dpi settings on Ubuntu.

---

### Post by Gussn on 2012-10-16
Thanks for your help folks. But it happens I've already tried all that and the issue persists. So I exchanged the LG for a bigger Samsung display and everything is fine now.

---

