---
title: "HP Pavilion dv6000 wireless issues"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by choklitmello on 2014-05-03
Hello, I'm relatively new to Ubuntu. I aquired an old HP Pavilion and installed Ubuntu on it. I believe I had 12.04 on it first. The wireless worked for a little bit with a fix I found online, then went out again. I followed a few guides but nothing worked, so I shelved it for a while. Today I updated to 13.10 (14.04 wouldn't work due to what I believe are driver issues). I think perhaps the wireless card broke because in most of the guides, the first thing they do is give a command to identify the wireless card, and for the life of me I cannot get any of them to work. If you could help me get this fixed (if the wireless card is still operational) or just simply confirm that it's broken, it would be an immense help.

Extra info:
-The motherboard on it was broken when I got it, so I replaced it. I don't think it's too relevant since the wireless did work for a little while in the beginning, but every bit of information helps
-The wireless switch has two positions and when functioning, gives an orange light when it's off and a blue light when it's on. The light does not turn blue when the switch is flipped. I never paid much attention when it was working (how easy it is to take such things for granted...) so I don't know if it's supposed to be blue any time the switch is on or just when it's on AND connected.

Thanks!

---

### Post by mörgæs on 2014-05-04
There could be several problems here, both hard- and software. Please begin with running ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by choklitmello on 2014-05-04
Contents of lshw.txt: 
```
 computer
    description: Notebook
    product: HP Pavilion (EZ475UAR#ABA) (EZ475UAR#AB)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 family=103C_5335KV sku=EZ475UAR#AB uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 30B8
       vendor: Quanta
       physical id: 0
       version: 65.2B
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.3D
          date: 11/22/2007
          size: 101KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-52
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.8.2
          slot: Socket S1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: NT512T64UH8A1FN-3C
             vendor: F7F7F7B000000000
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: NT512T64UH8A1FN-3C
             vendor: F7F7F7B000000000
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.8.2
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: NVIDIA Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: NVIDIA Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: NVIDIA Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: NVIDIA Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: NVIDIA Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:4000(size=4096) memory:c2000000-c3ffffff ioport:c8200000(size=2097152)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:5000(size=4096) memory:c4000000-c5ffffff ioport:c8400000(size=2097152)
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 memory:c6000000-c7ffffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G72M [GeForce Go 7200]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:16 memory:c7000000-c7ffffff memory:d0000000-dfffffff memory:c6000000-c6ffffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1d00(size=128)
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: NVIDIA Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: NVIDIA Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0040000-c007ffff
     *-usb:0
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:c0004000-c0004fff
     *-usb:1
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:c0005000-c00050ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:3080(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:30c0(size=8) ioport:30b4(size=4) ioport:30b8(size=8) ioport:30b0(size=4) ioport:3090(size=16) memory:c0006000-c0006fff
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: memory:c8000000-c80fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:07:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:5 memory:c8000000-c80007ff
        *-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:07:05.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=64
             resources: irq:7 memory:c8000800-c80008ff
        *-generic:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:07:05.2
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=r592 latency=0
             resources: irq:7 memory:c8001000-c80010ff
        *-generic:2
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:07:05.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=r852 latency=0
             resources: irq:7 memory:c8001400-c80014ff
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:c0000000-c0003fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: [REMOVED]
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=[REMOVED] latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:20 memory:c0008000-c0008fff ioport:30e0(size=8)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
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
          physical id: 6
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4084N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: KQ09
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 7
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST98823AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 7.24
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000e38e6
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 73GiB
                capacity: 73GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-05-03 17:26:10 filesystem=ext4 lastmountpoint=/ modified=2014-05-03 20:42:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-05-03 20:42:05 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 1022MiB
                capacity: 1022MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1022MiB
                   capabilities: nofs 
```

---

### Post by mörgæs on 2014-05-04
It's powerful enough to run all the Buntus, but of course there could be other kind of hardware problems. From your post it sounds like it could have been dropped or suffered some other kind of injury.

Let's focus on the wired connection for now. What happens in a fresh install of 14.04?

---

### Post by choklitmello on 2014-05-04
It installs, then will boot to the log-in screen. When you log in, the log-in screen GUI goes away and it just stays on whatever the background was on that screen. You do have control over the mouse, but there's nothing you can do with it. When you use a live CD and select to try 14.04, it gives a black screen and stays there. I made sure to test 13.10 with a live CD and the "try it" option worked so I installed, Interestingly enough, when I went to install 13.10, it said it detected no prior operating system on it, even though 14.04 was on there and could boot but not log in.

---

### Post by mörgæs on 2014-05-04
For Nvidia screen cards it's often a good idea to add the **nomodeset** boot option or check 'restricted software' during install.

Your output from lshw is not complete. Please post in full length.

---

### Post by choklitmello on 2014-05-04
How would I add the nomodeset boot option?And that's all I had in the lshw output. I ran it again and got the same result, right down to the character count.

---

### Post by wildmanne39 on 2014-05-04
Please post the output from:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by choklitmello on 2014-05-05
```

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Kernel driver in use: forcedeth

```

---

### Post by wildmanne39 on 2014-05-05
The card is not showing up so here are the options.

1. Check and make sure the card is plugged in or setted properly after changing the mother board.
2. Reset the bios and see if that fixes it.
3. Buy an usb adaptor.

I have one of these laptops and the light should be blue when the card is on, my card went completely out in this model.

---

### Post by choklitmello on 2014-05-05
Thanks for all of the help. I have a USB adapter that on its way that I ordered a while ago before I got on here because I was pretty sure the card was broken. I'll make sure the card is in good once I hunt down my tiny screwdriver set.

---

