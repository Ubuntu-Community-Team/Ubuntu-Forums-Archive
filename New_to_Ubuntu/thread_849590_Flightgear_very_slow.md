---
title: "Flightgear very slow"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-04
Hi,

  I installed flightgear thru add/remove applications. when i opened flightgear no problem with graphics was found. but wat i seen is the application is very slow than usual. i even notice my PC's busy (red) light is indicating this busy application, but it is not. it is as normal as is. What may be the reason please help me. i cant play games it s tooooo slow.

---

### Post by ramjet_1953 on 2008-07-04
Some system specs would be useful:

CPU type and speed?

Video card/chipset and video RAM?

Have you enabled hardware 3D acceleration?

Have you installed the driver for your video card?

Amount of user RAM

Regards,
Roger :cool:

---

### Post by mailtwogopal on 2008-07-05
Hi,

 i executed command "sudo lshw" which i got from google. sorry for such a long o/p to post here. since i cant find device manager from system - administration. bare with me and below is the o/p.

```

gopal@gopal-desktop:~$ sudo lshw
[sudo] password for gopal: 
gopal-desktop             
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=75E61A08-4460-11DB-A454-00E0188FF8F4
  *-core
       description: Motherboard
       product: D102GGC2
       vendor: Intel Corporation
       physical id: 0
       version: AAD42789-204
       serial: BTGC637000YE
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: GC11020M.86A.1065.2006.0502.1638 (05/02/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 512MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DDR [empty]
             physical id: 0
             slot: DIMM0
        *-bank:1
             description: DIMM DDR [empty]
             physical id: 1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 0x4A4D33363751363433412D35202020202020
             vendor: 0x7F4F000000000000
             physical id: 2
             serial: 0x00000000
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR [empty]
             physical id: 3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: ST3802110AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9LR04Y9V
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f9e3f9e3
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: afed58da-c5e5-4cc7-aedb-e370ed0ac87a
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-28 20:10:40 filesystem=ext3 modified=2008-07-05 10:11:33 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-04 20:46:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1278MiB
                   capacity: 1278MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1278MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 81
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi5
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-cdrom
                description: DVD reader
                product: CDW/DVD SH-M522C
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TS07
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:16:76:c6:8c:7c
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

---

### Post by Dr Small on 2008-07-05
Next time, enclose it is [noparse]```

```[/noparse] tags so it is readable.

---

### Post by Sam Lars on 2008-07-17
I have the same problem.  I'm sure a better graphics card would help, as would a faster system.

---

### Post by jml75 on 2008-09-12
I have the same problem and my system spec is certainly not the problem.

I have a Athlon X2 2.4Ghz
2Gig of dual channel DDR2-800
And a 7600GT video card.

There is no way that my problem can come from an inadequate system spec and I have exactly the same problem.

Any one have found a fix for this? Maybe it's a flighgear misconfig?

Any help would be welcomed.

---

### Post by tigerdog on 2008-10-10
I am ABSOLUTELY not expert at this, but I have a system with very similar specs (including a 7600GS card).  I get performance that's at least useable if I use the proprietary NVIDIA driver that does 3D acceleration on the card.  I also get much better performance (58fps v 5 fps) if I drop the bit depth of the screen from 24 bits to 16.  I did this by manually editing /etc/X11/xorg.conf and changing the entry in the "screen" section

Make sure to save a copy of xorg.conf someplace where you can easily recover it BEFORE you edit it and restart the display.

---

### Post by skyway45 on 2009-11-19
You might not THINK you are the quintessential expert on this, but after days of suspecting an nVidia driver problem, suspecting pulseaudio and then removing it and installing esound, reinstalling pulseaudio, trying a different driver, deleting and reinstalling Flightgear, etc....  going into xorg.conf and changing that 24 to a 16 took me from a very choppy and 'no fun and impossible to control flight at all'  framerate of about 9fps (with all scenery options disables, up to 40+ fps now, with all scenery options enabled!  Thank You so much.

---

### Post by overdrank on 2009-11-19
Did you notice the date on the thread > July 4th, 2008  :)
Thread closed

---

