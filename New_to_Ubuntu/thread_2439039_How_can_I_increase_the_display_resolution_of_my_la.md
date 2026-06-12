---
title: "How can I increase the display resolution of my laptop?"
date: 2020-03-21
forum: New to Ubuntu
---

### Post by pixaeiro on 2020-03-21
Hello,

I installed Ubuntu in my HP Pavilion M1X71UA ([hp support page]("https://support.hp.com/in-en/document/c04693459")) and I haven't been able to set the display resolution to 1920 x 1080 as I had it in Windows.

I followed the steps in this [askubuntu post]("https://askubuntu.com/questions/448045/how-to-make-my-maximum-screen-resolution-to-be-detected-by-ubuntu"), these is the output;

$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

$ xrandr --newmode "1920x1080"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 16384 x 16384
eDP connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900      60.00*+  40.00  
   1440x900      60.00  
   1280x800      60.00  
   1280x720      60.00  
   1024x768      60.00  
   800x600       60.00  
   640x480       60.00  
HDMI-A-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x6cb) 173.000MHz -HSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz

$ xrandr --addmode eDP "1920x1080"

The screen blinks and in Settings > Devices > Display I see the new 1920 x 1080 screen resolution, but if I select it the screen goes black and it comes back after a while.

Am I doing something wrong? I have tried a few times but I haven't been able to increase the display resolution yet.

Thank you!

---

### Post by mörgæs on 2020-03-22
Hi, welcome to the fora.

Though you have linked to the HP page we would like to see more details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by pixaeiro on 2020-03-22
Thank you mörgæs,

Here is the lshw output:

```

computer
    description: Notebook
    product: HP Pavilion Notebook (M1X71UA#ABL)
    vendor: Hewlett-Packard
    version: Chassis Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV sku=M1X71UA#ABL uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 80B0
       vendor: Hewlett-Packard
       physical id: 0
       version: 81.28
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F.13
          date: 08/06/2015
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cache:0
          description: L1 cache
          physical id: d
          slot: L1 CACHE
          size: 320KiB
          capacity: 320KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: e
          slot: L2 CACHE
          size: 2MiB
          capacity: 2MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1600 MHz (0.6 ns)
             product: HP687515-H66-MCN
             vendor: Kingston
             physical id: 0
             serial: [REMOVED]
             slot: Bottom-Slot 1 (left)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1600 MHz (0.6 ns)
             product: HP691160-H66-MCN
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: Bottom-Slot 2 (right)
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G
          vendor: Advanced Micro Devices [AMD]
          physical id: 21
          bus info: cpu@0
          version: AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G
          slot: P0
          size: 1329MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic:0 UNCLAIMED
             description: IOMMU
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Carrizo
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: c5
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=amdgpu latency=0
             resources: irq:48 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:f000(size=256) memory:ff700000-ff73ffff memory:c0000-dffff
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
             resources: irq:50 memory:ff764000-ff767fff
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:ff600000-ff6fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:35 memory:ff600000-ff600fff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:ff500000-ff5fffff
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eno1
                version: 07
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:36 ioport:e000(size=256) memory:ff514000-ff514fff memory:ff510000-ff513fff memory:ff500000-ff50ffff
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:1000(size=4096) memory:ff400000-ff4fffff ioport:f0900000(size=2097152)
           *-network
                description: Network controller
                product: BCM43142 802.11b/g/n
                vendor: Broadcom Limited
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:46 memory:ff400000-ff407fff
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:2000(size=4096) memory:f0b00000-f0cfffff ioport:f0d00000(size=2097152)
        *-generic:1 UNCLAIMED
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msix ht pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0800000-f081ffff memory:ff300000-ff3fffff memory:ff76f000-ff76ffff memory:ff76a000-ff76bfff
        *-multimedia:1
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:ff760000-ff763fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:ff768000-ff769fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.18.0-15-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.18
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: HP Truevision HD
                   vendor: Generic
                   physical id: 1
                   bus info: usb@2:1
                   version: 19.16
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Generic USB device
                   product: BCM43142A0
                   vendor: Broadcom Corp
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.12
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=btusb speed=12Mbit/s
              *-usb:2
                   description: Mouse
                   product: Trackball
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@2:3
                   version: 2.20
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.18.0-15-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.18
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:38 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:ff76d000-ff76d3ff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:ff76c000-ff76c0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.18.0-15-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.18
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
                      description: Wireless interface
                      product: 802.11 n WLAN
                      vendor: Ralink
                      physical id: 1
                      bus info: usb@1:1.1
                      logical name: wlx9cefd5fcb0c4
                      version: 1.01
                      serial: [REMOVED]
                      capabilities: usb-2.00 ethernet physical wireless
                      configuration: broadcast=yes driver=rt2800usb driverversion=4.18.0-15-generic firmware=0.36 ip=[REMOVED] link=yes maxpower=450mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 4a
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
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:09.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
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
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
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
             product: PNY CS900 480GB
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0211
             serial: [REMOVED]
             size: 447GiB (480GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=5fd3c6ee
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 512MiB
                capabilities: primary bootable boot fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 446GiB
                capacity: 446GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 446GiB
                   capacity: 446GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2020-03-20 21:15:14 filesystem=ext4 lastmountpoint=/ modified=2020-03-22 10:55:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2020-03-22 10:55:51 state=mounted
     *-scsi:1
          physical id: 2
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
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: KI04041
       vendor: 131-24-72
       physical id: 1
       slot: Primary
       capacity: 41440mWh
       configuration: voltage=14.8V

```

---

### Post by mörgæs on 2020-03-23
I don't know much about the AMDGPU drivers so other users might be able to give more precise advice.

If you don't get other answers I suggest that you do a fresh install of 19.10. The AMD drivers are in fast development and it's worth the effort to try to see what the new versions bring.

---

### Post by pixaeiro on 2020-03-23
Sounds like a plan. I'll try that!
Thank you mörgæs.

---

