---
title: "Takes time when Ubuntu 22.04.3 LTS gets boot"
date: 2023-12-23
forum: New to Ubuntu
---

### Post by dipeshmagar335 on 2023-12-23
As I have restart the snap and after that it gets lots of time when I boot the device and my network also gets connected but it does't work . After I enable the internal firewall the network gets works and my firewall also gets disable when i boot the devoce

---

### Post by Rubi1200 on 2023-12-23
Hi and welcome to the forums :-)

Two things you need to do:

1. run the system info script (in my signature) and post the link to the pastebin here on the forum

2. open a terminal with Ctrl+Alt+T and run the following command
```
sudo systemd-analyze critical-chain
```

When you reply please click on Go Advanced >> paste the terminal output >> highlight the text and then click on the # icon to wrap with code tags.

Makes things much easier for us to review and analyze.

Thanks.

---

### Post by dipeshmagar335 on 2023-12-23
I get below message when i run above command 
graphical.target @8.099s
&#9492;&#9472;multi-user.target @8.099s
  &#9492;&#9472;kerneloops.service @8.079s +19ms
    &#9492;&#9472;network-online.target @8.040s
      &#9492;&#9472;NetworkManager-wait-online.service @2.171s +5.868s
        &#9492;&#9472;NetworkManager.service @2.124s +44ms
          &#9492;&#9472;network-pre.target @2.106s
            &#9492;&#9472;firewalld.service @1.858s +248ms
              &#9492;&#9472;polkit.service @1.729s +118ms
                &#9492;&#9472;basic.target @1.693s
                  &#9492;&#9472;sockets.target @1.693s
                    &#9492;&#9472;snapd.socket @1.668s +24ms
                      &#9492;&#9472;sysinit.target @1.663s
                        &#9492;&#9472;snapd.apparmor.service @1.364s +298ms
                          &#9492;&#9472;apparmor.service @1.187s +99ms
                            &#9492;&#9472;local-fs.target @1.184s
                              &#9492;&#9472;run-snapd-ns-snapd\x2ddesktop\x2dintegration.mn>
                                &#9492;&#9472;run-snapd-ns.mount @3.449s
                                  &#9492;&#9472;swap.target @1.404s
                                    &#9492;&#9472;dev-mapper-vgubuntu\x2dswap_1.swap @1.325>
                                      &#9492;&#9472;dev-mapper-vgubuntu\x2dswap_1.device @1>

---

### Post by Rubi1200 on 2023-12-23
We still need to see the system info script. The information can help us to help you solve this.

Thanks.

---

### Post by MAFoElffen on 2023-12-23
For the 'system-info' script, select to upload it to a pastebin, and post the URL of where it gets uploaded to...

It looks like your added time in the boot process is related to Firewall & apparmor. Seeing that report will help us to look at what you have installed beyond the defaults, and to help choose a direction to look into further.

---

