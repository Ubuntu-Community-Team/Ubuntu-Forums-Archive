---
title: "checking PC config"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by vamsi_spr on 2013-10-30
Hey folks, So finally i installed steam and trying to play dota 2 on my newly installed ubuntu right ?, here i found there is a lot of lag in the game and the graphics aren't that cool either, so i wondered what would be the specs of my system ( it's been a while since i used this laptop and it was given to me by my company, i rarely use it) , i mean i know that this is lenovo thinkpad with i3 processor but i want to know about the graphics, processor speed and all other hardware specs, i opened system monitor and was little perplexed 'cause there was no system tab, i attached the screenshot for reference, am a complete noob here so please fill me out here, i can see only one drive  as in the screenshot there but i shrinked a windows drive and formatted with ext4 and also placed my steam library there, why is that not showing up ?? any other suggestions on how to improve my gaming experience in Ubuntu will be greatly appreciated, Thanks guys !!

---

### Post by kurt18947 on 2013-10-31
Perhaps try installing "hardinfo" from the repositories?  That is fairly informative.

---

### Post by mastablasta on 2013-10-31
lshw command will give plenty info. you can copy and paste it here and people can tell you what needs to be upgraded.

---

### Post by vamsi_spr on 2013-11-01
```
tux_chary@Acharya-ThinkPad-Edge-E430:~$ sudo lshw
[sudo] password for tux_chary: 
acharya-thinkpad-edge-e430
    description: Notebook
    product: 3254CTO (SKU)
    vendor: LENOVO
    version: ThinkPad Edge E430
    serial: MP0RBZW
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad Edge E430 power-on_password=disabled sku=SKU uuid=01E9A859-5952-CB11-A0DA-E20852C0FFD2
  *-core
       description: Motherboard
       product: 3254CTO
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZM4926FA3H
       slot: Not Available
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
          serial: None
          slot: CPU Socket - U3E1
          size: 800MHz
          capacity: 2300MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 3
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 4
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 5
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 2
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 1
             serial: 00E8C469
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: d
          version: H0ET30WW (1.12 )
          date: 05/08/2012
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification uefi
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
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
             resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:6000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:f3600000-f360ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:44 memory:f3615000-f361500f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f361a000-f361a3ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f3610000-f3613fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:5000(size=4096) memory:f2e00000-f35fffff ioport:f0400000(size=8388608)
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:41 memory:f2e00000-f2e00fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:f2d00000-f2dfffff
           *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 74:e5:43:06:36:67
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-32-generic firmware=N/A ip=192.168.0.120 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:4000(size=256) memory:f2d00000-f2d03fff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:f2500000-f2cfffff ioport:f0c00000(size=8388608)
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:f1d00000-f24fffff ioport:f1400000(size=9437184)
           *-network
                description: Ethernet interface
                product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth0
                version: 07
                serial: b8:88:e3:32:cc:76
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f3619000-f36193ff
        *-isa
             description: ISA bridge
             product: HM77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:6088(size=8) ioport:6094(size=4) ioport:6080(size=8) ioport:6090(size=4) ioport:6060(size=32) memory:f3618000-f36187ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f3614000-f36140ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST320LT007-9ZV14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0004
             serial: W0Q4H35K
             size: 298GiB (320GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=576af7d4-dfda-4156-af86-08830a18de2b sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: 8e10-1f80
                size: 95MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI system partition
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: cb6fc323-6e3f-43a8-8d61-1dd65c08a3dc
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 16ae05f8-4ec5-e940-ba1d-3945256588bd
                size: 172GiB
                capacity: 172GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-06-18 23:32:55 filesystem=ntfs label=Windows7_OS modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /
                version: 1.0
                serial: 0ee8d14d-0a10-4780-8663-738a9f86f23a
                size: 12GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-20 12:52:37 filesystem=ext4 lastmountpoint=/ modified=2013-11-01 06:16:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-11-01 06:16:48 name=Basic data partition state=mounted
           *-volume:4
                description: BIOS Boot partition
                vendor: EFI
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                serial: 4f59e782-8112-4a45-8e68-7e258f0708a7
                capacity: 1023KiB
                capabilities: nofs
           *-volume:5
                description: EXT4 volume
                vendor: Linux
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                logical name: /media/tux_chary/b9ba585b-e68f-47dc-b2cd-6697cde63feb
                version: 1.0
                serial: b9ba585b-e68f-47dc-b2cd-6697cde63feb
                size: 1428MiB
                capacity: 1428MiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-20 12:52:40 filesystem=ext4 modified=2013-11-01 06:37:54 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2013-11-01 06:37:54 state=mounted
           *-volume:6
                description: Linux swap volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                version: 1
                serial: 68a4e369-17b1-4271-ab64-b493a091dfb0
                size: 3683MiB
                capacity: 3683MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:7
                description: EXT4 volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                logical name: /media/tux_chary/77f43541-b4b5-4a6a-a28b-7878b2015869
                version: 1.0
                serial: 77f43541-b4b5-4a6a-a28b-7878b2015869
                size: 107GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-14 07:35:47 filesystem=ext4 lastmountpoint=/media/tux_chary/77f43541-b4b5-4a6a-a28b-7878b2015869 modified=2013-11-01 06:37:51 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2013-11-01 06:37:51 state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT50N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: LC01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: 45N1049
       vendor: LGC
       physical id: 1
       slot: Rear
       capacity: 40400mWh
       configuration: voltage=10.8V
```

---

### Post by vamsi_spr on 2013-11-01
> **kurt18947 said:**
> Perhaps try installing "hardinfo" from the repositories?  That is fairly informative.

That worked thanks but what do you think is wrong with the system monitor ??

---

### Post by howefield on 2013-11-01
> **vamsi_spr said:**
> ... but what do you think is wrong with the system monitor ??

Nothing is wrong with system monitor.

Information that you used to find on the system tab can now be found in System Settings > Details.

---

