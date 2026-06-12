---
title: "Ubuntu stop working - the mouse cursor does not move"
date: 2019-12-08
forum: New to Ubuntu
---

### Post by pawellepko on 2019-12-08
Hello,

I have had a problem with Ubuntu's crashing for a long time. The problem most often occurs when browsing the Internet in Firefox and is manifested by a complete blockade of the system - the mouse cursor and keyboard do not respond and I need to restart by holding the power button. Is there any solution for this?

Below is the configuration of my system:
```

usr/bin/dbus-run-session  /usr/bin/gnome-session-custom-session
/usr/bin/gnome-session


                        lscpu:
Architektura:           x86_64
Tryb(y) pracy CPU:      32-bit, 64-bit
Kolejno&#347;&#263; bajtów:       Little Endian
CPU:                    4
Lista aktywnych CPU:    0-3
W&#261;tków na rdze&#324;:        1
Rdzeni na gniazdo:      4
Gniazd:                 1
W&#281;z&#322;ów NUMA:            1
ID producenta:          AuthenticAMD
Rodzina CPU:            22
Model:                  0
Nazwa modelu:           AMD A4-5000 APU with Radeon(TM) HD Graphics
Wersja:                 1
CPU MHz:                827.725
CPU max MHz:            1500,0000
CPU min MHz:            800,0000
BogoMIPS:               2994.18
Wirtualizacja:          AMD-V
Cache L1d:              32K
Cache L1i:              32K
Cache L2:               2048K
Procesory w&#281;z&#322;a NUMA 0: 0-3
Flagi:                  fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_llc hw_pstate proc_feedback ssbd vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold overflow_recov

                        lshw:

WARNING: you should run this program as super-user.
pawel-satellite-c55d-a-13g  
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5393MiB
     *-cpu
          product: AMD A4-5000 APU with Radeon(TM) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1011MHz
          capacity: 1500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_llc hw_pstate proc_feedback ssbd vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold overflow_recov cpufreq
..
..
..
 *-network
       description: Ethernet interface
       physical id: 1
       logical name: wwx001e101f0000
       serial: 00:1e:10:1f:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device ip=46.113.117.50 link=yes multicast=yes

```

---

### Post by TheFu on 2019-12-08
Firefox is a RAM hog, so my first idea is that the system is running out of RAM. 
**free -hm**
will show the amount of RAM and swap the system has and what is being used.  Using **top** will stop the CPU using processes and RAM use.

Often, when a system seems to be locked up, it is just the GUI.  By switching to a different console, you'll be able to login, see what the RAM use looks like (free) and see the CPU/RAM for processes using **top**.  To switch consoles, press <cntl><alt>-1 or <c><a>-2 ... or 3, 4, 5, 6 ... <c><a>-7 is the normal GUI console where X11 or Wayland run.  If the system is truly locked up, then changing consoles won't work.  That seldom actually happens, unless there is some hardware failure or RAM+swap is completely used up.

There are many different ways to get a summary of the hardware in a system.  For example:
```
$ inxi -IC
CPU:       Quad core Intel Core i5-8250U (-HT-MCP-) cache: 6144 KB 
           clock speeds: max: 3400 MHz 1: 716 MHz 2: 721 MHz 3: 717 MHz
           4: 708 MHz 5: 703 MHz 6: 714 MHz 7: 712 MHz 8: 702 MHz
Info:      Processes: 376 Uptime: 6 days Memory: 3485.6/7859.6MB
           Client: Shell (bash) inxi: 2.2.35 
```
shows I'm using 3.4G of 8G RAM.

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           7.7G        3.0G        924M        451M        3.8G        3.8G
Swap:          4.5G        1.4G        3.1G
```
shows 3.0G of real-RAM used, 1.4G of swap.  If the "free" column for both Mem and Swap get low, expect a system crash.  Buffers/cache will be freed to be used a RAM, when that becomes advantageous, so the system has 3.8G of buffers that will be used if programs demand it.  As more swap is used, the system should "feel" slower. This is feedback to the user to check on RAM use and release some ... i.e. close big programs.
Buffers are used by network and storage processes to improve disk and network performance.

Assuming this explains things, you'll be able to take steps before the GUI appears locks up.
But it might be something else like a GPU driver or some hardware failure.  The system log files should have warnings and errors before a crash occurs.

---

### Post by pawellepko on 2019-12-08
```
inix -IC:
CPU:       Quad core AMD A4-5000 APU with Radeon HD Graphics (-MCP-) 
           cache: 2048 KB
           clock speeds: max: 1500 MHz 1: 1035 MHz 2: 877 MHz 3: 915 MHz
           4: 904 MHz