### Post by dipeshmagar335 on 2023-12-23
```
dipesh@dipesh-IdeaPad-Flex-5-14ARE05:~$ sudo lshw
dipesh-ideapad-flex-5-14are05
    description: Convertible
    product: 81X2 (LENOVO_MT_81X2_BU_idea_FM_IdeaPad Flex 5 14ARE05)
    vendor: LENOVO
    version: IdeaPad Flex 5 14ARE05
    serial: R911WE7K
    width: 64 bits
    capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=convertible family=IdeaPad Flex 5 14ARE05 frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_81X2_BU_idea_FM_IdeaPad Flex 5 14ARE05 uuid=99a727b3-816e-11eb-87de-dce99489df6e
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: SDK0J40700 WIN
       serial: R911WE7K
       slot: Chassis Location Unknown
     *-memory
          description: System Memory
          physical id: 1
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: Row of chips DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
             product: M471A5244CB0-CWE
             vendor: Samsung
             physical id: 0
             serial: 00000000
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
        *-bank:1
             description: Row of chips DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
             product: M471A5244CB0-CWE
             vendor: Samsung
             physical id: 1
             serial: 00000000
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 3200MHz (0.3ns)
     *-cache:0
          description: L1 cache
          physical id: 3
          slot: L1 - Cache
          size: 384KiB
          capacity: 384KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 4
          slot: L2 - Cache
          size: 3MiB
          capacity: 3MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 5
          slot: L3 - Cache
          size: 8MiB
          capacity: 8MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: AMD Ryzen 5 4500U with Radeon Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 6
          bus info: cpu@0
          version: 23.96.1
          serial: Null
          slot: FP6
          size: 1382MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibrs ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsaveerptr rdpru wbnoinvd cppc arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif v_spec_ctrl umip rdpid overflow_recov succor smca sev sev_es cpufreq
          configuration: cores=6 enabledcores=6 microcode=140509444 threads=6
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: d
          version: EECN30WW
          date: 11/26/2020
          size: 128KiB
          capacity: 16MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb ls120boot zipboot biosbootspecification netboot
     *-pci:0
          description: Host bridge
          product: Renoir/Cezanne Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Renoir/Cezanne IOMMU
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Renoir/Cezanne PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096) memory:fc800000-fc8fffff ioport:230000000(size=2097152)
           *-generic
                description: MMC Host
                product: RTS522A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: mmc0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:35 memory:fc800000-fc800fff
        *-pci:1
             description: PCI bridge
             product: Renoir/Cezanne PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:2000(size=4096) memory:fc700000-fc7fffff ioport:230200000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 00
                serial: dc:e9:94:89:df:6d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtw_8822ce driverversion=6.2.0-32-generic firmware=N/A ip=172.17.18.189 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:81 ioport:2000(size=256) memory:fc700000-fc70ffff
        *-pci:2
             description: PCI bridge
             product: Renoir/Cezanne PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:4000(size=4096) memory:fc600000-fc6fffff ioport:230400000(size=2097152)
           *-nvme
                description: NVMe device
                product: WDC PC SN530 SDBPMPZ-256G-1101
                vendor: Sandisk Corp
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: /dev/nvme0
                version: 21160001
                serial: 2048G3473203
                width: 64 bits
                clock: 33MHz
                capabilities: nvme pm msi msix pciexpress nvm_express bus_master cap_list
                configuration: driver=nvme latency=0 nqn=nqn.2018-01.com.wdc:guid:E8238FA6BF53-0001-001B444A46B0E4FA state=live
                resources: irq:53 memory:fc600000-fc603fff memory:fc604000-fc6040ff
              *-namespace:0
                   description: NVMe disk
                   physical id: 0
                   logical name: hwmon3
              *-namespace:1
                   description: NVMe disk
                   physical id: 2
                   logical name: /dev/ng0n1
              *-namespace:2
                   description: NVMe disk
                   physical id: 1
                   bus info: nvme@0:1
                   logical name: /dev/nvme0n1
                   size: 238GiB (256GB)
                   capabilities: gpt-1.00 partitioned partitioned:gpt
                   configuration: guid=80ef9d24-bb6c-434d-921b-dbea4fc1745e logicalsectorsize=512 sectorsize=512 wwid=eui.001b444a46b0e4fa
                 *-volume:0
                      description: Windows FAT volume
                      vendor: mkfs.fat
                      physical id: 1
                      bus info: nvme@0:1,1
                      logical name: /dev/nvme0n1p1
                      version: FAT32
                      serial: b524-f3cd
                      size: 510MiB
                      capacity: 511MiB
                      capabilities: boot fat initialized
                      configuration: FATs=2 filesystem=fat name=EFI System Partition
                 *-volume:1
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 2
                      bus info: nvme@0:1,2
                      logical name: /dev/nvme0n1p2
                      logical name: /boot
                      version: 1.0
                      serial: c7ebd748-7486-45cf-9fd2-acd950ccf096
                      size: 1709MiB
                      capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                      configuration: created=2023-05-09 22:41:50 filesystem=ext4 lastmountpoint=/boot modified=2023-12-23 15:10:50 mount.fstype=ext4 mount.options=rw,relatime mounted=2023-12-23 15:10:50 state=mounted
                 *-volume:2
                      description: EFI partition
                      physical id: 3
                      bus info: nvme@0:1,3
                      logical name: /dev/nvme0n1p3
                      serial: 60e6c893-6490-4457-801e-c1d299263d90
                      size: 236GiB
                      capacity: 236GiB
                      width: 1475455680 bits
                      capabilities: encrypted luks initialized
                      configuration: bits=22950292160 filesystem=luks hash=sha256 version=2
        *-pci:3
             description: PCI bridge
             product: Renoir Internal PCIe GPP Bridge to Bus
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:1000(size=4096) memory:fc100000-fc5fffff ioport:260000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Renoir
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: /dev/fb0
                version: c3
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list fb
                configuration: depth=32 driver=amdgpu latency=0 mode=1920x1080 resolution=1920,1080 visual=truecolor xres=1920 yres=1080
                resources: iomemory:20-1f iomemory:20-1f irq:45 memory:260000000-26fffffff memory:270000000-2701fffff ioport:1000(size=256) memory:fc500000-fc57ffff
           *-multimedia:0
                description: Audio device
                product: Renoir Radeon High Definition Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:04:00.1
                logical name: card0
                logical name: /dev/snd/controlC0
                logical name: /dev/snd/hwC0D0
                logical name: /dev/snd/pcmC0D3p
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:79 memory:fc5c8000-fc5cbfff
              *-input
                   product: HD-Audio Generic HDMI/DP,pcm=3
                   physical id: 0
                   logical name: input20
                   logical name: /dev/input/event12
           *-generic:0
                description: Encryption controller
                product: Family 17h (Models 10h-1fh) Platform Security Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: driver=ccp latency=0
                resources: irq:74 memory:fc400000-fc4fffff memory:fc5ce000-fc5cffff
           *-usb:0
                description: USB controller
                product: Renoir/Cezanne USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:33 memory:fc100000-fc1fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 6.2.0-32-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 6.02
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: Integrated Camera: Integrated C
                      vendor: Generic
                      physical id: 4
                      bus info: usb@1:4
                      logical name: input19
                      logical name: /dev/input/event11
                      version: 0.08
                      serial: 200901010001
                      capabilities: usb-2.01 usb
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 6.2.0-32-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 6.02
                   capabilities: usb-3.10
                   configuration: driver=hub slots=2 speed=10000Mbit/s
           *-usb:1
                description: USB controller
                product: Renoir/Cezanne USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:04:00.4
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:45 memory:fc200000-fc2fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 6.2.0-32-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 6.02
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0 UNCLAIMED
                      description: Generic USB device
                      vendor: Synaptics, Inc.
                      physical id: 3
                      bus info: usb@3:3
                      version: 0.00
                      serial: 60555e361436
                      capabilities: usb-2.00
                      configuration: maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 4
                      bus info: usb@3:4
                      version: 0.00
                      serial: 00e04c000001
                      capabilities: bluetooth usb-1.00
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 6.2.0-32-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 6.02
                   capabilities: usb-3.10
                   configuration: driver=hub slots=2 speed=10000Mbit/s
           *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: Raven/Raven2/FireFlight/Renoir Audio Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.5
                bus info: pci@0000:04:00.5
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:fc580000-fc5bffff
           *-multimedia:2
                description: Audio device
                product: Family 17h (Models 10h-1fh) HD Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.6
                bus info: pci@0000:04:00.6
                logical name: card1
                logical name: /dev/snd/controlC1
                logical name: /dev/snd/hwC1D0
                logical name: /dev/snd/pcmC1D0c
                logical name: /dev/snd/pcmC1D0p
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:54 memory:fc5c0000-fc5c7fff
              *-input:0
                   product: HD-Audio Generic Mic
                   physical id: 0
                   logical name: input21
                   logical name: /dev/input/event13
              *-input:1
                   product: HD-Audio Generic Headphone
                   physical id: 1
                   logical name: input22
                   logical name: /dev/input/event14
           *-generic:1 UNCLAIMED
                description: Signal processing controller
                product: Raven/Raven2/Renoir Sensor Fusion Hub
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.7
                bus info: pci@0000:04:00.7
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix cap_list
                configuration: latency=0
                resources: memory:fc300000-fc3fffff memory:fc5cc000-fc5cdfff
        *-pci:4
             description: PCI bridge
             product: Renoir Internal PCIe GPP Bridge to Bus
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:5000(size=4096) memory:fc000000-fc0fffff ioport:230600000(size=2097152)
           *-sata:0
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 81
                width: 32 bits
                clock: 33MHz
                capabilities: sata pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:37 memory:fc001000-fc0017ff
           *-sata:1
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 81
                width: 32 bits
                clock: 33MHz
                capabilities: sata pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:72 memory:fc000000-fc0007ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 51
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
           *-pnp00:00
                product: PnP device PNP0c02
                physical id: 0
                capabilities: pnp
                configuration: driver=system
           *-pnp00:01
                product: PnP device PNP0b00
                physical id: 1
                capabilities: pnp
                configuration: driver=rtc_cmos
           *-pnp00:02
                product: PnP device PNP0c02
                physical id: 2
                capabilities: pnp
                configuration: driver=system
           *-pnp00:03
                product: PnP device PNP0c01
                physical id: 3
                capabilities: pnp
                configuration: driver=system
           *-pnp00:04
                product: PnP device PNP0303
                physical id: 4
                capabilities: pnp
                configuration: driver=i8042 kbd
           *-input
                product: Ideapad extra buttons
                physical id: 5
                logical name: input16
                logical name: /dev/input/event10
                capabilities: platform
     *-pci:1
          description: Host bridge
          product: Renoir PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Renoir PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Renoir PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Renoir Device 24: Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Renoir Device 24: Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Renoir Device 24: Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Renoir Device 24: Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Renoir Device 24: Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Renoir Device 24: Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Renoir Device 24: Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Renoir Device 24: Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10b
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-input:0
       product: Power Button
       physical id: 1
       logical name: input0
       logical name: /dev/input/event0
       capabilities: platform
  *-input:1
       product: Lid Switch
       physical id: 2
       logical name: input1
       logical name: /dev/input/event1
       capabilities: platform
  *-input:2
       product: Wacom HID 5218 Pen
       physical id: 3
       logical name: input13
       logical name: /dev/input/event8
       logical name: /dev/input/mouse2
       capabilities: i2c
  *-input:3
       product: Wacom HID 5218 Finger
       physical id: 4
       logical name: input14
       logical name: /dev/input/event9
       logical name: /dev/input/mouse3
       capabilities: i2c
  *-input:4
       product: MSFT0001:00 04F3:3140 Mouse
       physical id: 5
       logical name: input17
       logical name: /dev/input/event6
       logical name: /dev/input/mouse0
       capabilities: i2c
  *-input:5
       product: MSFT0001:00 04F3:3140 Touchpad
       physical id: 6
       logical name: input18
       logical name: /dev/input/event7
       logical name: /dev/input/mouse1
       capabilities: i2c
  *-input:6
       product: Sleep Button
       physical id: 7
       logical name: input2
       logical name: /dev/input/event2
       capabilities: platform
  *-input:7
       product: Power Button
       physical id: 8
       logical name: input3
       logical name: /dev/input/event3
       capabilities: platform
  *-input:8
       product: AT Translated Set 2 keyboard
       physical id: 9
       logical name: input4
       logical name: /dev/input/event4
       logical name: input4::capslock
       logical name: input4::numlock
       logical name: input4::scrolllock
       capabilities: i8042
  *-input:9
       product: Video Bus
       physical id: a
       logical name: input5
       logical name: /dev/input/event5
       capabilities: platform




journalctl -b -p err -xe
~
~
~
~
Dec 23 15:10:49 dipesh-IdeaPad-Flex-5-14ARE05 kernel: ucsi_acpi USBC000:00: failed to reset PPM!
Dec 23 15:10:49 dipesh-IdeaPad-Flex-5-14ARE05 kernel: ucsi_acpi USBC000:00: PPM init failed (-110)
Dec 23 15:11:03 dipesh-IdeaPad-Flex-5-14ARE05 sddm-helper[4218]: gkr-pam: unable to locate daemon control file
Dec 23 15:15:26 dipesh-IdeaPad-Flex-5-14ARE05 systemd[4220]: Failed to start Application launched by gnome-session-binary.
&#9617;&#9617; Subject: A start job for unit UNIT has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 467 and the job result is failed.
Dec 23 15:15:26 dipesh-IdeaPad-Flex-5-14ARE05 systemd[4220]: Failed to start Application launched by gnome-session-binary.
&#9617;&#9617; Subject: A start job for unit UNIT has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 475 and the job result is failed.
Dec 23 15:15:26 dipesh-IdeaPad-Flex-5-14ARE05 systemd[4220]: Failed to start Application launched by gnome-session-binary.
&#9617;&#9617; Subject: A start job for unit UNIT has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 471 and the job result is failed.
Dec 23 17:00:01 dipesh-IdeaPad-Flex-5-14ARE05 kernel: ata1: failed stop FIS RX (-16)
Dec 23 17:33:11 dipesh-IdeaPad-Flex-5-14ARE05 pulseaudio[4229]: Lost I/O connection in module "module-gsettings"
Dec 23 17:33:18 dipesh-IdeaPad-Flex-5-14ARE05 sddm-helper[336585]: gkr-pam: unable to locate daemon control file
Dec 23 17:33:18 dipesh-IdeaPad-Flex-5-14ARE05 systemd[4220]: Failed to start Application launched by gnome-session-binary.
&#9617;&#9617; Subject: A start job for unit UNIT has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 1227 and the job result is failed.
Dec 23 17:33:33 dipesh-IdeaPad-Flex-5-14ARE05 pulseaudio[339470]: org.bluez.ProfileManager1.RegisterProfile() failed: org.bluez.Error.NotPermitted: UUID already registered
Dec 23 17:33:33 dipesh-IdeaPad-Flex-5-14ARE05 pulseaudio[339470]: org.bluez.ProfileManager1.RegisterProfile() failed: org.bluez.Error.NotPermitted: UUID already registered
Dec 23 17:33:36 dipesh-IdeaPad-Flex-5-14ARE05 sddm-helper[339685]: gkr-pam: unable to locate daemon control file
Dec 24 10:11:53 dipesh-IdeaPad-Flex-5-14ARE05 systemd[4220]: Failed to start Application launched by gnome-shell.
&#9617;&#9617; Subject: A start job for unit UNIT has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 1742 and the job result is failed.
```

