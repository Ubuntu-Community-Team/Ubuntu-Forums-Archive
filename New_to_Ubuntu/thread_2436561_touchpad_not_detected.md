---
title: "touchpad not detected"
date: 2020-02-08
forum: New to Ubuntu
---

### Post by jimmie688 on 2020-02-08
i recently flashed my chromebook firmware with mrchromebox firmware and i installed ubuntu 20.04 works awesome besides the touchpad is not detected in xinput in terminal i tried everything i could possibly find on the internet and i am stuck , im currently using a external mouse to fix this issue its as if ubuntu is not reconizing the touchpad to even use it and i cant find any drivers for cypress ata touchpads .


system i have a samsung 5 550 chrome book flashed to coreboot uefi
os- ubuntu 20.04 
touch pad is a cypress ata 
 any advice would be awesome

---

### Post by mörgæs on 2020-02-09
Hi, welcome to the fora.

Please post the output from the **xinput** command. Not sure that I can use it to draw conclusions but there might be some who can.

---

### Post by jimmie688 on 2020-02-10
jimmie@Lumpy:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. USB Device                     id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; WebCam SC-10HDP11538N: WebCam S             id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
jimmie@Lumpy:~$ 


the mosart semi usb is the usb mouse ive been using to navigate thru ubuntu

if i download the firmware back to chrome os the touchpad works fine but when i reinstall mrchromebox firmware it doesnt work on any operating systems fedora ,galimos, windows 10 ubuntu 18.10, ubuntu 19.10 and my current ubuntu 20.04. i can provide any info you want just ask i will continue to try

jimmie@Lumpy:~$ sudo lshw
[sudo] ```
password for jimmie: 
lumpy                       
    description: Laptop
    product: Lumpy
    vendor: GOOGLE
    version: 1.0
    serial: 123456789
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=laptop
  *-core
       description: Motherboard
       product: Lumpy
       vendor: GOOGLE
       physical id: 0
       version: 1.0
       serial: 123456789
     *-firmware
          description: BIOS
          vendor: coreboot
          physical id: 0
          version: MrChromebox-4.11.1
          date: 12/01/2019
          size: 1MiB
          capacity: 8MiB
          capabilities: pci pcmcia upgrade bootselect acpi
     *-cpu:0 DISABLED
          description: CPU [empty]
          vendor: GenuineIntel
          physical id: 4
          version: Intel(R) Celeron(R) CPU 867 @ 1.30GHz
          configuration: cores=16 enabledcores=8
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: CACHE1
             size: 32KiB
             capacity: 32KiB
             capabilities: internal instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: CACHE2
             size: 256KiB
             capacity: 256KiB
             capabilities: internal unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: CACHE3
             size: 2MiB
             capacity: 2MiB
             capabilities: internal unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 5
          slot: CACHE0
          size: 32KiB
          capacity: 32KiB
          capabilities: internal data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: 00000000
             slot: Channel-0-DIMM-0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DDR3 Synchronous 1333 MHz (0.8 ns)
             product: None
             vendor: Unknown (0)
             physical id: 1
             serial: 00000000
             slot: Channel-1-DIMM-0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:1
          product: Intel(R) Celeron(R) CPU 867 @ 1.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1039MHz
          capacity: 1300MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm arat pln pts md_clear flush_l1d cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:3000(size=64) memory:c0000-dffff
        *-generic:0 UNCLAIMED
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: latency=0
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:29 memory:e0611000-e061100f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:e060e000-e060e3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-12-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: WebCam SC-10HDP11538N
                      vendor: Namuga
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 0.03
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:31 memory:e0608000-e060bfff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:e0400000-e04fffff
           *-network
                description: Wireless interface
                product: AR93xx Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 01
                serial: 20:68:9d:8d:12:80
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=5.4.0-12-generic firmware=N/A ip=10.0.0.234 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:e0400000-e041ffff memory:e0420000-e042ffff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) ioport:e0500000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 06
                serial: 50:b7:c3:69:d3:bf
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII
                resources: irq:19 ioport:2000(size=256) memory:e0504000-e0504fff memory:e0500000-e0503fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:e060f000-e060f3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-12-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Mouse
                      product: USB Device
                      vendor: MOSART Semi.
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 1.17
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-sata
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:3060(size=8) ioport:3070(size=4) ioport:3068(size=8) ioport:3074(size=4) ioport:3040(size=32) memory:e060d000-e060d7ff
           *-disk
                description: ATA Disk
                product: SanDisk SSD U100
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 1.04
                serial: 123434301663
                size: 14GiB (16GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=8744b0a7-0443-4abe-ad28-54eedd77a68c logicalsectorsize=512 sectorsize=512
              *-volume:0 UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   version: FAT32
                   serial: b9e0-580b
                   size: 510MiB
                   capacity: 511MiB
                   capabilities: boot fat initialized
                   configuration: FATs=2 filesystem=fat name=EFI System Partition
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 258eb4cb-224e-4feb-bde4-bf20438d13ef
                   size: 14GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2020-02-09 13:12:46 filesystem=ext4 lastmountpoint=/ modified=2020-02-10 11:46:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2020-02-10 11:46:13 state=mounted
        *-serial
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:23 memory:e0610000-e06100ff ioport:400(size=32)
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: 6 Series/C200 Series Chipset Family Thermal Management Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:e060c000-e060cfff
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0103
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0b00
          physical id: 7
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 8
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device GGL0303
          physical id: a
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:06
          product: PnP device PNP0c02
          physical id: b
          capabilities: pnp
          configuration: driver=system
     *-pnp00:07
          product: PnP device PNP0c31
          physical id: c
          capabilities: pnp
          configuration: driver=tpm_tis
jimmie@Lumpy:~$
```

ChromeOS Firmware Utility Script [2020-01-17] 
 (c) Mr Chromebox <mrchromebox@gmail.com> 
*********************************************************
**   Device: Samsung Chromebook Series 5 550 (LUMPY)
** CPU Type: Intel SandyBridge
**  Fw Type: Full ROM / UEFI (MrChromebox-4.11.1 12/01/2019)
**    Fw WP: Disabled

---

### Post by wildmanne39 on 2020-02-10
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by jimmie688 on 2020-02-10
i figured it out by installing sea bois my issue was within my bois thanks for everyones interest i will continue to use this forum for more help . and maybe ill know how to use this forum but then sorry if i went about it wrong . cheers mate

---

