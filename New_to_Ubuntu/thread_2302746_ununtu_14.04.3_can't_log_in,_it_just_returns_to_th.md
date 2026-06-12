---
title: "ununtu 14.04.3 can't log in, it just returns to the log in screen"
date: 2015-11-12
forum: New to Ubuntu
---

### Post by kenb2 on 2015-11-12
I have installed ubuntu 14.04.3 on and old MDG computer from CD Disk Image.  It all seems to boot up fine from the hard drive, but when I reach the user login screen, I log in, the machine starts the log in, then the screen goes dark, and returns me right back to the log in screen.  I have tried 3 attempts at re-installing the software with the same result.

If I run the program from the CD it works just fine, but of course it is very slow.  Can some one help with this?

---

### Post by mörgæs on 2015-11-13
Hi, welcome to the fora.

You don't post the hardware specifications but since you call the computer old my first suggestion is a fresh install of Lubuntu 15.10.

---

### Post by grahammechanical on 2015-11-13
The Ubuntu live session uses an open source video driver. When we install Ubuntu and tick the box Install third party software we get a proprietary video driver. So, when the live session works fine and the installed session does not work as it should, I start thinking "proprietary video driver."

At the Grub boot menu we can select Advanced Options for Ubuntu and then select recovery mode. At the recovery menu we can then select Resume. That should get us to a working desktop without using the proprietary video driver. At a desktop we can go to System Settings>Software & Updates>Additional Drivers tab and if we are connected to the internet and wait a few seconds the utility will offer some video drivers for us to experiment with.

The latest versions of Ubuntu and Lubuntu for that matter, come with the latest video drivers which often lack support for other video adapters. There are legacy versions of proprietary drivers available.

Regards.

---

### Post by kenb2 on 2015-11-13
Thank you for your advice, but I am new to this.  I don't know how to get to the Grub boot menu.  However the problem seems to be intermittent.  This morning I started up the machine and was able to log in.  I spent some time looking around, and getting used to ubuntu, everything works fast and fine.  Then I logged off and could not log back in.  With repeated attempts I was able to log in as guest.  Logged out could not log back in my account or guest account.  Restarted computer 4 times, on 4th restart I again successfully logged in.  Can this still be video driver problem?

---

### Post by mörgæs on 2015-11-13
Many problems are more likely than driver ones but let's find out.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by kenb2 on 2015-11-13
Hi Morgaes, I have managed to log in again.  I have made the lshw text file, but not sure how to use code tags.  I am going to try <> from the menu above my message.  I see it did not work.  I am new!  Also I had begun reading your post about older machines on my much newer computer, and was finding it interesting and I am sure helpful, but then I saw you had posted a reply.  Maybe I will try the LUBUNTU if that' what you recommend.  Thanks Ken

```
computer
    description: Computer
    product: Grantsdale-G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: D915GAV
       vendor: Intel Corporation
       physical id: 0
       version: AAC64137-400
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: EV91510A.86A.0482.2006.0222.2350
          date: 02/22/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: [REMOVED]
          slot: J2E1
          size: 2933MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: [REMOVED]
             slot: J6G1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: [REMOVED]
             slot: J6G2
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: [REMOVED]
             slot: J6H1
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: [REMOVED]
             slot: J6H2
             width: 64 bits
             clock: 400MHz (2.5ns)
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
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:ffa00000-ffafffff memory:d7f00000-d7ffffff
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:ff480000-ff4fffff ioport:ec00(size=8) memory:d8000000-dfffffff memory:ff440000-ff47ffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:ff43c000-ff43ffff
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:ff600000-ff6fffff ioport:d7b00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:ff700000-ff7fffff ioport:d7c00000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:3000(size=4096) memory:ff800000-ff8fffff ioport:d7d00000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:4000(size=4096) memory:ff900000-ff9fffff ioport:d7e00000(size=1048576)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c800(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:cc00(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ff43bc00-ff43bfff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:ff500000-ff5fffff ioport:d7a00000(size=1048576)
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:ff500000-ff500fff ioport:bc00(size=64)
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
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:c400(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600JB-00G
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2D08
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000b6583
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 148GiB
                capacity: 148GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-11-12 21:35:45 filesystem=ext4 lastmountpoint=/ modified=2015-11-13 13:22:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-11-13 13:22:31 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1014MiB
                capacity: 1014MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1014MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GSA-H22N
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.01
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by mörgæs on 2015-11-13
Yes, feed it Lubuntu 15.10 and forget what was posted about graphics drivers. Enjoy! 

Drivers are a much bigger problem for new hardware, only in rare cases for old.

Code tags are available in the advanced editor.

Please let me know if you have comments to the Old Hardware guide.

---

