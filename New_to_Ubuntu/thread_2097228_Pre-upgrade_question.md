---
title: "Pre-upgrade question"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Roger49 on 2012-12-22
Hi,
I am looking to upgrade from 10.04 to 12.04.1 soon. I am running a pentium 4  HT with 512 MB of RAM. I am intending to add 2 gigabytes of RAM.
I have tried 2 separate 12.04 live cd's, and am experiencing problems with the display. Checkerboard style strips appear in the background, and the labels which pop up from the icons on the left-hand side of the screen quickly become unreadable - the white parts being overwritten with black pixels?
I have tried Xubuntu - no problems at all, and have successfully installed it on my laptop, but would like the "full-fat" version on my desktop so that Libre Office, etc., would be there from the start. 
My machine is a HP Compaq dc5100, with integrated Intel graphics.
Regards to everybody, and a Merry Christmas.
Roger49

---

### Post by audiomick on 2012-12-22
If you do put the machine up to 2GB of RAM, I think you should be able to get things going, albeit perhaps a little slow. I don't know what might be causing your problems with the live CD, but I daresay they are not insurmountable.

I suggest you do
```
sudo lshw
```
in a terminal and post the output here, so that people can see exactly what is in the machine. Maybe someone knows of a specific problem and solution.

---

### Post by Roger49 on 2012-12-24
Hi,
Here is the result from ```
sudo lshw
``````
roger-desktop             
    description: Mini Tower Computer
    product: HP Compaq dc5100 MT(EC955ET)
    vendor: Hewlett-Packard
    serial: CZC6032PRT
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=1 uuid=A44A10F8-E27F-DA11-BBDA-FE2D055D000F
  *-core
       description: Motherboard
       product: 09E0h
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC6032PRT
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786C2 v01.07 (08/25/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 2800MHz
          capacity: 2800MHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
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
     *-memory:0
          description: System Memory
          physical id: 33
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: M3 78T3354CZ3-CD5
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: C4530171
             slot: XMM1
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 1
             slot: XMM2
        *-bank:2
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: M3 78T3354CZ3-CD5
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 2
             serial: AE530171
             slot: XMM3
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 3
             slot: XMM4
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 34
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfd00000-cfd7ffff ioport:1800(size=8) memory:e0000000-efffffff(prefetchable) memory:cfd80000-cfdbffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:20000000-201fffff memory:20200000-203fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f0200000-f04fffff memory:20400000-205fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth0
                version: 01
                serial: 00:0f:fe:2d:05:5d
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
                resources: irq:17 memory:f0400000-f040ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1440(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1460(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1480(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:14a0(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:cfdc0000-cfdc03ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:21 ioport:1000(size=256) ioport:1400(size=64) memory:cfdc0400-cfdc05ff memory:cfdc0600-cfdc06ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:14e0(size=16)
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4482B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.05
                serial: [HL-DT-STRW/DVD GCC-4482B1.05H.L.D.S.2005/07/20
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1818(size=8) ioport:1830(size=4) ioport:1820(size=8) ioport:1834(size=4) ioport:14f0(size=16)
           *-disk:0
                description: ATA Disk
                product: Maxtor 6V080E0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: VA11
                serial: V20P3ZEG
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9c879c87
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 38df93b0-e71f-d748-a48e-8c7eae8d0737
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2001-02-26 16:38:39 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD2500JS-55N
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 10.0
                serial: WD-WCANKM130288
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00068b02
              *-volume:0
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /boot
                   version: 1.0
                   serial: d0da9c13-b2f6-45c6-879f-19ec97422498
                   size: 476MiB
                   capacity: 476MiB
                   capabilities: primary ext2 initialized
                   configuration: filesystem=ext2 modified=2012-12-24 14:46:05 mount.fstype=ext2 mount.options=rw,relatime,errors=continue mounted=2012-12-24 14:45:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 75GiB
                   capacity: 75GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1906MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      logical name: /
                      capacity: 7628MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sdb7
                      logical name: /home
                      capacity: 66GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
     *-scsi:0
          physical id: 3
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000e0748
           *-volume:0
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/New Volume
                version: FAT32
                serial: b90f-39a6
                size: 74GiB
                capacity: 74GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=New Volume mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdc2
                version: 1
                serial: 68dc41c4-be9c-4ef4-8402-fa501f3f70e6
                size: 3814MiB
                capacity: 3814MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sdc3
                logical name: /media/Documents
                version: FAT32
                serial: d3ba-1467
                size: 78GiB
                capacity: 78GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=Documents mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 4
          bus info: usb@1:4
          logical name: scsi7
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@7:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /media/3Connect
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/3Connect
                capabilities: partitioned partitioned:mac
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 17KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   vendor: Mac OS X
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000001000
                   size: 25MiB
                   capacity: 25MiB
                   capabilities: hfsplus initialized
                   configuration: checked=1904-01-01 00:00:00 created=2010-03-02 14:15:55 filesystem=hfsplus lastmountedby=10.0 modified=2010-03-02 14:15:55 state=clean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@8:0.0.0
             logical name: /dev/sdd
roger@roger-desktop:~$ 


```It would be good to get some feedback on this, to find out whether it might be new box time, or time to try Lubuntu.
Regards,
Roger.

