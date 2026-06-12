---
title: "I am new, and I can't get my desktop to run correctly"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by anthony68 on 2015-06-20
EDIT I ended up following this link. [http://ubuntuforums.org/showthread.php?t=2278518](http://ubuntuforums.org/showthread.php?t=2278518)

and I was up and running. Thank the guys below for the information. 




I am running an i7-5820k nVidia 970gtx setup.

I installed Ubuntu 14.04. Everything came up and running. However, everything runs very sluggish and slow. Also I am having a lot of trouble installing my 970gtx graphics card. I have tried everything from every forum you can link me to but it doesn't seem to work. I keep getting stuck at the login screen. I believe it is because I am not properly removing and installing the driver. I have copy and pasted and modified commands for my case for the past 2 days now. I can not get my machine to run smoothly. Can anyone please give me some newbie help.

Thank You! Cheers!!!

Edit: Also every time I make a play on installing a graphics driver, I have to reinstall the OS because I don't know how to (if there is a way) to remove the driver without logging in. 

And not sure why the sudo ubuntu-drivers devices command is not returning anything.

---

### Post by wildmanne39 on 2015-06-20
Please run these commands in the terminal and post the output here between code tags using the # button.
```
sudo lshw
```
```
lspci -nnk | grep -iA2 vga
```
Thanks

---

### Post by anthony68 on 2015-06-20
Hi Wild Man! Thank you for the response. It is much appreciated right now. I ran those commands.

```


08:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:13c2] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8508]
08:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbb] (rev a1)



```

This was returned from vga. 

The other listed everything. What exactly am I looking for?

Thank you again!

---

### Post by wildmanne39 on 2015-06-20
That command should have shown the driver being used with your video card even if it is just the generic driver, so I am wndering why one is not present.

I wanted you to post everything that command put out so we can see your specs and that will give us an idea of what is going on.

There are other people better with this issue then I am, I mainly work with wireless issues.
Thanks

---

### Post by anthony68 on 2015-06-20
Thanks! Sorry would have done this earlier but didn't know if putting something this long was ok. But here it goes.

```

description: Desktop Computer
    product: All Series (All)
    vendor: ASUS
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=ASUS MB sku=All uuid=40BCC694-21C0-D311-BBB5-382C4A6E1895
  *-core
       description: Motherboard
       product: X99-A
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 140931900103584
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0216
          date: 08/29/2014
          size: 64KiB
          capacity: 15MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 5d
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 0
             serial: NO DIMM
             slot: DIMM_A1
        *-bank:1
             description: DIMM Synchronous [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: DIMM_A2
        *-bank:2
             description: DIMM Synchronous [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 2
             serial: NO DIMM
             slot: DIMM_B1
        *-bank:3
             description: DIMM Synchronous [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: DIMM_B2
        *-bank:4
             description: DIMM Synchronous 2400 MHz (0.4 ns)
             product: BLS8G4D240FSA.M16FA
             vendor: Undefined
             physical id: 4
             serial: A1109F90
             slot: DIMM_C1
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:5
             description: DIMM Synchronous [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 5
             serial: NO DIMM
             slot: DIMM_C2
        *-bank:6
             description: DIMM Synchronous 2400 MHz (0.4 ns)
             product: BLS8G4D240FSA.M16FA
             vendor: Undefined
             physical id: 6
             serial: A1109F91
             slot: DIMM_D1
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:7
             description: DIMM Synchronous [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 7
             serial: NO DIMM
             slot: DIMM_D2
     *-cache:0
          description: L1 cache
          physical id: 69
          slot: CPU Internal L1
          size: 384KiB
          capacity: 384KiB
          capabilities: internal write-back
     *-cache:1
          description: L2 cache
          physical id: 6a
          slot: CPU Internal L2
          size: 1536KiB
          capacity: 1536KiB
          capabilities: internal write-back unified
     *-cache:2
          description: L3 cache
          physical id: 6b
          slot: CPU Internal L3
          size: 15MiB
          capacity: 15MiB
          capabilities: internal write-back unified
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 6c
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz
          slot: SOCKET 2011
          size: 2874MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=6 enabledcores=6 threads=12
     *-pci
          description: Host bridge
          product: Haswell-E DMI2
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Haswell-E PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64
        *-pci:1
             description: PCI bridge
             product: Haswell-E PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:65
        *-pci:2
             description: PCI bridge
             product: Haswell-E PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:66
        *-pci:3
             description: PCI bridge
             product: Haswell-E PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:67
        *-pci:4
             description: PCI bridge
             product: Haswell-E PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:68
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Haswell-E Address Map, VTd_Misc, System Management
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Haswell-E Hot Plug
             vendor: Intel Corporation
             physical id: 5.1
             bus info: pci@0000:00:05.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress msi cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Haswell-E RAS, Control Status and Global Errors
             vendor: Intel Corporation
             physical id: 5.2
             bus info: pci@0000:00:05.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: PIC
             product: Haswell-E I/O Apic
             vendor: Intel Corporation
             physical id: 5.4
             bus info: pci@0000:00:05.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress pm io_x_-apic bus_master cap_list
             configuration: latency=0
             resources: memory:fb23e000-fb23efff
        *-generic:4 UNCLAIMED
             description: Unassigned class
             product: Wellsburg SPSR
             vendor: Intel Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress pm bus_master cap_list
             configuration: latency=0
        *-storage:0
             description: SATA controller
             product: Wellsburg sSATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 11.4
             bus info: pci@0000:00:11.4
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:80 ioport:f130(size=8) ioport:f120(size=4) ioport:f110(size=8) ioport:f100(size=4) ioport:f040(size=32) memory:fb23d000-fb23d7ff
        *-usb:0
             description: USB controller
             product: Wellsburg USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:23 memory:fb220000-fb22ffff
        *-communication
             description: Communication controller
             product: Wellsburg MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:83 memory:fb23c000-fb23c00f
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I218-V
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: 38:2c:4a:6e:18:95
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.1-4 ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:82 memory:fb200000-fb21ffff memory:fb239000-fb239fff ioport:f020(size=32)
        *-usb:1
             description: USB controller
             product: Wellsburg USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fb238000-fb2383ff
        *-multimedia
             description: Audio device
             product: Wellsburg HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:84 memory:fb230000-fb233fff
        *-pci:5
             description: PCI bridge
             product: Wellsburg PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:69
        *-pci:6
             description: PCI bridge
             product: Wellsburg PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:70 memory:fb100000-fb1fffff
           *-usb
                description: USB controller
                product: ASMedia Technology Inc.
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:fb100000-fb107fff
        *-pci:7
             description: PCI bridge
             product: Wellsburg PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:71 ioport:e000(size=4096) memory:fa000000-fb0fffff ioport:c0000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list
                configuration: latency=0
                resources: memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:08:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:16 memory:fb080000-fb083fff
        *-usb:2
             description: USB controller
             product: Wellsburg USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:fb237000-fb2373ff
        *-isa
             description: ISA bridge
             product: Wellsburg LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage:1
             description: SATA controller
             product: Wellsburg 6-Port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:81 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f000(size=32) memory:fb236000-fb2367ff
        *-serial UNCLAIMED
             description: SMBus
             product: Wellsburg SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fb235000-fb2350ff ioport:580(size=32)
     *-generic:0 UNCLAIMED
          description: System peripheral
          product: Haswell-E R3 QPI Link 0 & 1 Monitoring
          vendor: Intel Corporation
          physical id: b
          bus info: pci@0000:ff:0b.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:1 UNCLAIMED
          description: Performance counters
          product: Haswell-E R3 QPI Link 0 & 1 Monitoring
          vendor: Intel Corporation
          physical id: b.1
          bus info: pci@0000:ff:0b.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:2 UNCLAIMED
          description: Performance counters
          product: Haswell-E R3 QPI Link 0 & 1 Monitoring
          vendor: Intel Corporation
          physical id: b.2
          bus info: pci@0000:ff:0b.2
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:3 UNCLAIMED
          description: System peripheral
          product: Haswell-E Unicast Registers
          vendor: Intel Corporation
          physical id: c
          bus info: pci@0000:ff:0c.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:4 UNCLAIMED
          description: System peripheral
          product: Haswell-E Unicast Registers
          vendor: Intel Corporation
          physical id: c.1
          bus info: pci@0000:ff:0c.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:5 UNCLAIMED
          description: System peripheral
          product: Haswell-E Unicast Registers
          vendor: Intel Corporation
          physical id: c.2
          bus info: pci@0000:ff:0c.2
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:6 UNCLAIMED
          description: System peripheral
          product: Haswell-E Unicast Registers
          vendor: Intel Corporation
          physical id: c.3
          bus info: pci@0000:ff:0c.3
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:7 UNCLAIMED
          description: System peripheral
          product: Haswell-E Unicast Registers
          vendor: Intel Corporation
          physical id: c.4
          bus info: pci@0000:ff:0c.4
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:8 UNCLAIMED
          description: System peripheral
          product: Haswell-E Unicast Registers
          vendor: Intel Corporation
          physical id: c.5
          bus info: pci@0000:ff:0c.5
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:9 UNCLAIMED
          description: System peripheral
          product: Haswell-E Buffered Ring Agent
          vendor: Intel Corporation
          physical id: f
          bus info: pci@0000:ff:0f.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:10 UNCLAIMED
          description: System peripheral
          product: Haswell-E Buffered Ring Agent
          vendor: Intel Corporation
          physical id: f.1
          bus info: pci@0000:ff:0f.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:11 UNCLAIMED
          description: System peripheral
          product: Haswell-E System Address Decoder & Broadcast Registers
          vendor: Intel Corporation
          physical id: f.4
          bus info: pci@0000:ff:0f.4
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:12 UNCLAIMED
          description: System peripheral
          product: Haswell-E System Address Decoder & Broadcast Registers
          vendor: Intel Corporation
          physical id: f.5
          bus info: pci@0000:ff:0f.5
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:13 UNCLAIMED
          description: System peripheral
          product: Haswell-E System Address Decoder & Broadcast Registers
          vendor: Intel Corporation
          physical id: f.6
          bus info: pci@0000:ff:0f.6
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:14 UNCLAIMED
          description: System peripheral
          product: Haswell-E PCIe Ring Interface
          vendor: Intel Corporation
          physical id: 10
          bus info: pci@0000:ff:10.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:15 UNCLAIMED
          description: Performance counters
          product: Haswell-E PCIe Ring Interface
          vendor: Intel Corporation
          physical id: 10.1
          bus info: pci@0000:ff:10.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:16 UNCLAIMED
          description: System peripheral
          product: Haswell-E Scratchpad & Semaphore Registers
          vendor: Intel Corporation
          physical id: 10.5
          bus info: pci@0000:ff:10.5
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:17 UNCLAIMED
          description: Performance counters
          product: Haswell-E Scratchpad & Semaphore Registers
          vendor: Intel Corporation
          physical id: 10.6
          bus info: pci@0000:ff:10.6
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:18 UNCLAIMED
          description: System peripheral
          product: Haswell-E Scratchpad & Semaphore Registers
          vendor: Intel Corporation
          physical id: 10.7
          bus info: pci@0000:ff:10.7
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:19 UNCLAIMED
          description: System peripheral
          product: Haswell-E Home Agent 0
          vendor: Intel Corporation
          physical id: 12
          bus info: pci@0000:ff:12.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:20 UNCLAIMED
          description: Performance counters
          product: Haswell-E Home Agent 0
          vendor: Intel Corporation
          physical id: 12.1
          bus info: pci@0000:ff:12.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:21 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Target Address, Thermal & RAS Registers
          vendor: Intel Corporation
          physical id: 13
          bus info: pci@0000:ff:13.0
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:22 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Target Address, Thermal & RAS Registers
          vendor: Intel Corporation
          physical id: 13.1
          bus info: pci@0000:ff:13.1
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:23 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder
          vendor: Intel Corporation
          physical id: 13.2
          bus info: pci@0000:ff:13.2
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:24 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder
          vendor: Intel Corporation
          physical id: 13.3
          bus info: pci@0000:ff:13.3
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:25 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder
          vendor: Intel Corporation
          physical id: 13.4
          bus info: pci@0000:ff:13.4
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:26 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder
          vendor: Intel Corporation
          physical id: 13.5
          bus info: pci@0000:ff:13.5
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:27 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO Channel 0/1 Broadcast
          vendor: Intel Corporation
          physical id: 13.6
          bus info: pci@0000:ff:13.6
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:28 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO Global Broadcast
          vendor: Intel Corporation
          physical id: 13.7
          bus info: pci@0000:ff:13.7
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:29 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 0 Thermal Control
          vendor: Intel Corporation
          physical id: 14
          bus info: pci@0000:ff:14.0
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:30 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 1 Thermal Control
          vendor: Intel Corporation
          physical id: 14.1
          bus info: pci@0000:ff:14.1
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:31 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 0 ERROR Registers
          vendor: Intel Corporation
          physical id: 14.2
          bus info: pci@0000:ff:14.2
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:32 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 1 ERROR Registers
          vendor: Intel Corporation
          physical id: 14.3
          bus info: pci@0000:ff:14.3
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:33 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO (VMSE) 0 & 1
          vendor: Intel Corporation
          physical id: 14.6
          bus info: pci@0000:ff:14.6
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:34 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO (VMSE) 0 & 1
          vendor: Intel Corporation
          physical id: 14.7
          bus info: pci@0000:ff:14.7
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:35 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 2 Thermal Control
          vendor: Intel Corporation
          physical id: 15
          bus info: pci@0000:ff:15.0
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:36 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 3 Thermal Control
          vendor: Intel Corporation
          physical id: 15.1
          bus info: pci@0000:ff:15.1
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:37 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 2 ERROR Registers
          vendor: Intel Corporation
          physical id: 15.2
          bus info: pci@0000:ff:15.2
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:38 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 0 Channel 3 ERROR Registers
          vendor: Intel Corporation
          physical id: 15.3
          bus info: pci@0000:ff:15.3
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:39 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 1 Target Address, Thermal & RAS Registers
          vendor: Intel Corporation
          physical id: 16
          bus info: pci@0000:ff:16.0
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:40 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO Channel 2/3 Broadcast
          vendor: Intel Corporation
          physical id: 16.6
          bus info: pci@0000:ff:16.6
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:41 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO Global Broadcast
          vendor: Intel Corporation
          physical id: 16.7
          bus info: pci@0000:ff:16.7
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:42 UNCLAIMED
          description: System peripheral
          product: Haswell-E Integrated Memory Controller 1 Channel 0 Thermal Control
          vendor: Intel Corporation
          physical id: 17
          bus info: pci@0000:ff:17.0
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0
     *-generic:43 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO (VMSE) 2 & 3
          vendor: Intel Corporation
          physical id: 17.4
          bus info: pci@0000:ff:17.4
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:44 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO (VMSE) 2 & 3
          vendor: Intel Corporation
          physical id: 17.5
          bus info: pci@0000:ff:17.5
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:45 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO (VMSE) 2 & 3
          vendor: Intel Corporation
          physical id: 17.6
          bus info: pci@0000:ff:17.6
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:46 UNCLAIMED
          description: System peripheral
          product: Haswell-E DDRIO (VMSE) 2 & 3
          vendor: Intel Corporation
          physical id: 17.7
          bus info: pci@0000:ff:17.7
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:47 UNCLAIMED
          description: System peripheral
          product: Haswell-E Power Control Unit
          vendor: Intel Corporation
          physical id: 1e
          bus info: pci@0000:ff:1e.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:48 UNCLAIMED
          description: System peripheral
          product: Haswell-E Power Control Unit
          vendor: Intel Corporation
          physical id: 1e.1
          bus info: pci@0000:ff:1e.1
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:49 UNCLAIMED
          description: System peripheral
          product: Haswell-E Power Control Unit
          vendor: Intel Corporation
          physical id: 1e.2
          bus info: pci@0000:ff:1e.2
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:50 UNCLAIMED
          description: System peripheral
          product: Haswell-E Power Control Unit
          vendor: Intel Corporation
          physical id: 1e.3
          bus info: pci@0000:ff:1e.3
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:51 UNCLAIMED
          description: System peripheral
          product: Haswell-E Power Control Unit
          vendor: Intel Corporation
          physical id: 1e.4
          bus info: pci@0000:ff:1e.4
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:52 UNCLAIMED
          description: System peripheral
          product: Haswell-E VCU
          vendor: Intel Corporation
          physical id: 1f
          bus info: pci@0000:ff:1f.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-generic:53 UNCLAIMED
          description: System peripheral
          product: Haswell-E VCU
          vendor: Intel Corporation
          physical id: 1f.2
          bus info: pci@0000:ff:1f.2
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG SSD 830
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 1B1Q
             serial: S0VTNYABA00953
             size: 59GiB (64GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=c0aa1aca
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 2a1af8bb-2833-884c-a172-e453aa3cf57d
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-11-24 19:07:59 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 59GiB
                capacity: 59GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 15GiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 15GiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 11GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 15GiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: BB6Q
             serial: S1DHNSAF778535W
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=6e2887ee
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: be2d-42fd
                size: 348MiB
                capacity: 350MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-05-21 23:54:41 filesystem=ntfs label=System Reserved modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: 04f5d496-fe6d-344d-9c0a-f1a81f58ec01
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2015-05-21 23:54:52 filesystem=ntfs state=clean
     *-scsi:2
          physical id: 3
          logical name: scsi6
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2002FAEX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 1D05
             serial: WD-WMAY02511852
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=7b93ced5
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                version: 3.1
                serial: e8d0c4a5-f465-cd41-a300-caca4c87d7c7
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-11-27 02:27:04 filesystem=ntfs label=WD SATA 3.0 2TB state=clean
     *-scsi:3
          physical id: 4
          logical name: scsi8
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-RE  WH12LS38
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:4
          physical id: 5
          logical name: scsi9
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-222AB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sr1
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

```

Edit: It scrolls :) haha didn't know it would. Really appreciate it wild man. I am switching over from windows and really want to jump into the development world. I studied physics in school and forgot how interested I really was in all of this stuff. So figured why not jump in and learn it all on an open source UNIX system where I can hate myself for a month but learn a ton more.

