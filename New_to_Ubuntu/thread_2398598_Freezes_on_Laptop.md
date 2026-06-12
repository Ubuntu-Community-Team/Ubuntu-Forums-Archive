---
title: "Freezes on Laptop"
date: 2018-08-14
forum: New to Ubuntu
---

### Post by patrickspiegel on 2018-08-14
Hello, 

I want to switch to Ubuntu. But my Computer freezes in nearly any situation. Shutdown, reboot, sometimes startup, clicking away the after installation dialogue or executing the wrong commands in the shell. 

[https://www.dropbox.com/s/sz2yvb9sbd99t9o/IMG_0294.MOV?dl=0](https://www.dropbox.com/s/sz2yvb9sbd99t9o/IMG_0294.MOV?dl=0)

I have already found this one and tried to edit under /etc/default/grub the cmd_grub_default (or what so ever) and added intel_idle.max_cstate=1 behind the already given quiet parameter. 
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)

What information is required for diagnosis? 

- Computer is a Laptop from MSI (GV72 8RE)

Any kind of help is appreciated.

---

### Post by mörgæs on 2018-08-15
HI, welcome to the fora.

Though you have stated the model number it's often a good idea to post the actual hardware details which may vary, also within the same model number.

Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by patrickspiegel on 2018-08-15
Hello,

I have finally managed to get the output via recovery mode.

```
computer
    description: Notebook
    product: GV72 8RE (179E.1)
    vendor: Micro-Star International Co., Ltd.
    version: REV:1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=notebook family=GV sku=179E.1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: MS-179E
       vendor: Micro-Star International Co., Ltd.
       physical id: 0
       version: REV:1.0
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 1
          version: E179EIMS.107
          date: 05/22/2018
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 3b
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2667 MHz (0,4 ns)
             product: M471A1K43CB1-CRC
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 2667 MHz (0,4 ns)
             product: M471A1K43CB1-CRC
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: 44
          slot: L1 Cache
          size: 384KiB
          capacity: 384KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 45
          slot: L2 Cache
          size: 1536KiB
          capacity: 1536KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 46
          slot: L3 Cache
          size: 9MiB
          capacity: 9MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 47
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          serial: [REMOVED]
          slot: U3E1
          size: 3955MHz
          capacity: 4100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=6 enabledcores=6 threads=12
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Skylake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:a3000000-a40fffff ioport:90000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GP106M [GeForce GTX 1060 Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:4000(size=128) memory:a4000000-a407ffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:a2000000-a2ffffff memory:80000000-8fffffff ioport:5000(size=64) memory:c0000-dffff
        *-generic
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:16 memory:a4322000-a4322fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:123 memory:a4300000-a430ffff
        *-memory UNCLAIMED
             description: RAM memory
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:a431a000-a431bfff memory:a4321000-a4321fff
        *-network
             description: Wireless interface
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             logical name: wlo1
             version: 10
             serial: [REMOVED]
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-30-generic firmware=34.0.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
             resources: irq:16 memory:a4314000-a4317fff
        *-communication:0
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:125 memory:a4320000-a4320fff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:124 memory:a4318000-a4319fff memory:a431f000-a431f0ff ioport:5090(size=8) ioport:5080(size=4) ioport:5060(size=32) memory:a431e000-a431e7ff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:3000(size=4096) memory:a4200000-a42fffff
           *-network
                description: Ethernet interface
                product: QCA8171 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 10
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
                resources: irq:19 memory:a4200000-a423ffff ioport:3000(size=128)
        *-communication:1
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:20 memory:a431d000-a431dfff
        *-isa
             description: ISA bridge
             product: Intel Corporation
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
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:140 memory:a4310000-a4313fff memory:a4100000-a41fffff
        *-serial:0 UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 10
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a431c000-a431c0ff ioport:efa0(size=32)
        *-serial:1 UNCLAIMED
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 10
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe010000-fe010fff
     *-scsi:0
          physical id: 0
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MZNLN256
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 100Q
             serial: [REMOVED]
             size: 238GiB (256GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=67596db1-ddf2-42d3-bf27-c77a603c6a4e logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 448MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2018-08-12 22:40:51 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 93MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                serial: [REMOVED]
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: [REMOVED]
                size: 93GiB
                capacity: 93GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-08-12 22:40:55 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@1:0.0.0,5
                logical name: /dev/sda5
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 144GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2018-08-14 21:31:12 filesystem=ext4 lastmountpoint=/ modified=2018-08-15 17:30:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-08-15 17:29:21 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10SPZX-17Z
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1A01
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=d200a814-de91-4bdd-a876-fe15466a3c03 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: [REMOVED]
                size: 912GiB
                capacity: 912GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-03-15 00:37:26 filesystem=ntfs label=Data modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                vendor: Windows
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: [REMOVED]
                size: 19GiB
                capacity: 19GiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2018-03-15 00:37:28 filesystem=ntfs label=BIOS_RVY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:2
          physical id: 3
          bus info: usb@2:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             serial: [REMOVED]
             size: 14GiB (15GB)
             capabilities: removable
             configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 14GiB (15GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=056262a3
              *-volume
                   description: Windows FAT volume
                   vendor: SYSLINUX
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/patrick/UBUNTU 18_0
                   version: FAT32
                   serial: [REMOVED]
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=UBUNTU 18_0 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh
```

---

### Post by mörgæs on 2018-08-16
The bug report to which you linked deals with problems for Bay Trail, which is a processor series in the power-saving Atom family.

You have a much newer Coffee Lake processor in the high-performing Core family. The boot option 
intel_idle.max_cstate=1
may or may not have a significance here, I don't know. 

Your BIOS is up to date.

As your processor is about as new as it gets I suggest that you first try a live boot of Ubuntu 18.10 (development release) for comparison. You can download it here:

[http://cdimage.ubuntu.com/ubuntu/daily-live/pending/](http://cdimage.ubuntu.com/ubuntu/daily-live/pending/)

---