---

### Post by dipeshmagar335 on 2023-12-24
[https://pastebin.com/W24G8rqy](https://pastebin.com/W24G8rqy)

---

### Post by MAFoElffen on 2023-12-24
Welcome to Ubuntu Forums.

As a new member, to help you with your experience here, please read this:    [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945") 

If you notice #3 there, when posting raw output and/or commands, it is important that you post them within CODE Tags... That not only helps others to be able to identify ad read what is there, to be able to help you... Some stray output can actually do strange and harmful things to the Forum's "System Software" interpreting it.

Next read this the post for this Sticky: Sticky: [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

You will notice that in that Sticky, there may be information that may be asked for that may be required for us to be able to help you... Two of us have asked you for specific information in the same form and source. You did provide "some information", but it was not the information we asked for, nor in the form we ask it by... 

This may be a misunderstanding. If you do not understand something.  Please ask us for clarification before going off and doing something on your own. We would be glad to clarify that for you. I would rather do that, than have you do a command that destroys your installation and loses your data. Understood? 

Please follow directions given. If you cannot follow simple directions, then I am hesitant in giving you more complex directions to solve your problem. Understood?

Both that Sticky, and two of us have asked you to supply the results of this: [Sticky: UbuntuForums 'system-info' Script]("https://ubuntuforums.org/showthread.php?t=2475931")

If you have trouble understanding or following those directions please post back and ask. We would be happy to answer any questions with that.

---

### Post by curtis77 on 2024-01-11
graphical.target @1min 58.488s
&#9492;&#9472;multi-user.target @1min 58.486s
  &#9492;&#9472;plymouth-quit-wait.service @46.059s +1min 12.362s
    &#9492;&#9472;systemd-user-sessions.service @44.984s +677ms
      &#9492;&#9472;network.target @44.811s
        &#9492;&#9472;wpa_supplicant.service @38.824s +5.983s
          &#9492;&#9472;dbus.service @35.860s
            &#9492;&#9472;basic.target @35.489s
              &#9492;&#9472;sockets.target @35.488s
                &#9492;&#9472;cups.socket @44.220s
                  &#9492;&#9472;sysinit.target @35.334s
                    &#9492;&#9472;snapd.apparmor.service @33.562s +1.768s
                      &#9492;&#9472;apparmor.service @30.933s +2.609s
                        &#9492;&#9472;local-fs.target @30.927s
                          &#9492;&#9472;boot-efi.mount @30.744s +181ms
                            &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-73CB\x2d6534.ser>
                              &#9492;&#9472;dev-disk-by\x2duuid-73CB\x2d6534.device @30.262s
lines 1-20/20 (END)

---

