---
title: "Ubuntu 18.04 system periodically hard freezing"
date: 2019-11-29
forum: New to Ubuntu
---

### Post by vurnhat on 2019-11-29
I installed Ubuntu 18.04 off usb flash drive iso to use Rstudio.  I did the bare bones install rather than the version with suggested packages.  Ubuntu was freezing periodically from the start, every 1-2 hours, typically after going AFK for about 5+ min and returning to an unresponsive keyboard/mouse.  Rstudio was crashing periodically.  Issue was GPU rendering.  I switched it to software rending and crash stopped.  Then I updated GPU drivers using sudo ubuntu-drivers autoinstall.  Before autoinstall, when I ran "sudo apt purge nvidia-*", the system froze as well.  After searching a few forums on what may solve my issue with system freezing, I've come across various solutions specific to hardware I don't have like an AMD GPU.  I've realized two common themes though, the kernel crash dump solution ([https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html](https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html)) as well as the logs application solution.  The logs application solution seems much faster so i'm trying that here first, but would love to know the ideal way to troubleshoot this issue.

Here is the "important" output from my Ubuntu 18.04 Logs Application:
10:15:26 AM bluetoothd: Failed to set mode: Blocked through rfkill (0x12)
10:15:26 AM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
10:15:25 AM pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
10:15:16 AM bluetoothd: Failed to set mode: Blocked through rfkill (0x12)
10:15:16 AM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
10:15:15 AM hpfax: [1435]: error: Failed to create /var/spool/cups/tmp/.hplip
10:15:11 AM gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
10:15:10 AM kernel: PKCS#7 signature not signed with a trusted key
10:15:10 AM bluetoothd: Failed to set mode: Blocked through rfkill (0x12)
10:15:10 AM kernel: PKCS#7 signature not signed with a trusted key
10:15:10 AM kernel: Couldn't get size: 0x800000000000000e
10:15:10 AM kernel: MODSIGN: Couldn't get UEFI db list
10:15:10 AM kernel: Couldn't get size: 0x800000000000000e

Thank you for any help!

---

### Post by vurnhat on 2019-11-30
If my post is lacking some essential info, any help on what to further include would be appreciated.  I'm so new i'm not even sure what I could further include that would help solicit some support on the question.

Thanks.

---

### Post by mörgæs on 2019-12-01
Hi, welcome to the fora.
A good starting point is a hardware description. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by vurnhat on 2019-12-01
Thank you for the help!

