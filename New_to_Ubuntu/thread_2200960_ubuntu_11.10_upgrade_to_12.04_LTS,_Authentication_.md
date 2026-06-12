---
title: "ubuntu 11.10 upgrade to 12.04 LTS, Authentication failed message"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by handysmurf on 2014-01-22
dialog box shows:
downloading the release upgrade tool
     File one of two downloading....  Then:

Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server. 

Have tried "upgrade" several times... same results each time.

---

### Post by fantab on 2014-01-22
11.10 is dead. Its not supported anymore. There are no repos for 11.10 to support the upgrade.
Follow this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If I were you, I would do a fresh and clean install of 12.04, better sitll wait for the 14.04 to release this April and meanwhile use 13.10. Fresh install is any day a better option.
I hope your DATA is well backed up...

---

### Post by handysmurf on 2014-01-23
wow! that's a real drag...  i had the update manager set to notify me of LTS versions, and it never showed any...  all i know is it stopped showing any updates a few weeks back.
i changed the setting to show any update, and THEN it shows me 12.04!  (which it won't do).

    So, anyway, what do you think of ubuntu studio 13.04?  and how do I determine if i'm suppose to be able to use the AMD64 version?  I thought I saw some mention of that in one of the files on this laptop, but i don't remember where.

---

### Post by deadflowr on 2014-01-23
> [COLOR=#000000]So, anyway, what do you think of ubuntu studio 13.04? and how do I determine if i'm suppose to be able to use the AMD64 version?[/COLOR]

Two parter.

First, if you are going to upgrade, go up to 13.10.
13.04(raring) is only going to be supported for a few more weeks(actually support is suppose to end at the end of January). 

Second, the amd64 means for a computer that can run 64-bit.
Most machines built within the last five years are(but not all) 64-bit capable.
If you are unsure post the output of this 
```
sudo lshw -sanitize > lshw.txt

```

---

### Post by fantab on 2014-01-24
13.10 is what you should install.
Ubuntu Studio 13.10 is fantastic if you use media/graphics editing software. It uses Xfce by default.

If you have 64bit processor then you must install amd64 version of Ubuntu if not then 32bit.

---

### Post by handysmurf on 2014-01-24
i made backup image, and the backup program named it "ubuntu-11.10-amd64-dell_A00"...   anyway, here's the output:

computer
    description: Portable Computer
    product: Vostro 2420 (To be filled by O.E.M.)
    vendor: Winbond Electronics
    version: Not Specified
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=portable sku=To be filled by O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0KHJFD
       vendor: Winbond Electronics
       physical id: 0
       version: A05
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A05
          date: 09/28/2012
          size: 64KiB
          capacity: 1984KiB
          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     *-memory:0 UNCLAIMED
          physical id: 1
        *-bank UNCLAIMED
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT351S6CFR8C-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_B
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-memory:1 UNCLAIMED
          physical id: 2
        *-bank UNCLAIMED
             description: DIMM [empty]
             product: Not Specified
             vendor: Not Specified
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A
     *-memory:2
          description: System Memory
          physical id: 7
          slot: System board or motherboard
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 27
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz
          slot: SOCKET 0
          size: 800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: 6
             slot: CPU Internal L3
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: CPU Internal L2
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 4
             slot: CPU Internal L1
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through data
     *-memory:3 UNCLAIMED
          physical id: 3
     *-memory:4 UNCLAIMED
          physical id: 4
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
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
             resources: irq:42 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:f7d0a000-f7d0a00f
        *-usb:0
             description: USB Controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7d08000-f7d083ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f7d00000-f7d03fff
        *-pci:0
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f7c00000-f7cfffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-32-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
        *-pci:2
             description: PCI bridge
             product: Panther Point PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:e000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 07
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:40 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-usb:1
             description: USB Controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7d07000-f7d073ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Panther Point 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi4
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7d06000-f7d067ff
           *-disk
                description: ATA Disk
                product: WDC WD5000LPVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e9e206ca
              *-volume:0
                   description: Windows FAT volume
                   vendor: Winbond Electronics
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: [REMOVED]
                   size: 286MiB
                   capacity: 298MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows FAT volume
                   vendor: Winbond Electronics
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: FAT32
                   serial: [REMOVED]
                   size: 3058MiB
                   capacity: 3076MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=Unlabeled
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 462GiB
                   capacity: 462GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-12-19 01:48:11 filesystem=ext4 lastmountpoint=/ modified=2014-01-03 18:56:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,stripe=1,data=ordered mounted=2014-01-23 19:28:02 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW SN-208BB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D500
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d05000-f7d050ff ioport:f040(size=32)
  *-battery
       description: Lithium Ion Battery
       product: DELL 4YRJH2B
       vendor: SANYO
       physical id: 1
       serial: [REMOVED]
       slot: Sys. Battery Bay
       capacity: 45000mWh
       configuration: voltage=10.8V

---

### Post by deadflowr on 2014-01-24
Yeah, you can download the 64-bit version.
(That's the amd64)

---

### Post by handysmurf on 2014-01-24
[**[COLOR=#000000]fantab[/COLOR]**]("http://ubuntuforums.org/member.php?u=1275004")... Thank you very much for your input
[**[COLOR=#000000]deadflowr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276577")... Thank you very much for your guidance, time, and insight, and for walking me through this.

I've got everytrhing backed up, and with both you guys help, i'm now ready to make the plunge... if all goes well, i'll see you on the other side...

I have installed ubuntustudio 13.10, updated everything, and looks like everything is: happy happy happy!

---