Info:      Processes: 227 Uptime: 25 min Memory: 1390.5/5393.7MB
           Client: Shell (bash) inxi: 2.3.56 
```


```
free -hm:
              razem       u&#380;yte       wolne    dzielone   buf/cache    dost&#281;pne
Pami&#281;&#263;:        5,3G        1,3G        3,0G         56M        989M        3,7G
Wymiana:        2,0G          0B        2,0G
```

---

### Post by pawellepko on 2019-12-08
```
computer
    description: Notebook
    product: SATELLITE C55D-A-13G (PSCH2E)
    vendor: TOSHIBA
    version: PSCH2E-00X01GPL
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=Kabini sku=PSCH2E uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PT10AN
       vendor: AMD
       physical id: 0
       version: Base Board Version
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: 1.30
          date: 05/21/2014
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb uefi
     *-cpu
          description: CPU
          product: AMD A4-5000 APU with Radeon(TM) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD A4-5000 APU with Radeon(TM) HD Graphics
          serial: [REMOVED]
          slot: Socket FT1
          size: 1138MHz
          capacity: 1500MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_llc hw_pstate proc_feedback ssbd vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold overflow_recov cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1333 MHz (0,8 ns)
             product: RMT3010EC58E8F1333
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1333 MHz (0,8 ns)
             product: M471B5173BH0-YK0
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: Family 16h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Kabini [Radeon HD 8330]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:37 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:4000(size=256) memory:f0a00000-f0a3ffff memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Kabini HDMI/DP Audio
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f0a40000-f0a43fff
        *-pci:0
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0900000-f09fffff ioport:d0000000(size=268435456)
           *-display
                description: Display controller
                product: Sun PRO [Radeon HD 8570A/8570M]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:39 memory:d0000000-dfffffff memory:f0900000-f093ffff ioport:3000(size=256) memory:f0940000-f095ffff
        *-pci:1
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f0800000-f08fffff ioport:f0b00000(size=2097152)
           *-network
                description: Ethernet interface
                product: QCA8172 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 10
                serial: [REMOVED]
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
                resources: irq:31 memory:f0800000-f083ffff ioport:2000(size=128)
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0a48000-f0a49fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-37-generic xhci-hcd
                physical id: 0
                bus info: usb@5
                logical name: usb5
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-37-generic xhci-hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:32 ioport:4118(size=8) ioport:4124(size=4) ioport:4110(size=8) ioport:4120(size=4) ioport:4100(size=16) memory:f0a4e000-f0a4e3ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0a4d000-f0a4dfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.0.0-37-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.00
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0a4c000-f0a4c0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-37-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: HUAWEI Mobile
                   vendor: HUAWEI
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi4
                   logical name: scsi3
                   version: 1.02
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: TF CARD Storage
                      vendor: HUAWEI
                      physical id: 0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdc
                      version: 2.31
                      capabilities: removable
                      configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdc
                 *-cdrom
                      description: SCSI CD-ROM
                      product: Mass Storage
                      vendor: HUAWEI
                      physical id: 1
                      bus info: scsi@3:0.0.0
                      logical name: /dev/sr1
                      logical name: /media/pawel/PLAY ONLINE20
                      version: 2.31
                      capabilities: removable audio
                      configuration: ansiversion=2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,norock,check=r,map=n,blocksize=2048,uid=1000,gid=1000,dmode=500,fmode=400 state=mounted status=ready
                    *-medium
                         physical id: 0
                         logical name: /dev/sr1
                         logical name: /media/pawel/PLAY ONLINE20
                         capabilities: partitioned partitioned:mac
                         configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,norock,check=r,map=n,blocksize=2048,uid=1000,gid=1000,dmode=500,fmode=400 state=mounted
                       *-volume:0 UNCLAIMED
                            description: Apple partition map
                            physical id: 1
                            capacity: 1KiB
                       *-volume:1 UNCLAIMED
                            description: Apple HFS
                            physical id: 2
                            version: 4
                            serial: [REMOVED]
                            size: 33MiB
                            capacity: 33MiB
                            capabilities: hfsplus initialized
                            configuration: checked=2014-03-12 10:19:16 created=2014-03-12 09:19:16 filesystem=hfsplus lastmountedby=LSDf modified=2014-03-12 10:19:16 state=unclean
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0a4b000-f0a4bfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.0.0-37-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.00
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   physical id: 4
                   bus info: usb@4:4
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0a4a000-f0a4a0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-37-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: Flash Card Reader/Writer
                   vendor: Generic
                   physical id: 1
                   bus info: usb@2:1
                   logical name: scsi2
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.01 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Card  Reader
                      vendor: Multiple
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 1.00
                      serial: [REMOVED]
                      capabilities: removable
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:35 memory:f0a44000-f0a47fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 16h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 16h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 16h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 16h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 16h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS725050A7
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: B550
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=fef06ac7
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2019-03-14 18:48:09 filesystem=ext4 lastmountpoint=/ modified=2019-12-08 15:39:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-12-08 14:06:25 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SU-208DB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: TF01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wwx001e101f0000
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device ip=[REMOVED] link=yes multicast=yes
```

---

### Post by TheFu on 2019-12-08
6G of RAM with 0.7 given to the GPU.
2G swap, none used.

On a desktop, I like to see 4.1G of swap, since modern browsers are bloated.  Right now, it doesn't seem to be any issue.  Do you get any warning before the system locks up?

As for any Radeon GPU driver issues, someone else will need to help. I'm not qualified. Haven't used Radeon in about 6 yrs and retired that box.

For the logs, use
**sudo egrep -i 'warn|error' /var/log/*og**
to search most of them for warnings and errors which you'll need to research more.  That grep is just a starting point.  Use a pager or redirect to a log file if you like and if there are more than 1 page worth.
**sudo egrep -i 'warn|error' /var/log/*og | tee /tmp/err.log**

To help people help you, please don't just post output. Post the **command used** AND the **output**, so we know what you are showing.

Long ago, I had a desktop with a cracked motherboard that crashed all the time.  Only the hardware manufacturer had the diagnostic tools needed to determine the MB was cracked. Fortunately, it was under warranty and they replaced it.  There were different sorts of failures, but mostly crashes.  It was harder back then - it ran Windows which would crash for no reason.

---

### Post by pawellepko on 2019-12-08
I don't get any warnings before system locks up.
This is my log files:[B]
sudo egrep -i 'warn|error' /var/log/*og:
[/B][https://pastebin.com/2QFqCuz1](https://pastebin.com/2QFqCuz1)
[B]sudo egrep -i 'warn|error' /var/log/*og | tee /tmp/err.log
[/B][https://pastebin.com/9MXdyQHe](https://pastebin.com/9MXdyQHe)

---

### Post by mörgæs on 2019-12-08
Does the system also freeze using other browsers?

---

### Post by pawellepko on 2019-12-08
I use firefox all the time.

---

### Post by TheFu on 2019-12-08
How are the optical and USB storage devices used?  Lots and lots of errors in those.  Seems like some corruption exists.

---

### Post by pawellepko on 2019-12-08
One usb port is used for the mouse and the other for mobile internet (this is a small modem with a phone card)

---

### Post by TheFu on 2019-12-08
> **pawellepko said:**
> One usb port is used for the mouse and the other for mobile internet (this is a small modem with a phone card)

sr1 is showing lots and lots of errors.  That is usually a DVD or CD device.

---

### Post by pawellepko on 2019-12-08
lsblk shows that **sr1** is PLAY ONLINE20 - this is modem.

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  14,8M  1 loop /snap/gnome-characters/359
loop1    7:1    0  44,2M  1 loop /snap/gtk-common-themes/1353
loop2    7:2    0 140,7M  1 loop /snap/gnome-3-26-1604/98
loop3    7:3    0   4,2M  1 loop /snap/gnome-calculator/544
loop4    7:4    0   156M  1 loop /snap/gnome-3-28-1804/91
loop5    7:5    0  89,1M  1 loop /snap/core/7917
loop6    7:6    0  54,5M  1 loop /snap/core18/1223
loop7    7:7    0  54,5M  1 loop /snap/core18/1265
loop8    7:8    0 156,7M  1 loop /snap/gnome-3-28-1804/110
loop9    7:9    0   4,2M  1 loop /snap/gnome-calculator/536
loop10   7:10   0  42,8M  1 loop /snap/gtk-common-themes/1313
loop11   7:11   0   3,7M  1 loop /snap/gnome-system-monitor/107
loop12   7:12   0   956K  1 loop /snap/gnome-logs/81
loop13   7:13   0  89,1M  1 loop /snap/core/8039
loop14   7:14   0   3,7M  1 loop /snap/gnome-system-monitor/111
loop15   7:15   0  14,8M  1 loop /snap/gnome-characters/367
loop16   7:16   0 140,7M  1 loop /snap/gnome-3-26-1604/97
loop17   7:17   0  1008K  1 loop /snap/gnome-logs/61
sda      8:0    0 465,8G  0 disk 
&#9492;&#9472;sda1   8:1    0 465,8G  0 part /
sr0     11:0    1  1024M  0 rom  
**sr1     11:1    1   128M  0 rom  /media/pawel/PLAY ONLINE20**
```

