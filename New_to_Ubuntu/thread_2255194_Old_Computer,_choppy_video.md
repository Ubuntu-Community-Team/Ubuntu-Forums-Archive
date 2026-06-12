---
title: "Old Computer, choppy video"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by cap10longboat on 2014-12-02
Hello.  I've recently installed Lubuntu on a spare parts throw together system for my man-cave.  Not trying to do anything fancy, just basic internet access.  

It boots up and runs just fine, but streaming video such as youtube is extremely choppy.

Sempron 2800
1GB ddr400
80GB IDE hdd
Nvidia geforce 128MB (unsure of specific processor)

Is this computer simply too old?

Any help would be appreciated.

---

### Post by papibe on 2014-12-02
Hi cap10longboat. Welcome to the forum ):P

I don't have a clear picture how fast that processor is, but I'm gonna guess is equivalent to a Pentium 3?

If so, youtube videos will play very slow mainly because of video decoding on Firefox.

You may get better performance reproducing local video files, if you get a relatively newer graphic card though.

Let us know if you have more questions.

Come here often and have fun.
Regards.

---

### Post by mastablasta on 2014-12-03
try reducing quality of your tube videos. The CPU should be able to handle you tube. though maybe not full screen.

you can also try Chrome which uses pepper flash.

I think the issue is the graphics card, not the CPU.

1,2 Ghz Athlon with 224 MB ram and 32MB GPU card plays youtube ok as long as they are not full screen.

---

### Post by mörgæs on 2014-12-03
Let's see which gear you are using. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by cap10longboat on 2014-12-03
Here it is.  A bit of a dinosaur.

```
computer
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 760GX-M
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 09/16/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot virtualmachine
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          slot: Socket 754
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:e8000000-e9ffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master vga_palette
             resources: ioport:d000(size=4096) memory:eb000000-eb0fffff memory:d8000000-dfffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:d8000000-dfffffff memory:eb000000-eb01ffff ioport:d000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e000(size=256) ioport:e100(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:20 memory:eb122000-eb122fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:21 memory:eb123000-eb123fff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:22 memory:eb124000-eb124fff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32 maxlatency=80
             resources: irq:23 memory:eb120000-eb120fff
        *-display
             description: VGA compatible controller
             product: NV18 [GeForce4 MX 4000]
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
             resources: irq:17 memory:ea000000-eaffffff memory:e0000000-e7ffffff memory:40000000-4001ffff
        *-network
             description: Ethernet interface
             product: RTL8169 PCI Gigabit Ethernet Controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
             resources: irq:18 ioport:e300(size=256) memory:eb125000-eb1250ff memory:40020000-4003ffff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 6L080P0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: BAJ4
             serial: [REMOVED]
             size: 76GiB (81GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00066d11
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 75GiB
                capacity: 75GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-01 15:47:36 filesystem=ext4 lastmountpoint=/ modified=2014-12-02 20:47:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-02 20:47:41 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 895MiB
                capacity: 895MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 895MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          bus info: usb@1:8
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-32-generic firmware=0.29 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by mörgæs on 2014-12-04
Yes, as suggested above the graphics processors are slow. 

This thread deals with a similar problem and might give some inspiration:
[http://ubuntuforums.org/showthread.php?t=2254404](http://ubuntuforums.org/showthread.php?t=2254404)

You haven't commented on what was mentioned in post #2: Is it only a problem for streaming or also for local films?

---

### Post by monkeybrain20122 on 2014-12-04
Probably it would help a bit if you don't use flash for streaming

[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

For Youtube only, get smtube from ppa
[https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)

---

