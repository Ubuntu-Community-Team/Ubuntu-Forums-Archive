---
title: "Intel 82845G/GL: Color Depth"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by posaojedan on 2013-10-31
I'm a total newbie to this, but managed to install Lubuntu on an old desktop PC.
Now I've run into an issue: the color depth isn't set to true colour (24 bit) and the gradients look super bad.

First I followed some guides to verify that the graphic card drivers are installed doing the ```
sudo apt-get install xserver-xorg-video-intel
``` thing and they are.

Then I found another guide telling me to add DefaultDepth 24 to the Xorg.conf file, but I'm not sure where to exactly put that line since it contains way more lines than the one shown in the tutorial. Here's how the config file looks like: [http://pastebin.com/ufRJGbwB](http://pastebin.com/ufRJGbwB)

Am I doing this the correct way or is there another, better way to change the color depth? Or maybe the integrated graphics aren't good enough for Lubuntu in the first place?

---

### Post by mörgæs on 2013-10-31
Hi, welcome to the fora.

> **posaojedan said:**
> Or maybe the integrated graphics aren't good enough for Lubuntu in the first place?

That may be the explanation. Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by posaojedan on 2013-10-31
Here it is.

```
computer
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 8GE667
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG
          date: 09/17/2002
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: Socket 478
          size: 2400MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.2.4
          slot: Socket 478
          size: 2400MHz
          capacity: 3066MHz
          clock: 100MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-d7ffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d8000000-dfffffff memory:e2000000-e207ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e2080000-e20803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:a000(size=4096) memory:e0000000-e1ffffff memory:20000000-200fffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:01:02.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:22 ioport:a000(size=256) memory:e1000000-e10000ff memory:20000000-2000ffff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:cc00(size=16) memory:20100000-201003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5000(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:d400(size=256) ioport:d800(size=64) memory:e2082000-e20821ff memory:e2083000-e20830ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JB-00CR
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 17.0
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0003e5de
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 74GiB
                capacity: 74GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-31 11:33:07 filesystem=ext4 lastmountpoint=/target modified=2013-10-31 12:01:45 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-10-31 12:01:45 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 503MiB
                capacity: 503MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 503MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7170A
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.02
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

In the meantime, I tried to add the DefaultDepth line as per instructions found in another thread (disregarding the extra stuff in the config), but Lubuntu failed to boot after that.

---

### Post by mörgæs on 2013-10-31
While the old Intel graphics cards are trustworthy and well supported they are not that powerful. I wouldn't expect a high resolution and / or colour depth. 

If you can find another 512 MB of memory it will make a big difference. Should not cost you much.

---

### Post by posaojedan on 2013-11-01
Solved it, I think.
I removed everything from the xorg.conf file, except for this:

```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
        DefaultDepth 24
EndSection

```

Then I rebooted and everything's fine now. Hopefully the removal of the other chunk of lines from the config won't cause any issues.

---

### Post by mörgæs on 2013-11-01
It surprises me that it was so easy. If a simple setting in xorg.conf can do the trick, why wasn't 24 bit detected and enabled by the system by default? Hmmm....

Anyway, now I also learned something.

---

