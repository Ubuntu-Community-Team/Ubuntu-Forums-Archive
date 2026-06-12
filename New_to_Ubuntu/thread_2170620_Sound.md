---
title: "Sound"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by louh2 on 2013-08-26
So.  Here I am, a lone home recording enthusiast, hoping that all my problems with Microsoft will be over and I can get back to actually recording music again.  Lots of promise in this particualr flavor of Linux.  There's only one small problem...I don't know what to do to get started.  I have successfully setup a dual boot US 12.04 with Win 7.  Unfortunately I am not getting any sound.  I read some place that pulse audio could be a problem and there were some command lines to delete it and now I have ALSA unpacked on my desktop but I have no fricken idea how to install it.  Could someone be a real sport and help me get things moving here?  Yeah, I don't know much about command line arguments but I'm guessing I'm gonna be real smart about them in the near future.

AMD quad core cpu
M-Audio Delta Audiophile 2496

---

### Post by bkline on 2013-08-26
You probably already have ALSA installed.  If you're really eager to get started with the command line, here's your chance!  Open up a command window (control+alt+T if you did a default Ubunutu install) and type in

dpkg -l | grep alsa

(the symbol right in front of "grep" is the character you get if you hold down the shift key while pressing the \ key just above the Enter key).

If you see a bunch of lines, you've got ALSA already installed (as you should, with the default installation).

---

### Post by louh2 on 2013-08-26
Ok, so that's done.  But I'm still not getting any sound output.  I tried setting up Jack but it says "JACK can only be configured with a loaded and stopped studio. Please create a new studio or load and stop an existing one."  What studio needs to be setup and then stopped?  Also when I try to play a song it puts up the following ALSA error "snd_mixer_attach failed: No such file or directory.
snd_pcm_open failed: No such file or directory."  I've probably gone and effed this installation up real good.  Maybe reinstall and start fresh?

---

### Post by su:bhatta on 2013-08-27
Hi, louh2! I am also a beginner in this ! Have you installed Ubuntu or the Ubuntu Studio 12.04?

---

### Post by mastablasta on 2013-08-27
post output form lspci and lshw 
commands so we can see what chip you have

---

### Post by louh2 on 2013-08-27
This install is Ubuntu Studio 12.04


Here is the info from those 2 commands:
```

lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS740 [Radeon 2100]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
03:05.0 Network controller: Qualcomm Atheros AR9227 Wireless Network Adapter (rev 01)
03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

lshw
XXXXXXXX-computer
    description: Desktop Computer
    product: To Be Filled By O.E.M. (RS740M04-6KRS2H)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=RS740M04-6KRS2H uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A74ML-K
       vendor: FOXCONN
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014
          date: 04/14/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X4 645 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) II X4 645 Processor
          serial: To Be Filled By O.E.M.
          slot: Socket 940
          size: 800MHz
          capacity: 3100MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=4 enabledcores=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 30
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:fe800000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS740 [Radeon 2100]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:18 memory:d0000000-dfffffff memory:fe9f0000-fe9fffff ioport:b000(size=256) memory:fe800000-fe8fffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:fea00000-feafffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 90:fb:a6:23:83:16
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:c800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feae0000-feafffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=8) ioport:7000(size=4) ioport:6000(size=16) memory:fe7ff800-fe7ffbff
           *-disk
                description: ATA Disk
                product: WDC WD2500AVVS-6
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAV11262455
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=aaaaaaaa
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 343a-bcb0
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2013-07-24 20:15:35 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/Lou's Disk 1
                   version: 3.1
                   serial: 7a60f44e-de23-4f49-85f4-60c913e47b68
                   size: 193GiB
                   capacity: 193GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2013-07-24 20:16:02 filesystem=ntfs label=Lou's Disk 1 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 32GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /boot
                      capacity: 2860MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 3759MiB
                      capabilities: nofs
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe7fe000-fe7fefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe7fd000-fe7fdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe7ff000-fe7ff0ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe7fc000-fe7fcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe7fb000-fe7fbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe7fa800-fe7fa8ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-111D
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@5:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.23
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:d000(size=8192) memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: AR9227 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 5
                bus info: pci@0000:03:05.0
                logical name: wlan0
                version: 01
                serial: f8:d1:11:6e:68:d4
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-52-lowlatency firmware=N/A ip=192.168.1.2 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:20 memory:febf0000-febfffff
           *-multimedia
                description: Multimedia audio controller
                product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
                vendor: VIA Technologies Inc.
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=oss_envy24 latency=64
                resources: irq:21 ioport:e800(size=32) ioport:e400(size=16) ioport:e000(size=16) ioport:d800(size=64)
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe7f9000-fe7f9fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
```

