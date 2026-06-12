---
title: "Audio and video skipping. Screen tearing"
date: 2021-03-10
forum: New to Ubuntu
---

### Post by joubqa on 2021-03-10
Laptop is connected to soundbar with HDMI which is connected to smart TV with HDMI.
Audio skips for a second every once in a while (about once a minute), sometimes screen goes black also for for a second. There is screen tearing when browsing, watching youtube or video files.

```
sudo lshw:

    description: Notebook
    product: 81LB (LENOVO_MT_81LB_BU_idea_FM_Legion Y530-15ICH-1060)
    vendor: LENOVO
    version: Lenovo Legion Y530-15ICH-1060
    serial: PF1KQM7E
    width: 64 bits
    capabilities: smbios-3.0.1 dmi-3.0.1 smp vsyscall32
    configuration: administrator_password=disabled boot=normal  chassis=notebook family=Legion Y530-15ICH-1060  frontpanel_password=disabled keyboard_password=disabled  power-on_password=disabled sku=LENOVO_MT_81LB_BU_idea_FM_Legion  Y530-15ICH-1060 uuid=E1C732A7-7306-E911-BB88-E86A64896E20
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: SDK0R32862 WIN
       serial: PF1KQM7E
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 9VCN20WW
          date: 06/15/2020
          size: 128KiB
          capacity: 10MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd  int13floppynec int13floppytoshiba int13floppy360 int13floppy1200  int13floppy720 int13floppy2880 int9keyboard int10video acpi usb  biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2781MHz
          capacity: 4100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr  sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art  arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid  aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg  fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt  tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch  cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi  flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2  erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec  xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window  hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=6 enabledcores=6 threads=12
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 384KiB
             capacity: 384KiB
             capabilities: synchronous internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 9MiB
             capacity: 9MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2667 MHz (0,4 ns)
             product: M471A1K43CB1-CTD
             vendor: Samsung
             physical id: 0
             serial: 4166422C
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 2667 MHz (0,4 ns)
             product: M471A1K43CB1-CTD
             vendor: Samsung
             physical id: 1
             serial: 4166415F
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
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
             resources: irq:122 ioport:5000(size=4096) memory:a3000000-a40fffff ioport:90000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GP106M [GeForce GTX 1060 Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:146 memory:a3000000-a3ffffff  memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128)  memory:a4080000-a40fffff
           *-multimedia
                description: Audio device
                product: GP106 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:a4000000-a4003fff
        *-display
             description: VGA compatible controller
             product: UHD Graphics 630 (Mobile)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:143 memory:a2000000-a2ffffff memory:b0000000-bfffffff ioport:6000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:a4510000-a4517fff
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:a4520000-a4520fff
        *-generic:2
             description: Signal processing controller
             product: Cannon Lake PCH Thermal Controller
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:16 memory:a4521000-a4521fff
        *-usb
             description: USB controller
             product: Cannon Lake PCH USB 3.1 xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:127 memory:a4500000-a450ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.8.0-44-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.08
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Audio device
                   product: Wireless Stereo Headset
                   vendor: Sony Interactive Entertainment
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-1.10 audio-control
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Video
                   product: Integrated Camera
                   vendor: SunplusIT Inc
                   physical id: 6
                   bus info: usb@1:6
                   version: 54.22
                   capabilities: usb-2.01
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   product: Bluetooth Radio
                   vendor: Realtek
                   physical id: e
                   bus info: usb@1:e
                   version: 1.10
                   serial: 00e04c000001
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=500mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.8.0-44-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.08
                capabilities: usb-3.10
                configuration: driver=hub slots=8 speed=10000Mbit/s
              *-usb
                   description: Mass storage device
                   product: External USB 3.0
                   vendor: TOSHIBA
                   physical id: 3
                   bus info: usb@2:3
                   version: 3.15
                   serial: 20200206021934F
                   capabilities: usb-3.00 scsi
                   configuration: driver=usb-storage maxpower=896mA speed=5000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Cannon Lake PCH Shared SRAM
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:a451c000-a451dfff memory:a4522000-a4522fff
        *-serial:0
             description: Serial bus controller
             product: Cannon Lake PCH Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:8f800000-8f800fff
        *-serial:1
             description: Serial bus controller
             product: Cannon Lake PCH Serial IO I2C Controller #1
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:8f801000-8f801fff
        *-communication:0
             description: Communication controller
             product: Cannon Lake PCH HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:142 memory:a4525000-a4525fff
        *-sata
             description: SATA controller
             product: Cannon Lake Mobile PCH SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:126 memory:a451e000-a451ffff  memory:a452a000-a452a0ff ioport:6080(size=8) ioport:6088(size=4)  ioport:6060(size=32) memory:a4529000-a45297ff
        *-pci:1
             description: PCI bridge
             product: Cannon Lake PCH PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:a4400000-a44fffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM981/PM981/PM983
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:a4400000-a4403fff
              *-nvme0
                   description: NVMe device
                   product: SAMSUNG MZVLB512HAJQ-000L2
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 4L1QEXA7
                   serial: S3RGNX0KA27604
                   configuration:  nqn=nqn.2014.08.org.nvmexpress:144d144dS3RGNX0KA27604      SAMSUNG  MZVLB512HAJQ-000L2 state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
                      size: 476GiB (512GB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: guid=0c1bb75d-d0de-4e8d-9429-d755f0f9104f logicalsectorsize=512 sectorsize=512
                    *-volume:0
                         description: Windows FAT volume
                         vendor: MSDOS5.0
                         physical id: 1
                         logical name: /dev/nvme0n1p1
                         logical name: /boot/efi
                         version: FAT32
                         serial: 16cb-a9bd
                         size: 255MiB
                         capacity: 259MiB
                         capabilities: boot fat initialized
                         configuration: FATs=2 filesystem=fat  label=SYSTEM_DRV mount.fstype=vfat  mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro  name=EFI system partition state=mounted
                    *-volume:1
                         description: reserved partition
                         vendor: Windows
                         physical id: 2
                         logical name: /dev/nvme0n1p2
                         serial: 490220c3-63c4-4bcc-9fc8-9afab25b411d
                         capacity: 15MiB
                         capabilities: nofs
                         configuration: name=Microsoft reserved partition
                    *-volume:2
                         description: Windows NTFS volume
                         vendor: Windows
                         physical id: 3
                         logical name: /dev/nvme0n1p3
                         version: 3.1
                         serial: b0f4d822-e07f-7140-be5d-201c6739ac16
                         size: 445GiB
                         capacity: 445GiB
                         capabilities: ntfs initialized
                         configuration: clustersize=4096  created=2019-01-08 04:35:19 filesystem=ntfs label=Windows-SSD name=Basic  data partition state=clean
                    *-volume:3
                         description: Windows NTFS volume
                         vendor: Windows
                         physical id: 4
                         logical name: /dev/nvme0n1p4
                         version: 3.1
                         serial: 6cf145ed-f033-384a-9c9b-ea3b78714d21
                         size: 973MiB
                         capacity: 999MiB
                         capabilities: boot precious ntfs initialized
                         configuration: clustersize=4096  created=2019-01-08 04:35:22 filesystem=ntfs label=WINRE_DRV name=Basic  data partition state=clean
                    *-volume:4
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 5
                         logical name: /dev/nvme0n1p5
                         logical name: /
                         version: 1.0
                         serial: af7e9db6-b182-4654-8325-dea13225645f
                         size: 30GiB
                         capabilities: journaled extended_attributes  large_files huge_files dir_nlink recover 64bit extents ext4 ext2  initialized
                         configuration: created=2020-11-21 23:34:52  filesystem=ext4 lastmountpoint=/ modified=2021-03-10 13:06:09  mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro  mounted=2021-03-10 13:06:09 state=mounted
        *-pci:2
             description: PCI bridge
             product: Cannon Lake PCH PCI Express Root Port #13
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 ioport:4000(size=4096) memory:a4300000-a43fffff
           *-network
                description: Wireless interface
                product: RTL8822BE 802.11a/b/g/n/ac WiFi adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlp7s0
                version: 00
                serial: 28:3a:4d:7d:cb:55
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtw_8822be  driverversion=5.8.0-44-generic firmware=N/A ip=192.168.1.128 latency=0  link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:144 ioport:4000(size=256) memory:a4300000-a430ffff
        *-pci:3
             description: PCI bridge
             product: Cannon Lake PCH PCI Express Root Port #14
             vendor: Intel Corporation
             physical id: 1d.5
             bus info: pci@0000:00:1d.5
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:3000(size=4096) memory:a4200000-a42fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: enp8s0
                version: 15
                serial: e8:6a:64:89:6e:20
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd  autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=r8169 driverversion=5.8.0-44-generic firmware=rtl8168h-2_0.0.2  02/26/15 latency=0 link=no multicast=yes port=MII
                resources: irq:17 ioport:3000(size=256) memory:a4204000-a4204fff memory:a4200000-a4203fff
        *-communication:1
             description: Communication controller
             product: Cannon Lake PCH Serial IO UART Host Controller
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:20 memory:8f802000-8f802fff
        *-isa
             description: ISA bridge
             product: HM470 Chipset LPC/eSPI Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Cannon Lake PCH cAVS
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:145 memory:a4518000-a451bfff memory:a4100000-a41fffff
        *-serial:2
             description: SMBus
             product: Cannon Lake PCH SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 10
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:16 memory:a4527000-a45270ff ioport:6040(size=32)
        *-serial:3 UNCLAIMED
             description: Serial bus controller
             product: Cannon Lake PCH SPI Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
             resources: memory:fe010000-fe010fff
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0b00
          physical id: 6
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:05
          product: PnP device INT3f0d
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0303
          physical id: 8
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:07
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: a
          capabilities: pnp
          configuration: driver=system
     *-scsi
          physical id: b
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: External USB 3.0
             vendor: TOSHIBA
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sda
             version: 5438
             serial: 20200206021934F
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=9c604f55
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/joni/TOSHIBA EXT
                version: 3.1
                serial: e2868087-0b0b-a640-8cc0-60f4beaaa4f3
                size: 735GiB
                capacity: 735GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2020-02-20  09:29:21 filesystem=ntfs label=TOSHIBA EXT mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/joni/Ext4
                logical name: /run/timeshift/backup
                version: 1.0
                serial: 01f45773-9c30-4e91-b1f8-69c157efc05c
                size: 195GiB
                capacity: 195GiB
                capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2020-11-23 14:33:24  filesystem=ext4 label=Ext4 lastmountpoint=/media/joni/Ext4  modified=2021-03-10 13:06:18 mount.fstype=ext4 mount.options=rw,relatime  mounted=2021-03-10 13:06:18 state=mounted
  *-battery
       description: Zinc Air Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 08/08/2010
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh

```

Edit: This fixed the tearing but audio/video still skipping 
nvidia-settings --assign CurrentMetaMode="HDMI-0:3840x2160_60  +0+0 { ForceFullCompositionPipeline = On }"

---

### Post by joubqa on 2021-03-11
This is so annoying! Can anyone tell me what I could try?
Screen randomly goes black for a second quite oftern. Sound skips for a second even more often

---

### Post by SeijiSensei on 2021-03-11
Are you using the proprietary NVIDIA driver?  Go to System Settings > Driver Manager to see.

If this is one of those "hybrid" systems with NVIDIA and another adapter, usually Intel, see if you can disable the secondary adapter in the BIOS.

---

### Post by joubqa on 2021-03-11
I couldn't find driver managet but the nvidia driver is 450.102.04. Not sure what you mean by adapter, specs are in the op. 
My laptop screen is not showing up in Ubuntu anymore (another issue) but if I remember correctly this going black only happened on the tv and not the laptop screen.

---

