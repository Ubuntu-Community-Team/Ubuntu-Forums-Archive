---
title: "Unity launcher flickering"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by Thee on 2012-11-27
Hey there!

When ever I'm on YouTube playing a video, or when Jdownloader is running in the background, and when I press the launcher menu, part of the launcher flickers (with youtube its the  part where the video is). See screenshots:

[[img]http://s7.postimage.org/kewfu2b4n/image.jpg[/img]](http://postimage.org/image/kewfu2b4n/)

[[img]http://s7.postimage.org/qh42kjzkn/image.jpg[/img]](http://postimage.org/image/qh42kjzkn/)

You can't tell from the screen, but that hidden part of the launcher appears/disappears constantly (flickers).

This happened with some other programs too, don't remember which exactly. And it happens only when a program is on the desktop, not when its minimized, ofc.

Its not really a problem, but its annoying. Is there a solution for this or is this a bug?

---

### Post by Thee on 2012-11-27
No one?

---

### Post by Darkhaund on 2012-11-27
I really have no idea.

Does it have to do with the theme you have?

I notice you have a different theme... which on is it?

---

### Post by Thee on 2012-11-28
Theme is the default one. I only changed the icons.

This does not happen to you when you play a video on youtube and open the launcher?

---

### Post by 3rdalbum on 2012-11-28
It's possible your flickering problem might subside if you switch Unity to "low graphics mode"? This page explains how: [http://www.ubuntuvibes.com/2012/10/make-unity-more-responsive-in-ubuntu.html](http://www.ubuntuvibes.com/2012/10/make-unity-more-responsive-in-ubuntu.html)

It just disables the transparency of the Dash and Launcher. Your flickering problem may be that the CPU and GPU are stressed by playing the video, and therefore don't have enough power to smoothly calculate the transparency of the Launcher at the same time.

---

### Post by audiomick on 2012-11-28
> **3rdalbum said:**
> Your flickering problem may be that the CPU and GPU are stressed by playing the video, and therefore don't have enough power to smoothly calculate the transparency of the Launcher at the same time.

I've been watching this thread but not answering as I can't offer a solution, but that thought had occurred to me too. Perhaps you could tell us what CPU and graphics card you have, and how much RAM. Maybe someone will be able to say definitively whether you can expect that hardware to run smoothly or not.

You can get a list of your hardware with
```
sudo lshw
```

That generates quite a bit of stuff, so use the # button at the top of the post window to put code tags around it if you want to post it here.

---

### Post by Thee on 2012-11-28
It shouldn't be a hardware problem.
Btw, I noticed when I install something using the Ubuntu Software Center, the launcher also flickers when the progress bar is moving.

```

           *-multimedia
                description: Audio device
                product: Barts HDMI Audio [Radeon HD 6800 Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:50 memory:fdefc000-fdefffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port E)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fdb00000-fdbfffff ioport:fd200000(size=1048576)
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fdbfe000-fdbfffff
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:fd100000-fd1fffff ioport:fdf00000(size=1048576)
           *-storage
                description: SATA controller
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:18 memory:fd1fe000-fd1fffff
           *-ide
                description: IDE interface
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:19 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:43 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02e000-fe02efff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02d000-fe02d0ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02c000-fe02cfff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02b000-fe02b0ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fe024000-fe027fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:b000(size=4096) memory:fdd00000-fddfffff memory:fdc00000-fdcfffff
           *-multimedia
                description: Multimedia audio controller
                product: CM8738
                vendor: C-Media Electronics Inc
                physical id: 7
                bus info: pci@0000:04:07.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_cmipci latency=32 maxlatency=24 mingnt=2
                resources: irq:21 ioport:be00(size=256)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:04:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:fddff000-fddff7ff memory:fddf8000-fddfbfff
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02a000-fe02afff
        *-pci:4
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:a000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
           *-storage
                description: SATA controller
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:17 memory:fdafe000-fdafffff
           *-ide
                description: IDE interface
                product: JMB363 SATA/IDE Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:af00(size=8) ioport:ae00(size=4) ioport:ad00(size=8) ioport:ac00(size=4) ioport:ab00(size=16)
        *-pci:5
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:9000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 03
                serial: 1c:6f:65:89:42:3b
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:49 ioport:9e00(size=256) memory:fd7ff000-fd7fffff memory:fd7f8000-fd7fbfff memory:fd700000-fd71ffff
        *-pci:6
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:8000(size=4096) memory:fd600000-fd6fffff ioport:fd500000(size=1048576)
        *-pci:7
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:7000(size=4096) memory:fd400000-fd4fffff ioport:fd300000(size=1048576)
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe029000-fe029fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe028000-fe0280ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72105
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: JP2O
             serial: JP1570HJ1MHK9K
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=c045a607
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 085a2ba5-b5cb-ac4a-b87e-bb56b4d59f0c
                size: 57GiB
                capacity: 57GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-01-28 19:49:29 filesystem=ntfs label=Win7sys state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 0067eef9-4126-8e4a-a577-0524731841d7
                size: 279GiB
                capacity: 279GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-01-28 19:50:01 filesystem=ntfs label=Radni 400GB state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                size: 127GiB
                capacity: 127GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 122GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 5720MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi10
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 6Y120P0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdb
             version: YAR4
             serial: Y34CPWDE
             size: 114GiB (122GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=8ef6c3a0
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@10:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: 104ce274-afb2-5643-a13f-4eb2b5408f01
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-09-24 22:32:31 filesystem=ntfs label=temp downloads state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@10:0.0.0,2
                logical name: /dev/sdb2
                size: 94GiB
                capacity: 94GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 94GiB

```

---

### Post by newb85 on 2012-11-28
The hardware maxing out was my thought, too.

Was that the entire list?  Perhaps I'm too much of a dunce to find it, but your graphics card doesn't even seem to be in that list.

Addendum: perhaps it would reduce the need for visual wading if you ran the following:

```
sudo lshw -c video
sudo lshw -short
```

---

### Post by Thee on 2012-11-28
Well I copied everything. My Graphics card is ATI HD 6870, CPU Phenom x4 3.2GHz, and 6GB of RAM.

---

### Post by newb85 on 2012-11-28
Well I'm befuddled.  On second thought, that list seems to exclude your CPU, GPU, and RAM.  (At the very least, they're not categorized normally.)

---

### Post by Thee on 2012-11-28
```

  *-display               
       description: VGA compatible controller
       product: Barts PRO [Radeon HD 6800 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:51 memory:d0000000-dfffffff memory:fdec0000-fdedffff ioport:ee00(size=256) memory:fde00000-fde1ffff

```

```

H/W path        Device     Class       Description
==================================================
                           system      GA-870A-UD3 ()
/0                         bus         GA-870A-UD3
/0/0                       memory      128KiB BIOS
/0/4                       processor   AMD Phenom(tm) II X4 955 Processor
/0/4/a                     memory      128KiB L1 cache
/0/4/c                     memory      512KiB L3 cache
/0/b                       memory      128KiB L1 cache
/0/27                      memory      6GiB System Memory
/0/27/0                    memory      2GiB DIMM 1066 MHz (0.9 ns)
/0/27/1                    memory      2GiB DIMM 1066 MHz (0.9 ns)
/0/27/2                    memory      2GiB DIMM 1066 MHz (0.9 ns)
/0/27/3                    memory      DIMM 1066 MHz (0.9 ns) [empty]
/0/100                     bridge      RX780/RX790 Chipset Host Bridge
/0/100/2                   bridge      RD790 PCI to PCI bridge (external gfx0 po
/0/100/2/0                 display     Barts PRO [Radeon HD 6800 Series]
/0/100/2/0.1               multimedia  Barts HDMI Audio [Radeon HD 6800 Series]
/0/100/9                   bridge      RD790 PCI to PCI bridge (PCI express gpp 
/0/100/9/0                 bus         uPD720200 USB 3.0 Host Controller
/0/100/a                   bridge      RD790 PCI to PCI bridge (PCI express gpp 
/0/100/a/0                 storage     JMB363 SATA/IDE Controller
/0/100/a/0.1               storage     JMB363 SATA/IDE Controller
/0/100/11                  storage     SB7x0/SB8x0/SB9x0 SATA Controller [IDE mo
/0/100/12                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                  bus         SBx00 SMBus Controller
/0/100/14.1                storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.2                multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/7              multimedia  CM8738
/0/100/14.4/e              bus         TSB43AB23 IEEE-1394a-2000 Controller (PHY
/0/100/14.5                bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/15                  bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE
/0/100/15/0                storage     JMB363 SATA/IDE Controller
/0/100/15/0.1              storage     JMB363 SATA/IDE Controller
/0/100/15.1                bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE
/0/100/15.1/0   eth0       network     RTL8111/8168B PCI Express Gigabit Etherne
/0/100/15.2                bridge      SB900 PCI to PCI bridge (PCIE port 2)
/0/100/15.3                bridge      SB900 PCI to PCI bridge (PCIE port 3)
/0/100/16                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                     bridge      Family 10h Processor HyperTransport Confi
/0/102                     bridge      Family 10h Processor Address Map
/0/103                     bridge      Family 10h Processor DRAM Controller
/0/104                     bridge      Family 10h Processor Miscellaneous Contro
/0/105                     bridge      Family 10h Processor Link Control
/0/1            scsi1      storage     
/0/1/0.0.0      /dev/sda   disk        500GB Hitachi HDS72105
/0/1/0.0.0/1    /dev/sda1  volume      57GiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2  volume      279GiB Windows NTFS volume
/0/1/0.0.0/3    /dev/sda3  volume      127GiB Extended partition
/0/1/0.0.0/3/5  /dev/sda5  volume      122GiB Linux filesystem partition
/0/1/0.0.0/3/6  /dev/sda6  volume      5720MiB Linux swap / Solaris partition
/0/2            scsi10     storage     
/0/2/0.0.0      /dev/sdb   disk        122GB Maxtor 6Y120P0
/0/2/0.0.0/1    /dev/sdb1  volume      19GiB Windows NTFS volume
/0/2/0.0.0/2    /dev/sdb2  volume      94GiB Extended partition
/0/2/0.0.0/2/5  /dev/sdb5  volume      94GiB HPFS/NTFS partition

```

---

### Post by newb85 on 2012-11-28
That first one showed your GPU, and the short list showed your memory and CPU.  Run these for more details on your memory and CPU.

```
sudo lshw -c memory
sudo lshw -c processor
```

(Don't know why they weren't there the first time.  Maybe the beginning of the output was cut off?)

---

### Post by Thee on 2012-11-28
No idea. If it was an error on my end, I apologize.

```

  *-firmware              
       description: BIOS
       vendor: Award Software International, Inc.
       physical id: 0
       version: F2
       date: 06/07/2010
       size: 128KiB
       capacity: 960KiB
       capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: a
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L3 cache
       physical id: c
       slot: External Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: synchronous internal write-back
  *-cache
       description: L1 cache
       physical id: b
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-memory
       description: System Memory
       physical id: 27
       slot: System board or motherboard
       size: 6GiB
     *-bank:0
          description: DIMM 1066 MHz (0.9 ns)
          physical id: 0
          slot: A0
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: DIMM 1066 MHz (0.9 ns)
          physical id: 1
          slot: A1
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:2
          description: DIMM 1066 MHz (0.9 ns)
          physical id: 2
          slot: A2
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:3
          description: DIMM 1066 MHz (0.9 ns) [empty]
          physical id: 3
          slot: A3
          width: 64 bits
          clock: 1066MHz (0.9ns)

```

```

  *-cpu                   
       description: CPU
       product: AMD Phenom(tm) II X4 955 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Phenom(tm) II X4 955 Processor
       slot: Socket M2
       size: 800MHz
       capacity: 3200MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save cpufreq

```

---

### Post by audiomick on 2012-11-28
> **newb85 said:**
> Well I'm befuddled.  On second thought, that list seems to exclude your CPU, GPU, and RAM.  (At the very least, they're not categorized normally.)

