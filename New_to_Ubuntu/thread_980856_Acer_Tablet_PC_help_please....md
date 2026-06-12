---
title: "Acer Tablet PC help please..."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by rhinchman on 2008-11-13
I have just installed Ubuntu on my old tablet pc - Acer Travelmate C303XMi

I am having trouble getting the hardware to work properly, specifically the touchscreen doesn't work, bluetooth doesn't work, the buttons on the screen and above the keyboard, etc...  this is what I've found so far.  

Can someone please help walk me through fixing these problems?

Thank you:confused:

---

### Post by mapes12 on 2008-11-13
What version of Ubu have you installed?

Did you use Live or alternate CD? If the Live CD did you run the CD Live session first, before installing, and if so did the problems you mention occur then?

Please could you post the output to:

```
sudo lshw
```

---

### Post by Sirchristopher on 2008-11-13
Rhinchman...To get the info asked open the terminal and type the code requested.  I know you just installed ubuntu today.  You are using version 8.10, correct?

---

### Post by rhinchman on 2008-11-14
I installed 8.1 yesterday and I used the downloadable .iso file for installation - clean install after format - 

Not sure what you mean by post code - I really am an absolute beginner at this

Thanks

---

### Post by rhinchman on 2008-11-14
type the code from the previous post?

---

### Post by rhinchman on 2008-11-14
Here is what happened when I entered the code...

richard-laptop            
    description: Computer
    product: TravelMate C300
    vendor: Acer
    version: -1
    serial: LXT280E12242800804M000
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=A045BC40-D121-11D8-86C0-D87B4D8E4EF0
  *-core
       description: Motherboard
       product: TravelMate C300
       vendor: Acer
       physical id: 0
       version: Rev.A
       serial: LXT280E12242800804M000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.07 (05/06/04)
          size: 111KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: U1
          size: 1700MHz
          capacity: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-system:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-system:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-pcmcia:0
                description: CardBus bridge
                product: OZ711EC1 SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
              *-storage
                   physical id: 0
                   version: Memory Card Adapter
                   slot: Socket 0
                   resources: irq:3
           *-pcmcia:1
                description: CardBus bridge
                product: OZ711EC1 SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
              *-pccard UNCLAIMED
                   description: SmartCardBus Reader
                   vendor: O2Micro
                   physical id: 0
                   version: V1.0
                   slot: Socket 1
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5705M Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 03
                serial: 00:0a:e4:0b:b8:26
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.07 ip=192.168.15.2 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 6
                bus info: pci@0000:02:06.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:2d:83:0e
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD800VE-75HD
                vendor: Western Digital
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXEX05659571
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a009a009
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 47c7b6bd-ea9d-49b8-9d63-e1ac47171ce4
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-13 20:31:18 filesystem=ext3 modified=2008-11-13 22:35:06 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-13 22:35:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 2925MiB
                   capacity: 2925MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2925MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD-RW DVR-K13RA
                vendor: PIONEER
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-scsi:0
          physical id: 1
          bus info: usb@1:1
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
             size: 279GiB (300GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=38ae9900
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Maxtor One Touch
                version: 3.1
                serial: 8e54ab9f-32a7-444f-a286-a77025c0c275
                size: 279GiB
                capacity: 279GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=512 created=2007-07-24 20:21:12 filesystem=ntfs label=Maxtor One Touch mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Memory Card Adap
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             version: 2001
             serial: 000000000000
             size: 1938MiB (2032MB)
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 1938MiB (2032MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/disk
                   version: FAT16
                   serial: 3834-3635
                   size: 1937MiB
                   capacity: 1937MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:31:e7:1b:d0:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Hope this is helpful

Thanks

-R

---

### Post by mapes12 on 2008-11-14
Quite a number of your devices are not recognised correctly i.e. UNCLAIMED

> *-system:0 UNCLAIMED
description: System peripheral
product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
vendor: Intel Corporation
physical id: 0.1
bus info: pci@0000:00:00.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: latency=0

*-system:1 UNCLAIMED
description: System peripheral
product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
vendor: Intel Corporation
physical id: 0.3
bus info: pci@0000:00:00.3
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: latency=0

*-display:0 UNCLAIMED
description: VGA compatible controller
product: 82852/855GM Integrated Graphics Device
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0

*-display:1 UNCLAIMED
description: Display controller
product: 82852/855GM Integrated Graphics Device
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0

*-pccard UNCLAIMED
description: SmartCardBus Reader
vendor: O2Micro
physical id: 0
version: V1.0
slot: Socket 1

*-serial UNCLAIMED
description: SMBus
product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 03
width: 32 bits
clock: 33MHz
configuration: latency=0

*-communication UNCLAIMED
description: Modem
product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
vendor: Intel Corporation
physical id: 1f.6
bus info: pci@0000:00:1f.6
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0

You may want to check the Hardware Compatibility Lists for your machine: [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

If you are using a Live CD did you manage to run an Ubuntu session from the live CD i.e. without installing it to you HDD?

---

### Post by rhinchman on 2008-11-15
Yes - I was able to run it from the CD without problems - I incorrectly assumed that everything would start working properly once I did the full install.

So...what do I do here?

---

### Post by mapes12 on 2008-11-15
Ubuntu needs to be re installed but go for 8.04 LTS, not 8.10 as the latter is still somewhat buggy. Before proceeding post the output to this so that we can set up your partitions ahead of the install. ```
sudo fdisk -l
```

---

### Post by rhinchman on 2008-11-16
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa009a009

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ae9900

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36482   293041633+   7  HPFS/NTFS

Disk /dev/sdc: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         984     1983619+   6  FAT16

---

### Post by rhinchman on 2008-11-16
By the way - ignore the 300 GB drive above - it's an external.  Don't really need to partition the primary drive - there's nothing other than the operating system on it anyway.

---

### Post by rhinchman on 2008-11-18
Ubuntu 8.04 LTS ready - awaiting further instructions please

---

### Post by Sirchristopher on 2008-11-21
I see a calibrate touchscreen app in the add/remove feature in the Applications menu.  Have you tried that?

---

### Post by rhinchman on 2008-11-22
Did you actually think it could be that simple?  Try again...I'm stumped

---

