---
title: "Sager N6852 and Linux Issues: Need Ubuntu release advice"
date: 2017-09-26
forum: New to Ubuntu
---

### Post by kelltech on 2017-09-26
[COLOR=#000000][FONT=sans-serif]Hello,[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I've been using Mint for a few years and I'm no Linux pro, but I just bought a Sager N6852 and received it last week.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I decided on that laptop because I was able to order it without an OS and I intend to run Linux, and because System76 and OpensourcePC among others use Sager/Clevo laptops. Someone is going to ask why didn't I just buy from System76, and that's because the equivalent of my laptop would easily cost $400 more from System76. [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I have tried Linux Mint 18.2, Ubuntu 16.04 and 17.04 and a few others, but have had some trouble and am running into a few problems.[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Most notably, the sound is horrible. It actually sounds like an old time AM radio. Also, the only fn keys that work are volume. I can't change the keyboard color from it's default blue (which by itself isn't a big deal, just an extra feature), but I'm also unable to dim screen brightness, or do anything else the fn keys operate.[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I couldn't live boot Ubuntu 16.04 past the splash screen to even attempt an install to see how it would go. Also, in 17.04 I have to use the 4.10.0.19 kernel, it appears my i7 Kabylake doesn't like the 4.10.0.35. [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I've searched high and low all over the internet, including the Linux Mint and Ubuntu communities among others for a week and can't find answers. After working in Linux in an older machine for the last few years, I'm really trying to avoid having to go back to Windows.[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I'm not stuck on Mint or any other at this point, I just want to be able to use my laptop's features as best as I can, especially the sound problem, which is a deal breaker for me.

I'm at my wits end. [S]Can someone please suggest an Ubuntu release that I should install and then try and address these issues?[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][/S][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] _**Edit:**_ I have 17.04 up and running to hopefully find some help addressing the trouble.

I would sincerely appreciate any amount of help you may be able to provide.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Thank you![/FONT][/COLOR]

---

### Post by mörgæs on 2017-09-26
Hi, welcome to the fora.

How does 17.10 (beta) work in a live boot?

---

### Post by kelltech on 2017-09-26
> **mörgæs said:**
> Hi, welcome to the fora.

How does 17.10 (beta) work in a live boot?
It won't boot past the load/splash screen. Unfortunately, I'm just about convinced that Linux isn't going to work on this machine, be it hardware, drivers, or whatever. Even 17.04 keeps hanging on me and I've forced power off dozens upon dozens of times. &#128551;

---

### Post by mörgæs on 2017-09-26
Let's see more hardware details. Please copy ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post the results in CODE tags.

---

### Post by kelltech on 2017-09-26
You're not going to believe this, but that code returns a blank line in the terminal. So I tried 
```
sudo lshw > hardware.txt
```

Except that also returned a blank line :(

---

### Post by oldos2er on 2017-09-26
But it created the file hardware.txt, right? Could you please copy and paste the contents of hardware.txt into a post here?

---

### Post by kelltech on 2017-09-26
> **mörgæs said:**
> Let's see more hardware details. Please copy ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post the results in CODE tags.

My mistake, I was expecting output in the terminal. Here's the lshw:

```
computer
    description: Notebook
    product: N85_N87,HJ,HJ1,HK1 (Not Applicable)
    vendor: Notebook
    version: Not Applicable
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=Not Applicable sku=Not Applicable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: N85_N87,HJ,HJ1,HK1
       vendor: Notebook
       physical id: 0
       version: Not Applicable
       serial: [REMOVED]
       slot: Not Applicable
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.05.15RLS1
          date: 07/05/2017
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int5printscreen int9keyboard int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: SODIMM DDR4 Synchronous 2400 MHz (0.4 ns)
             product: M471A1K43CB1-CRC
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: 17
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 18
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 19
          slot: L3 Cache
          size: 6MiB
          capacity: 6MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 1a
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
          serial: [REMOVED]
          slot: U3E1
          size: 900MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Skylake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:e000(size=4096) memory:de000000-df0fffff ioport:c0000000(size=301989888)
           *-display UNCLAIMED
                description: 3D controller
                product: GP107M [GeForce GTX 1050 Ti Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:128 memory:dd000000-ddffffff memory:a0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Sunrise Point-H USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:123 memory:df410000-df41ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-19-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: Chicony USB 2.0 Camera
                   vendor: SunplusIT Inc
                   physical id: 2
                   bus info: usb@1:2
                   version: 36.01
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.10
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2 UNCLAIMED
                   description: Generic USB device
                   product: EgisTec_ES603
                   vendor: EgisTec
                   physical id: 7
                   bus info: usb@1:7
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: b
                   bus info: usb@1:b
                   version: 24.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-19-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: Sunrise Point-H Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:df42e000-df42efff
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:136 memory:df42d000-df42dfff
        *-storage
             description: SATA controller
             product: Sunrise Point-H SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:125 memory:df428000-df429fff memory:df42c000-df42c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:df42b000-df42b7ff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:70000000-701fffff ioport:70200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:df300000-df3fffff
           *-generic
                description: Unassigned class
                product: RTL8411B PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:124 memory:df315000-df315fff memory:df300000-df30ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: enp3s0f1
                version: 12
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:127 ioport:d000(size=256) memory:df314000-df314fff memory:df310000-df313fff
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:df200000-df2fffff
           *-network
                description: Wireless interface
                product: Wireless 8265 / 8275
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 78
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-19-generic firmware=22.391740.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:137 memory:df200000-df201fff
        *-pci:4
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:df100000-df1fffff
           *-storage
                description: Non-Volatile memory controller
                product: Sandisk Corp
                vendor: Sandisk Corp
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:df100000-df103fff
        *-isa
             description: ISA bridge
             product: Sunrise Point-H LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-H PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
             resources: memory:df424000-df427fff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:138 memory:df420000-df423fff memory:df400000-df40ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-H SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df42a000-df42a0ff ioport:f040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 0001
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=29ce64b5
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 20GiB
                capacity: 20GiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2017-09-24 20:31:46 filesystem=ext3 label=test modified=2017-09-26 15:59:10 mounted=2017-09-26 15:56:31 state=clean
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: [REMOVED]
                size: 911GiB
                capacity: 911GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2017-09-24 20:31:53 filesystem=ext3 label=storage lastmountpoint=/media/irish/storage modified=2017-09-26 16:00:24 mounted=2017-09-26 16:00:24 state=clean


```

---

### Post by mörgæs on 2017-09-28
You have the latest Nvidia graphics which sometimes needs special settings. I suggest that you search through Oldfreds posts; chances are that he has already posted a solution for the problem. [Here]("https://ubuntuforums.org/showthread.php?t=2350059") is for example a thread dealing with related hardware.

---

### Post by kelltech on 2017-09-30
> **mörgæs said:**
> I suggest that you search through Oldfreds posts; chances are that he has already posted a solution for the problem. [Here]("https://ubuntuforums.org/showthread.php?t=2350059") is for example a thread dealing with related hardware.

Thank you very much for the information, things are running much better.

By the way, I have friends in Iceland and have been to your city a few times. I love it, a beautiful country and good people there!!

---

### Post by mörgæs on 2017-10-01
Good that it helped. You are always welcome in the north :-)

---