Yes, I suspect that those things were out the top of the terminal somehow. They are not there, anyway.

Edit: scratch that. Somehow or other a couple of post didn't show up here until after I had posted that.

That machine looks to me like it shouldn't be having problems with resources...

---

### Post by Thee on 2012-11-28
> **audiomick said:**
> That machine looks to me like it shouldn't be having problems with resources...

That's what I've been saying. So it's a software problem. As I see, this flickering happens whenever underneath the launcher there is something that's moving (download manager progress, install progress, video).

---

### Post by 3rdalbum on 2012-11-28
> **Thee said:**
> That's what I've been saying. So it's a software problem. As I see, this flickering happens whenever underneath the launcher there is something that's moving (download manager progress, install progress, video).

Have you installed the ATI driver?

I can't remember where it is in Ubuntu 12.10, but there is a program already installed that offers to download and install any additional drivers for you. If you haven't already used that, then you should do so or you will have low/no 3d performance and low video playback acceleration

---

### Post by audiomick on 2012-11-28
> **3rdalbum said:**
> I can't remember where it is in Ubuntu 12.10,...

I don't have 12.10 on any of my machines yet, but I think it is in system settings> software. I read that somewhere here, I think.

---

### Post by newb85 on 2012-11-28
Grabbing "Software Sources" from the Dash and going to the tab about drivers works too, I think.  (At least I think I remember reading that Software Sources had been made available at the Dash again, and that Jockey's functionality had been moved to a tab there.)

---

### Post by Thee on 2012-11-29
> **3rdalbum said:**
> Have you installed the ATI driver?

Yes I did. I play the games just fine. Even the Windows ones.
[[img]http://s8.postimage.org/j1pns7tch/Untitled.jpg[/img]](http://postimage.org/image/j1pns7tch/)

Maybe it's a driver related problem?

---

### Post by diogenes83 on 2013-04-24
I had the same problem, And since no solution was posted here i thought someone may be helped if i post what solved it for me.

Disable "Fading windows" in CCSM

[Link]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1070735") to the post that helped me.

---

### Post by Thee on 2013-04-24
Thanks for the tip, but unfortunately that didn't help me. I have the same problem even with fading windows disabled.
I guess I will just have to wait for the update to fix it.

---

### Post by mc4man on 2013-04-24
The screen shot reminds me of this bug
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1055308](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1055308)

---

### Post by Thee on 2013-04-25
Well I tried disabling those OpenGL options also, and the problem still persists. I'm thinking of upgrading to 13.04 now anyway, so the problem might go away.

---