---

### Post by squakie on 2012-12-24
I would try the following boot options:

i915.modeset=1

If that doesn't help, change it to:

i915.modeset

If you don't know how to do that, post back.

If neither help, post back.

Also, I hope your plan has been to back up anything you need, then do a fresh install.  Upgrading, as used in Ubuntu terms, would not be your best option - you could end up with old libs, etc., that weren't removed.  Instead, back everything up that you need and do a complete new install.

---

### Post by audiomick on 2012-12-24
> **Roger49 said:**
> ...It would be good to get some feedback on this, to find out whether it might be new box time, or time to try Lubuntu.
Regards,
Roger.

I reckon that should run ok with the current version or 12.04. I tried 12.04 on from a USB stick on a machine with a slower processor than that, and it went ok. I think the RAM update should be a priority, though.

---

### Post by Roger49 on 2012-12-31
Evening all,
I'm posting this from the laptop.
The memory upgrade went well, and I've installed 12.04.1 LTS, but don't seem to be able to get it to recognise my mobile broadband dongle.
I replaced it with  Xubuntu, as I've got on this laptop, but with no success.
In the Unity desktop, the dongle can be found in the "Computer" section, but is shown as Storage. "lsusb" however, names it correctly.
I have set it up in ?Network Manager, exactly as I had it in Lucid, but despite repeated reboots, and taking-out and putting-in of the dongle, I never have the option of enabling Mobile Broadband.
Any suggestions before I start throwing money at the problem?
Regards,
Roger

---

### Post by Roger49 on 2013-01-06
Hi all,
Sorry to see no replies. Still no success with Ubuntu on desk-top machine. Xubuntu allows mobile broadband every 2-3 reboots.
Posting this from a live cd of Debian. No problems at all.
TTFN,
Roger.

---

### Post by audiomick on 2013-01-06
Hi Roger.

I think you might get a better response if you start a new thread with an appropriate title about the USB dongle. People here tend to gravitate to particular themes, so a title with "USB dongle" in it is likely to attract someone with a bit of knowledge.

I saw a post or two recently that sounded similar, but I can't remember which thread or how long ago exactly. It seems the device was not being recognised properly as a modem. The solution in that case was to edit particular file. Sorry I can't be more help. I would be confident about being able to get it working, though. I can't recall many if any at all threads on the subject where the OP went away empty handed.

Anyway, start a dedicated thread, and maybe put a link to it in here to keep the discussion concentrated in one spot...

---

### Post by offgridguy on 2013-01-06
> **Roger49 said:**
> Hi all,
Sorry to see no replies. Still no success with Ubuntu on desk-top machine. Xubuntu allows mobile broadband every 2-3 reboots.
Posting this from a live cd of Debian. No problems at all.
TTFN,
Roger.
I haven't noticed anywhere if you have actually added more RAM yet ?
  Which i agree would be a priority.

---

### Post by audiomick on 2013-01-06
> **offgridguy said:**
> I haven't noticed anywhere if you have actually added more RAM yet ?

> **Roger49 said:**
> Evening all,
I'm posting this from the laptop.
The memory upgrade went well,


:-\"

---

### Post by Roger49 on 2013-01-14
Hello all,
I've installed Debian for the time being.
I'm back with the 2.6x series of kernel, and Gnome 2.3, and everything is OK.
Regards,
Roger.

---

### Post by Roger49 on 2013-05-06
Marking this as solved.
Have done more research and will start a new thread.
(Sorry, can't find "Solved" button)

---