```

[COLOR=#000000]
computer[/COLOR]    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Z370 Extreme4
       vendor: ASRock
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.10
          date: 10/12/2017
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
             product: CMK16GX4M2D3200C16
             vendor: AMI
             physical id: 1
             serial: [REMOVED]
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
             product: CMK16GX4M2D3200C16
             vendor: AMI
             physical id: 3
             serial: [REMOVED]
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
     *-cache:0
          description: L1 cache
          physical id: 16
          slot: L1 Cache
          size: 384KiB
          capacity: 384KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 17
          slot: L2 Cache
          size: 1536KiB
          capacity: 1536KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 18
          slot: L3 Cache
          size: 12MiB
          capacity: 12MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8700K CPU @ 3.70GHz
          vendor: Intel Corp.
          physical id: 19
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8700K CPU @ 3.70GHz
          serial: [REMOVED]
          slot: CPUSocket
          size: 4281MHz
          capacity: 4500MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=6 enabledcores=6 threads=12
     *-pci
          description: Host bridge
          product: 8th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:de000000-df0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GP104 [GeForce GTX 1080]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:144 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GP104 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:df080000-df083fff
        *-usb
             description: USB controller
             product: 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:121 memory:df430000-df43ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-36-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Human interface device
                   product: NZXT USB Device
                   vendor: NZXT.-Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 2.00
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: USB hub
                   product: AS2107
                   vendor: ASMedia
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.01
                   serial: [REMOVED]
                   capabilities: usb-2.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
              *-usb:2
                   description: USB hub
                   product: General Purpose USB Hub
                   vendor: Texas Instruments, Inc.
                   physical id: 4
                   bus info: usb@1:4
                   version: 1.01
                   capabilities: usb-1.10
                   configuration: driver=hub slots=3 speed=12Mbit/s
                 *-usb:0
                      description: Human interface device
                      product: SteelSeries Siberia 800
                      vendor: SteelSeries
                      physical id: 2
                      bus info: usb@1:4.2
                      version: 2.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
                 *-usb:1
                      description: Audio device
                      product: SteelSeries Siberia 800
                      vendor: SteelSeries
                      physical id: 3
                      bus info: usb@1:4.3
                      version: 1.00
                      capabilities: usb-1.10 audio-control
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-usb:3
                   description: Printer
                   product: HL-L2320D series
                   vendor: Brother
                   physical id: 6
                   bus info: usb@1:6
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=480Mbit/s
              *-usb:4
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: PixArt
                   physical id: 7
                   bus info: usb@1:7
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:5
                   description: Bluetooth wireless interface
                   product: CSR8510 A10
                   vendor: Cambridge Silicon Radio, Ltd
                   physical id: 9
                   bus info: usb@1:9
                   version: 88.91
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-36-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=10 speed=5000Mbit/s
              *-usb
                   description: USB hub
                   product: AS2107
                   vendor: ASMedia
                   physical id: 7
                   bus info: usb@2:7
                   version: 0.01
                   serial: [REMOVED]
                   capabilities: usb-3.00
                   configuration: driver=hub maxpower=8mA slots=4 speed=5000Mbit/s
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 200 Series PCH Thermal Subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:df44e000-df44efff
        *-communication
             description: Communication controller
             product: 200 Series PCH CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:132 memory:df44d000-df44dfff
        *-storage
             description: SATA controller
             product: 200 Series PCH SATA controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:130 memory:df448000-df449fff memory:df44c000-df44c0ff ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:df44b000-df44b7ff
        *-pci:1
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #17
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:df300000-df3fffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM961/PM961
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:134 memory:df300000-df303fff
        *-pci:2
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:3
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:df200000-df2fffff
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:133 ioport:d050(size=8) ioport:d040(size=4) ioport:d030(size=8) ioport:d020(size=4) ioport:d000(size=32) memory:df200000-df2001ff
        *-pci:4
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:df100000-df1fffff
           *-usb
                description: USB controller
                product: ASMedia Technology Inc.
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:df100000-df107fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.0.0-36-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 5.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb
                      description: USB hub
                      product: USB 2.0 Hub
                      vendor: Terminus Technology Inc.
                      physical id: 2
                      bus info: usb@3:2
                      version: 1.11
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                    *-usb:0
                         description: Mouse
                         product: ZOWIE Gaming mouse
                         vendor: Kingsis Peripherals
                         physical id: 1
                         bus info: usb@3:2.1
                         version: 0.01
                         capabilities: usb-2.00
                         configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                    *-usb:1
                         description: Keyboard
                         product: USB Gaming Keyboard
                         vendor: E-Signal
                         physical id: 2
                         bus info: usb@3:2.2
                         version: 1.00
                         capabilities: usb-2.00
                         configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.0.0-36-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 5.00
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:5
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19
        *-pci:6
             description: PCI bridge
             product: 200 Series PCH PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-isa
             description: ISA bridge
             product: Z370 Chipset LPC/eSPI Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: 200 Series/Z370 Chipset Family Power Management Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:df444000-df447fff
        *-multimedia
             description: Audio device
             product: 200 Series PCH HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:143 memory:df440000-df443fff memory:df420000-df42ffff
        *-serial UNCLAIMED
             description: SMBus
             product: 200 Series/Z370 Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df44a000-df44a0ff ioport:f000(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 00
             serial: [REMOVED]
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.2-4 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s [COLOR=#000000]             resources: irq:131 memory:df400000-df41ffff
[/COLOR]

```

---

### Post by mörgæs on 2019-12-01
With hardware this new I would not struggle with stale software like 18.04. Better to go straight to a clean install of 19.10. Run it for a while with the default Nvidia software and see how it goes.

A lot of [BIOS updates]("http://www.asrock.com/mb/Intel/Z370%20Extreme4/index.asp#BIOS") are available. Next step will be taking a look at them.

---

### Post by vurnhat on 2019-12-03
I went with 18.04 because it's the most recent stable supported version of Ubuntu, so my thinking was that it's best for learning R and python programming based on an assumption that it'd be most commonly used in the git community.  Let me know if this was misguided.

So I'll install both the BIOS updates and Ubuntu 19.10, I suppose.  Thank you so much for pointing me in the right direction.  I have a 32gb flash drive that i've reformatted at just "FAT32" and erased all the files from it.  I've downloaded the most recent BIOS release from the page you linked.  Am I supposed to grab the instant flash version I assume?  I read the how-to page located here:
[http://www.asrock.com/support/BIOSIG.asp?cat=BIOS9](http://www.asrock.com/support/BIOSIG.asp?cat=BIOS9)

Seems very easy and I think the BIOS are independent of OS so I can just do that update now with the flash drive I've emptied, reformated to FAT32, and loaded the unzipped BIOS file to?

Thanks again for all the help!  I'll get through this BIOS install tonight and then hopefully the OS tomorrow if I find some time.  My windows partition is still on my harddrive and I can see it in files browser, but it's no longer a boot option after i reformatted my old Ubuntu so i'll need to deal with that after all this as well... :/

---

### Post by vurnhat on 2019-12-03
I rolled the dice and updated my BIOS successfully and watched a video about the Ubuntu differences.  I'll update to Ubuntu 19.10 tomorrow morning and see how that goes.  Thanks.

---

### Post by mörgæs on 2019-12-04
All recent Buntu releases come with an R version available in the repository. New Buntus contain new version of all applications (R, Gimp, Libreoffice...) and provide better support for new hardware.

[Here]("https://packages.ubuntu.com/search?keywords=r-base") you can see which R packages are available. Being an R programmer myself I would not be satisfied with the default 3.4.4 delivered in 18.04.

I suggest a clean install of 19.10, not an upgrade in place. Just the plain installation without tweaking drivers to begin with.

Don't trust anyone's claim about this and that being 'stable' but test a number of alternatives on your own hardware (like we do now).

---

