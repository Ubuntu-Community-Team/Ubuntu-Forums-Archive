---
title: "Kernel fails to boot"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by fabian-hernalsteen on 2014-01-05
Hello,

Since i've done the upgrade to ubuntu 13.10, i am unable to boot.
After a lot of searching, i discovered that the latest kernel does not  boot.  Instead of fixing the problem, i went for the quick solution: I added  "GRUB_DEFAULT=saved" and "GRUB_SAVEDEFAULT=true" to /etc/default/grub  and simply selected an older kernel:
```

$ uname -r
3.8.0-34-generic

```

This worked fine at first, but now i am running into other issues as it is not the correct kernel for this ubuntu release

My question: how can this be debugged? When i boot the machine, i don't even get a terminal so i have no clue where i should start to search (and i am a complete noob when it comes to kernels :D)

Here is a screenshot of what happens when booting with the new kernel

[IMG]http://oi41.tinypic.com/1zwbvhi.jpg[/IMG]

FYI, i did an lshw, don't know if this is useful
```

mediacenter
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=A0E6423B-9570-DF11-BEB8-20CF3001266C
  *-core
       description: Motherboard
       product: P7H55-M
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: 105617820000919
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0503
          date: 04/08/2010
          size: 64KiB
          capacity: 8128KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.5.2
          serial: 0002-0652-0000-0000-0000-0000
          slot: LGA1156
          size: 3066MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
          configuration: cores=2 enabledcores=2 id=1 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.5.2
          serial: 0002-0652-0000-0000-0000-0000
          size: 3100MHz
          capabilities: vmx ht
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:f6000000-f7afffff ioport:e0000000(size=335544320)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:cc00(size=128) memory:f7a00000-f7a7ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7afc000-f7afffff
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:f5fff000-f5fff00f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f5ffe000-f5ffe3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f5ff8000-f5ffbfff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:f4000000-f41fffff ioport:f4200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f7e00000-f7efffff ioport:f4400000(size=2097152)
           *-ide
                description: IDE interface
                product: VT6415 PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list rom
                configuration: driver=pata_via latency=0
                resources: irq:17 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:f7ef0000-f7efffff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:f7c00000-f7dfffff ioport:f4600000(size=2097152)
           *-multimedia
                description: Multimedia video controller
                product: CX23885 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pciexpress pm vpd msi bus_master cap_list
                configuration: driver=cx23885 latency=0
                resources: irq:19 memory:f7c00000-f7dfffff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:f7b00000-f7bfffff ioport:f4f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: 20:cf:30:01:26:6c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:41 ioport:d800(size=256) memory:f4fff000-f4ffffff memory:f4ff8000-f4ffbfff memory:f7be0000-f7bfffff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f5ffd000-f5ffd3ff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f7f00000-f7ffffff
           *-network
                description: Wireless interface
                product: RT2800 802.11n PCI
                vendor: Ralink corp.
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: wlan0
                version: 00
                serial: 00:25:9c:f5:2d:0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-34-generic firmware=0.34 ip=192.168.0.108 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:16 memory:f7ff0000-f7ffffff
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=8) ioport:a480(size=4) ioport:a400(size=16) ioport:a080(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f5ffc000-f5ffc0ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16) ioport:b080(size=16)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: iHOS104
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: WL0B
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: Corsair Force 3
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 5.02
             serial: 12196504000017400369
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0001735d
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: ea8ff091-b744-48dd-8192-5f8ce231cab8
                size: 7628MiB
                capacity: 7628MiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 48GiB
                capacity: 48GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 48GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
        *-disk:1
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sdb
             version: 51.0
             serial: WD-WCAZA3254443
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7ed70e78-2e9c-4d1f-ba03-e38dc9f18aef sectorsize=512
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.1.0,2
                logical name: /dev/sdb2
                version: 1.0
                serial: de4e1357-549f-46dc-9b72-2d991e5c7464
                size: 21GiB
                capacity: 21GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-04-30 21:00:18 filesystem=ext4 label=home lastmountpoint=/media/mediacenter/home modified=2013-12-28 17:30:09 mounted=2013-12-28 17:30:09 state=clean
           *-volume:1
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.1.0,3
                logical name: /dev/sdb3
                version: 1
                serial: 636b5169-a53b-428c-ad0d-65aae178e7c9
                size: 7627MiB
                capacity: 7628MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@1:0.1.0,4
                logical name: /dev/sdb4
                logical name: /data
                version: 1.0
                serial: 3029d8d6-9430-4624-ad32-49be8cbc01b5
                size: 1815GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-04-30 21:00:20 filesystem=ext4 label=media lastmountpoint=/data modified=2014-01-05 13:16:10 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-01-05 13:16:10 state=mounted

```

Thanks for your hints,
Fabian

---

### Post by fabian-hernalsteen on 2014-01-05
The update manager just notified me that there is a new kernel. 
Downloading it right now, hope it fixes my problem. I will keep you posted

---

### Post by fabian-hernalsteen on 2014-01-05
I tried with kernel 3.11.0.15, still the exact same issue. 
When booting the kernel, the last thing i see is "loading initial ramdisk"
When booting in recovery mode, the last thing is about ispnp (see previous screenshot)

---

### Post by Doug S on 2014-01-05
There is a reasonable probability that your issue is still video related and that your [other thread]("http://ubuntuforums.org/showthread.php?t=2196221") is not actually "solved" yet, but as Bucky Ball mentioned on that other thread, there are no details as to how it was "solved".

What I am saying is that I suspect your kernel is actually booting and running fine, but is not interacting with the terminal. This happens to me often on my test computers, but I don't care since I normally only run servers and I just ssh into the computer when the terminal display doesn't work. 

So how to verify if your kernel is actually running or not? Can you "ping" the computer from another computer? If you don't have it installed already, you could install ssh server ( sudo apt-get install openssh-server ) and use an ssh client from another computer to attempt to connect to determine if the kernel is actually running (that is what I do). There might be simpler methods and/or workarounds, which perhaps someone else will mention.

---

### Post by fabian-hernalsteen on 2014-01-07
Thanks for your reply. I will test this evening when i get home

---

### Post by fabian-hernalsteen on 2014-01-07
I started a ping from an ancient ubuntu 9.10 laptop (good old times:P). I do not have a wired network connection so i did the test to the wireless card (hope this is not a problem, guess not)

I did following tests (multiple times to be sure)
Test 1
- machine is running with old kernel - ping ok
- reboot - ping stops
- machine comes back up - ping ok

Test 2
- machine is running with old kernel - ping ok
- reboot to new kernel- ping stops
- machine boots up to a certain point - ping not ok
- wait for a few minutes to be sure - ping still not ok

Clearly, networking is not started in the background. Any other suggestions?

---