---

### Post by pawellepko on 2019-12-08
According to the instructions on the blog [http://bogdancornianu.com/change-swap-size-in-ubuntu/](http://bogdancornianu.com/change-swap-size-in-ubuntu/) I changed the size of the swap space to 8GB - I hope this helps.

I checked the SYSRQ key combination and it doesn't work for me. On the keyboard I have the "Fn" button but the FN + ALT + SYSRQ key combination does not work?

---

### Post by TheFu on 2019-12-08
If you use a swap file, be certain that it isn't included in backups.
SYSRQ isn't the same as
<cntl><alt>-1

Try that.

---

### Post by pawellepko on 2019-12-09
The key combination "<cntl> <alt> -1" works but if the system freezes it doesn't work.

---

### Post by arcman7 on 2019-12-09
I've been having the same issue for about a year, still, haven't figured out the problem. Also using Firefox latest version on AMD Ryzen 5 w/Vega 11 graphics. I  have 16GB of ram that is rated 3000 but my motherboard AsRock AB350 Pro4 seems to be rated for 2133 speed ram, not sure if that is the problem or something else entirely.

---

### Post by TheFu on 2019-12-09
> **pawellepko said:**
> The key combination "<cntl> <alt> -1" works but if the system freezes it doesn't work.

Ok, that convinces me it is really locked up. Thanks for reporting back.  

Anything in the log files? If they are being wiped at boot, might need to change some journalctl settings to get them to stay around between boots.  I don't remember the exact setting, but it was really easy to find when I searched for it .... /etc/systemd/journald.conf  ... I think it was this setting:
```
Storage=persistent
```
The journald.conf manpage explains the directory requirements, which I had to manually create.

BTW, I have a ryzen 5 2600 and don't see this issue with firefox.  Not using AMD GPU, however.

---

### Post by pawellepko on 2019-12-10
sudo egrep -i 'warn|error' /var/log/*og:
[https://pastebin.com/vwbY7sfJ](https://pastebin.com/vwbY7sfJ)

sudo egrep -i 'warn|error' /var/log/*og | tee /tmp/err.log
[URL="https://pastebin.com/Pdw5yKL9"]https://pastebin.com/Pdw5yKL9
[/URL]
Maybe this is problem with gnome shell extension - "hide top panel/bar".
[B][URL="https://pastebin.com/vwbY7sfJ"]
[/URL][/B]

---

### Post by TheFu on 2019-12-10
> **pawellepko said:**
> sudo egrep -i 'warn|error' /var/log/*og:
[https://pastebin.com/vwbY7sfJ](https://pastebin.com/vwbY7sfJ)

sudo egrep -i 'warn|error' /var/log/*og | tee /tmp/err.log
[URL="https://pastebin.com/Pdw5yKL9"]https://pastebin.com/Pdw5yKL9
[/URL]
Maybe this is problem with gnome shell extension - "hide top panel/bar".
[B][URL="https://pastebin.com/vwbY7sfJ"]
[/URL][/B]

Have you looked at the logs? What do they tell YOU?
BTW, those are the same command - the 2nd one just stores it into a file for convenience.

---

### Post by ra7411 on 2019-12-10
I lose my wired keyboard and wireless logitech mouse response every 2 or 3 days. Both work off a usb 2.0 dock. Usually, changing the dock's  usb plug in on the back of my desktop gets it working again. Occasionally, I have to reboot.

---

### Post by Autodave on 2019-12-10
I may be way off here, but I usually look at things from a hardware side.  IF you are losing the 5V side of the PSU, you would have this issue.  Do you have too many things plugged in to USB ports?  Try removing everything that is not needed to do whatever it is that you are doing.  You could also try getting a powered USB port and put everything into that.

Also, one of those things that you have plugged into a USB port could be defective intermittantly causing the 5V line to go to low to power anything USB.  Not long ago, I had an issue where the HD was shorting out when hot and pulling way too much power.  The mouse would quit functioning.  Replacing the HD cured the problem.

---