---

### Post by su:bhatta on 2013-08-27
Ok, with Ubuntu Studio, did you set up jack ?
Suggest you have a look at these two pages:

[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Have you tweaked with the system too much? otherwise you dont really need a fresh install...

---

### Post by louh2 on 2013-08-27
Yeah, I think a reinstall here is probably what is in store.  I kept reading things from all sorts of people, people with more and less knowledge and experience, and there is much about the removal of pulse audio and so I followed this fellows post, [http://ubuntuforums.org/showthread.php?t=1783096](http://ubuntuforums.org/showthread.php?t=1783096), to get ALSA mixer installed and there was an error near the end and now I keep getting crash reports when trying to configure sound card in ALSA mixer.  I'm really trying hard here, I should be in bed it is 3:30am here and I work tomorrow but just trying to get a simple thing like some audio playback is a tremendous project.  Also, because the levels of knowledge and experience vary, so too will be the error rates when carrying out instructions I think.  I can see the positive value of Ubuntu Studio in terms of audio recording and I desperately want it to work but this is almost too much for a newb like myself to partake in.  I hate MS with a passion but at least I can play music there, recording is a different matter.  Is there a way for me to post system info so you could tell whether I need to reinstall?  Anything I can post system wise that will help you help me?  I'm stuck and in despair, I have some really great ideas music wise right now and the time is being wasted installing and setting and tweaking, I'm bitching and I know it but just frustrated!

---

### Post by mastablasta on 2013-08-27
12.04 huh? how about newer kernel.

anyway this is the sound chip
```
03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

``````

*-multimedia
description: Multimedia audio controller
product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
vendor: VIA Technologies Inc.
physical id: 6
bus info: pci@0000:03:06.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=oss_envy24 latency=64
resources: irq:21 ioport:e800(size=32) ioport:e400(size=16) ioport:e000(size=16) ioport:d800(size=64)


```

this will help search for an answer. i found this: [https://apps.ubuntu.com/cat/applications/oneiric/mudita24/](https://apps.ubuntu.com/cat/applications/oneiric/mudita24/)
a user got it working (but i don't understand the audio talk...): [http://ubuntuforums.org/showthread.php?t=2121587](http://ubuntuforums.org/showthread.php?t=2121587)
similar here (how to check and setup - with some solution for no sound): [http://ubuntuforums.org/showthread.php?t=1763274](http://ubuntuforums.org/showthread.php?t=1763274)

---

### Post by louh2 on 2013-08-27
I have Mudita24 installed which is supposed to work for my sound card but when I click on it nothing happens.  The checks and setup assume that you can get to a user interface which I am still unable to get to.

---

### Post by grahammechanical on 2013-08-27
There is a section on the forum specifically for Ubuntu Studio. So, if the issue is with applications in Ubuntu studio that section might give you access to people more qualified to help.

[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

This section is for Absolute Beginners, which you are as regards Ubuntu but not in the matter of Audio Software. On the other hand I have absolutely no experience with Audio software.

If I remember, Ubuntu 12.04 installs with sound muted. See, I can suggest absolute beginner solutions like click the sound icon and making sure sound is unmuted. Or doing it through Sound Settings - See sound icon menu.

Anyway, please confirm that sound is not working when you try to play an audio file using the default music player - RhythmBox?

Oh, one more thing. I have just seen your earlier post

[http://ubuntuforums.org/showthread.php?t=2170632](http://ubuntuforums.org/showthread.php?t=2170632)

It is the same problem is it not? Please do not ask the same question twice. It diversifies effort. I feel like I have wasted my time writing this post.

Regards.

---

### Post by su:bhatta on 2013-08-27
Are you sure you have to get rid of PulseAudio, I keep mine and recorded live , there was no problems...
Stick to wiki and known resources(like app websites for Ardour,mudita, jack etc e.g. : [http://code.google.com/p/mudita24/](http://code.google.com/p/mudita24/)) 

RhythmBox ain't the player in ubuntuStudio!
Also, I dont know what kernel 12.04 uses, but my 13.04 was last using 3.9.0-something lowlatency, where as the Saucy Development releae straightway gave me 3.11.0-2 lowlatency, 

Go for 13.04 i suggest,
Also, I have been in your kind of shoes 3 months back, getting frustrated is right, but you hafta to take one hurdle at a time...
First read up trac.jack.org, it is very useful,

best of luck, you will get it working for sure

---

### Post by louh2 on 2013-08-27
Well, decided to delete the current installation and reinstall.  Everything, so far, seems to be working.  There is sound output, Mudita24 comes up and has all the faders for the various ins and outs.  QJackCtl is working so I can begin to create a patchbay of sorts.  Hydrogen even makes a connection to my drum machine so I know MIDI is working too.  Lots of stuff to setup but I think the first install was just buggy or didn't install properly.  In any event thanks all for the help.  Maybe I ought to get to bed and get a half hour of sleep before getting up and going to work?  I think some strong java is in order for the day.
Night

---

### Post by Crusty Old Fart on 2013-08-27
> **louh2 said:**
> Well, decided to delete the current installation and reinstall...
It's amazing how much time we spend on wild goose chases when a tainted kernel is resisting every fix we attempt. At some point the machine wins and we reinstall.
I've learned from experience that tainted kernels are a good reason to reinstall. Now, one of the first things I do with every new installation, as soon as the machine boots, is to run the following command:
```

dmesg | grep -i taint

```
If you don't get any output, then the kernel isn't tainted.
If you get some output, look for notices of a tainted kernel.

Best wishes,

Crusty

---

### Post by su:bhatta on 2013-08-28
What to do if the output is as follows:

```
dmesg | grep -i taint
[   20.729375] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.729382] Disabling lock debugging due to kernel taint
[   20.756297] fglrx: module verification failed: signature and/or required key missing - tainting kernel
```

But this is from developmental Branch, UStudio Saucy Alpha2!

---

### Post by Crusty Old Fart on 2013-08-28
Did you install a proprietary graphics driver?

---

### Post by su:bhatta on 2013-08-28
I did, coz otherwise i dont get right screen resolution or colors et al! Fglrx is installed!

---

### Post by Crusty Old Fart on 2013-08-28
It's basically saying that you forgot to install the vendor's (ATI) certification key before you installed the driver.
If it's giving you any grief, you could remove the driver, install the certification key, and then install the driver.
But, that may not be an option if you don't have the key.
If it isn't causing you any problems, you could choose to ignore it
~~~ or ~~~
If you'd like, I'd be happy to take a look at the full dmesg output:
```

dmesg

```
And also your hardware list:
```

sudo lshw

```
This might be good to see as well:
```

lspci -tvv

```

---

### Post by su:bhatta on 2013-08-28
It's not givin any problem, but I can provide you the details! 
But I dont wanna hijack this thread ;)

I am starting one of my own! Please hav a look at the Absolute Beginners Section! Thanks!

---

