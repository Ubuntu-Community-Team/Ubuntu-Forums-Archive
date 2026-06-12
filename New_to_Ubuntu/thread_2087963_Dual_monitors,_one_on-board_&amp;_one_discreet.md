---
title: "Dual monitors, one on-board &amp; one discreet"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by sffvba[e0rt on 2012-11-25
Hi,

I would like some assistance setting up (or attempting to set up) a dual monitor configuration using one screen plugged into my ATI Radeon HD 6850 and the other into the motherboard on-board graphics.  I am using Ubuntu 12.04.

lshw:

```
circle
    description: Desktop Computer
    product: ()
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop uuid=32A2DE52-D63C-11E0-BAFE-00E04CB16295
  *-core
       description: Motherboard
       product: DH67CL
       vendor: Intel Corporation
       physical id: 0
       version: AAG10212-208
       serial: BTCL136000FH
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: BLH6710H.86A.0119.2011.0523.1030
          date: 05/23/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal unified
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: DIMM3
             width: 64 bits
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: JM1333KLN-4G
             vendor: Transcend
             physical id: 1
             serial: 0009461A
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber2
             vendor: A1_Manufacturer2
             physical id: 2
             serial: A1_SerNum2
             slot: DIMM4
             width: 64 bits
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 9DSEBNZB-TATP
             vendor: Undefined
             physical id: 3
             serial: BBD41209
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fe500000-fe5fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Barts PRO [ATI Radeon HD 6800 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:57 memory:e0000000-efffffff memory:fe520000-fe53ffff ioport:e000(size=256) memory:fe500000-fe51ffff
           *-multimedia
                description: Audio device
                product: Barts HDMI Audio [Radeon HD 6800 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:54 memory:fe540000-fe543fff
        *-display
             description: Display controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:56 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:55 memory:fe629000-fe62900f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: 38:60:77:3f:6e:8f
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-4 ip=192.168.1.135 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:52 memory:fe600000-fe61ffff memory:fe628000-fe628fff ioport:f080(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fe627000-fe6273ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:53 memory:fe620000-fe623fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm normal_decode bus_master cap_list
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:fe400000-fe4fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:fe400000-fe401fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe626000-fe6263ff
        *-isa
             description: ISA bridge
             product: H67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:fe625000-fe6257ff
           *-disk:0
                description: ATA Disk
                product: ST500DM002-1BC14
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JC4B
                serial: Z2AKB909
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000706ae
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: 0b2954a5-11c5-48d2-aeb5-7c2a5035efa5
                   size: 7628MiB
                   capacity: 7628MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 656f58bf-23f4-44b3-a94e-cb612673e86f
                   size: 46GiB
                   capacity: 46GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-11-12 21:57:11 filesystem=ext4 lastmountpoint=/ modified=2012-11-12 22:08:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-11-25 12:43:03 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 411GiB
                   capacity: 411GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 411GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH24NS90
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: IN00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: WDC WD3200AAJS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAT12469674
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a8a8a8a8
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /nlsthzn
                   version: 1.0
                   serial: ad8db2ef-479d-4808-a605-8e4bd8da37d9
                   size: 298GiB
                   capacity: 298GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-11-12 21:57:13 filesystem=ext4 modified=2012-11-25 12:43:05 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-11-25 12:43:05 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe624000-fe6240ff ioport:f040(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:1.4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart Plus
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdc
```

The interesting thing is, the monitor attached to the on-board shows some activity when booting, I see the Ubuntu boot/shut-down screens but once I am in Ubuntu it just goes blank.  There isn't any error on the screen about checking the cable etc. but it remains black.

It also doesn't show up under "Displays" and obviously nothing in the Catalyst Control Centre about it.

*edit: When I switch to a TTY my display connected to the on-board becomes active and the other one goes blank.  Switching back to TTY-7 they reverse again :/*

xorg.conf:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I see there is nothing about Intel in this file...



Cheers
404

---

### Post by dannyboy79 on 2012-12-03
you can't have two different cards active at the same time.

---

### Post by sffvba[e0rt on 2013-01-11
> **dannyboy79 said:**
> you can't have two different cards active at the same time.

I am trying this again because it works very well in Windows :/

**BUMP!**



404

---

### Post by audiomick on 2013-01-11
> **dannyboy79 said:**
> you can't have two different cards active at the same time.

I don't know how to help you, not found, sorry, but I also don't believe that dannyboy is right about this. I can recall seeing a video a while back about some monster compiz setup using 6 monitors, and, if I recall rightly, it was using 3 dual head cards.

If xrandr can't deal with it, you might need to look into creating an xorg.config file. I think it would involve defining a device for each card, but beyond that I would have to start delving into the documentation.

---

### Post by dannyboy79 on 2013-01-11
i didn't think it was possible but this thread may shead some light.
[http://ubuntuforums.org/showthread.php?t=53966](http://ubuntuforums.org/showthread.php?t=53966)

---

### Post by sffvba[e0rt on 2013-01-11
Thanks for the link :)

I just tried Ubuntu 12.10 and before installing the proprietary ATI drivers I could see two monitors when selecting display (the second was disabled and when I tried to enable it the system froze) so at least some progress of sorts.

Then installed the ATI drivers and then the system would only work on the Intel display but when I logged in Unity would crash (seems the Intel can't handle the fallback mode for Unity 3D or something) and the ATI display wasn't working well, sometimes resolution being out of range other times just being purple :/

I have had a quick look at the thread you linked, not sure how relevant anymore as the info has become severely dated but it does offer proof of a possibility :)


404

---

### Post by audiomick on 2013-01-11
> **not found said:**
> ... not sure how relevant anymore as the info has become severely dated ...

This is true in as much as Ubuntu now uses xrandr or whatever, but as far as I know, if an xorg.config is present, it will still be used. the nvidia driver still creates one, for instance. Or at least it did the last time I installed one, which is not that long ago. I also don't think the format and structure of xorg.config has been changed to any great extent. I believe the method described should still work in principle.

---

