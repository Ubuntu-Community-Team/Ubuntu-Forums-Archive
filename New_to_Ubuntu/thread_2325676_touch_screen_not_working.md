---
title: "touch screen not working"
date: 2016-05-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-05-24
running 16.04 on a hp laptop. just happened was working fine after i installed./?

---

### Post by chamerjr on 2016-05-24
I had a similar problem with my Samsung Ultrabook.  I removed the proprietary drivers and the open source ones, then reinstalled the open source driver.  I don't have the link that gave me the instructions, and I'm too new to the command line to attempt to give you the information.  I hope this helps.

---

### Post by yazdzik-k on 2016-05-24
Dear R,

Can you please post the output of xinput and lshw,  so we can see which input device and driver are or are not in use?

Best,
M

---

### Post by rburkartjo on 2016-05-24
ray@nightmare:~$ xinput
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Wireless Mouse        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. eGalaxTouch EXC3000-0367-44.01.00	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Wireless Mouse        	id=9	[slave  keyboard (3)]
    &#8627; HP Truevision HD                        	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=15	[slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                     	id=16	[slave  keyboard (3)]
```
ray@nightmare:~$ sudo lshw
```
[sudo] password for ray: 
nightmare                 
    description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 6910MiB
     *-cpu
          product: AMD A8-7410 APU with AMD Radeon R5 Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_l2 cpb hw_pstate vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold cpufreq
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Mullins [Radeon R4/R5 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 45
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:39 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:feb40000-feb5ffff
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
             resources: irq:44 memory:feb64000-feb67fff
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
             resources: irq:25 ioport:1000(size=4096) memory:d0900000-d0afffff ioport:d0b00000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: RTL8188EE Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 40:b8:9a:1b:90:6b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8188ee driverversion=4.4.0-22-generic firmware=N/A ip=192.168.2.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:45 ioport:e000(size=256) memory:fea00000-fea03fff
        *-pci:2
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 07
                serial: 3c:a8:2a:bc:f2:46
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:36 ioport:d000(size=256) memory:fe914000-fe914fff memory:fe910000-fe913fff memory:fe900000-fe90ffff
        *-pci:3
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:fe800000-fe8fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:34 memory:fe800000-fe800fff
        *-generic
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msix ht pm bus_master cap_list
             configuration: driver=ccp latency=0
             resources: irq:0 memory:d0800000-d081ffff memory:fe700000-fe7fffff memory:feb6f000-feb6ffff memory:feb6a000-feb6bfff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:feb68000-feb69fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-22-generic xhci-hcd
                physical id: 0
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-22-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 1
                   bus info: usb@3:1
                   version: 7.02
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Printer
                      product: Deskjet F4100 series
                      vendor: HP
                      physical id: 1
                      bus info: usb@3:1.1
                      version: 1.00
                      serial: CN75G2F0HY04TJ
                      capabilities: usb-2.00 bidirectional
                      configuration: driver=usblp maxpower=2mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: 2.4G Wireless Mouse
                   vendor: MOSART Semi.
                   physical id: 2
                   bus info: usb@3:2
                   version: 1.09
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:37 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb6e000-feb6e3ff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:feb6d000-feb6d0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Mouse
                      product: eGalaxTouch EXC3000-0367-44.01.00
                      vendor: eGalax Inc.
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 67.02
                      capabilities: usb-2.01
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:feb6c000-feb6c0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: HP Truevision HD
                      vendor: Sonix Technology Co., Ltd.
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 1.03
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb60000-feb63fff
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
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
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
          product: Advanced Micro Devices, Inc. [AMD]
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
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10JPVX-60J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: WD-WXL1E150AREX
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=00084d94
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 53739041-83a8-46d9-a78e-9378bcb97049
                size: 924GiB
                capacity: 924GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-05-16 09:06:08 filesystem=ext4 lastmountpoint=/ modified=2016-05-24 10:20:45 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-05-24 10:20:58 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 7101MiB
                capacity: 7101MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 7101MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW  DU8A6SH
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: DH61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
ray@nightmare
```

---

### Post by rburkartjo on 2016-05-29
bump

---

### Post by rburkartjo on 2016-10-06
10/06/16 update

just downloaded ubuntu 16.10 and touch screen is working fine in this version. has anyone figured out how to make it work in 16.04. i like to keep a running lts just in case i bork the current release./tks

---

