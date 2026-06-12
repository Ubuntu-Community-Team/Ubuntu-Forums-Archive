---
title: "30 minute bootup time"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by stereo247 on 2008-09-24
Hi. I have a Fujitsu Siemens M7405 Amilo laptop. My experience with installing Ubuntu 8.04. I have listed them below:
(1) When tyring to run any of the standard options in the first installer menu I ended at a command prompt???

I deselected the first option in the F6 menu and this problem was resolved (I think) because then I was able to install.

(2) While trying to run the installer a message appeared "pnp bios fatal error" with a couple of other lines about me needing to possibly disable this function???

This problem didn t however stop the installer from continuing. So the program finally installed. I used a dual boot option following the directions on the Ubuntu site.

(3)30 minute bootup time with an error message about 5 minute in saying "no buffer space avaiable". 25 minutes later I was in to what could only be described as the slowest operating system ever. It took 5 minutes to open the help file.

HELP!!!:confused:

---

### Post by jgedutis on 2008-09-24
You said that you installed using a dual boot option.  Is that because you have another OS like Windows XP installed?  If you do have another OS installed, does that one function properly?

I have had issues installing that were resolved by using the alternate install cd [http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso)

You could try that installer if you don't mind installing over again.  Personally I would try to get an install to work without error rather than troubleshoot errors or a slow system after an error prone install.

---

### Post by stereo247 on 2008-09-25
Sorry man tried this and cant even get passed the intial installation screen - just hangs irrespective of option chosen. Any other ideas?

---

### Post by Crafty Kisses on 2008-09-25
You can try booting into verbose mode and see where it actually hangs, when you're booting up, press the following:
```
Cntrl+Alt+F2
```
It should read off some error messages, post the back here.

---

### Post by kansasnoob on 2008-09-25
Are you able to run the live CD? I mean choosing Try without changes to computer?

---

### Post by kansasnoob on 2008-09-25
What I'm specifically wanting to see is your system specs. It'll be a long list but if you can boot the live CD and go to terminal then post the output of:

```
sudo lshw
```

(BTW: that's LSHW) It'll show all system specs like this:

> lance@lance-desktop:~$ sudo lshw
lance-desktop             
    description: Desktop Computer
    product: ID-PCM7E PC2500
    vendor: IDOT
    version: 1.x
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: ID-PCM7E PC2500
       vendor: IDOT
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/26/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: VIA Esther processor 1500MHz
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: 6.10.9
          slot: Socket 370
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: 9
             slot: External Cache
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 mingnt=2
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=64 module=sata_via
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1S
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 9L08
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             logical name: scsi3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64 module=pata_via
           *-disk
                description: ATA Disk
                product: WDC WD800JB-00JJ
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM9V620494
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=63056305
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 38c5aa95-12f1-8349-8b57-22b0e73dfec3
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-04-28 02:15:43 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 45GiB
                   capacity: 45GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 23GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1890MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 18GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 878MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM DDU1615
                vendor: SONY
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: GYS5
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
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
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:1b:b9:6d:d3:7a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=208.189.35.13 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
lance@lance-desktop:~$ 



---