---

### Post by wildmanne39 on 2015-06-20
Please tell us what drivers you have installed for video card and from where with links if possible. Did you try any drivers from additional drivers?
Thanks

---

### Post by anthony68 on 2015-06-20
Nothing showed up in additional drivers. 

[http://askubuntu.com/questions/561295/how-to-use-nvidia-gtx-970-gpu](http://askubuntu.com/questions/561295/how-to-use-nvidia-gtx-970-gpu) I have tried this, everything on the page...

I've tried a bunch of things with PPA. 

[http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/) this page showed a walkthrough for nvidia 343.22

Everything keeps giving me a login problem. Screen goes black and then goes back to the login. 

Truthfully I tried so many things before joining this forum, I don't even know how to reiterate what I've been doing the past couple of days. I've decided before I dig too deep and really screw something up I should just ask. Thank you in advance again.

EDIT: The only thing I have not done, is download drivers from nvidia and try to install those. I keep reading that is not the right way to do it.

---

### Post by SeijiSensei on 2015-06-20
This should help:

[http://ubuntuforums.org/showthread.php?t=2278518](http://ubuntuforums.org/showthread.php?t=2278518)

---

### Post by wildmanne39 on 2015-06-20
Looks like version 352.21 was just released on the 15th of June.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by anthony68 on 2015-06-20
I am going to try both. Will get back after they are finished. Thanks a bunch guys. And I am thinking I've seen that post Sieji. It might have been one of the first ones I've seen but will give it a try. Maybe I didn't do something right the first time. 

If it doesn't work I will try downloading that new release Wild. 

Thanks in advance guys. Will be back with updates.

---

### Post by wildmanne39 on 2015-06-20
Remember if the first one does not work you must completely remove it before installing the next one.

---

### Post by anthony68 on 2015-06-20
Thanks guys. Everything seems to be working for now. The Link you sent me worked perfect. I don't know how I missed that.

---

### Post by anthony68 on 2015-06-20
Wild Man thanks for getting back to me so many times!

---

### Post by wildmanne39 on 2015-06-20
Your welcome! it is a lot easier to resolve issues once we have the information needed that is why those two commands were so important.
Enjoy!

---

