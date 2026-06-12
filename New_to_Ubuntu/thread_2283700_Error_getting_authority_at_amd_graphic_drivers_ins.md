---
title: "Error getting authority at amd graphic drivers installation"
date: 2015-06-23
forum: New to Ubuntu
---

### Post by Xpdin on 2015-06-23
I am a beginner Linux user

  
I have just installed a new Ubuntu 15.04 from the beginning on HDD.

  
At the first boot it stops on a black screen, and from then it hasn't been working any more...

  
Some people recommend to install the graphic drivers from the terminal 

  
After I tried to install the ad graphic drivers it appears at the end error```
 Error getting authority: Error initializing authority
```

  
Still black screen...

  
Thank you..

---

### Post by mastablasta on 2015-06-24
we will need a bit more data about the system. please see this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)


you should be able to get at least basic VGA mode. see if one of the boot options will help on boot (particulary nomodeset): [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also does it work when you boot into live session (the try it button)?

---

### Post by Xpdin on 2015-06-24
Now I am on a Live USB Stick of Lubuntu 14.04, it has been starting from the Beginning, without me to do something more...

Before installing the new Lubuntu 15.04 from scratch on HDD, I have installed Linux Mint 14, Xubuntu 14, Lubuntu 14.04 which worked normally from the beginning.

Is not from the usb sticks or the isos, because it happened the same with both of the isos mini.iso & Lubuntu 15.04 iso, for both of them i chose to install "Lubuntu Minimal Installation".

On the USB Stick from where I installed Lubuntu 15.04 on my HDD isn't any "try it button" only "install"

I've tried nomodeset, like here : [If you are trying to install Ubuntu ]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076")

And after ctrl+x follow the commands from  [BinaryDriverHowto/AMD]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") - 3.1. Installing via the command line

But in the final when I 
```

sudo amdconfig --initial 
```  It said something about that can't find ... sorry I don't remember exactly.

Here are the help commands, but applied from the Live Stick Lubuntu 14.04, not from the 15.04, because from there I can't copy the results...

```
lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516/M62-S [Mobility Radeon X1350]
```

```
lspci | grep Wireless
``` - no result

```
lspci | grep ATI
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516/M62-S [Mobility Radeon X1350]
```




```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516/M62-S [Mobility Radeon X1350]
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)
```


```
sudo lshw
lubuntu                   
    description: Notebook
    product: ()
    vendor: Hewlett-Packard
    version: F.09
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=103C_5336AN
  *-core
       description: Motherboard
       product: 30D7
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 83.12
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68MDD Ver. F.09
          date: 01/11/2008
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U10
          size: 1867MHz
          capacity: 1867MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst external write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 0
             slot: DIMM #1
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T5663QZ3-CE6
             vendor: Samsung
             physical id: 1
             serial: 7835484C
             slot: DIMM #2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:dc400000-dc4fffff ioport:d0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RV516/M62-S [Mobility Radeon X1350]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:16 memory:d0000000-d7ffffff ioport:4000(size=256) memory:dc400000-dc40ffff memory:dc420000-dc43ffff
        *-network
             description: Ethernet interface
             product: 82562GT 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1f:29:8c:c4:d3
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.1-2 ip=192.168.1.52 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:44 memory:dc500000-dc51ffff memory:dc520000-dc520fff ioport:5000(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5020(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5040(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:dc521000-dc5213ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:dc524000-dc527fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:6000(size=4096) memory:dc000000-dc0fffff ioport:80000000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:dc000000-dc003fff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=8192) memory:d8000000-dbffffff ioport:80200000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:5060(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:5080(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50a0(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:dc528000-dc5283ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:50c0(size=16)
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:5100(size=32) memory:dc529000-dc5297ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-T20L
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: NC08
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54252
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: C32P
             serial: 080423BB3F00WDJ66LRF
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=75ff3e53
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: e8ebb90c-8602-450b-8706-bc65cb2d6a19
                size: 18GiB
                capacity: 18GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-06-22 19:51:40 filesystem=ext4 lastmountpoint=/ modified=2015-06-24 16:18:29 mounted=2015-06-24 16:18:30 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 3815MiB
                capacity: 3815MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3815MiB
                   capabilities: nofs
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: b5bafa66-ae85-4a80-adeb-b74cdd5886d5
                size: 210GiB
                capacity: 210GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-06-22 19:51:43 filesystem=ext4 lastmountpoint=/home modified=2015-06-24 16:18:46 mounted=2015-06-24 16:18:30 state=clean
     *-scsi:2
          physical id: 3
          bus info: usb@2:3
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: Windows FAT volume
             vendor: SYSLINUX
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             logical name: /cdrom
             version: FAT32
             serial: 1b14-296a
             size: 7381MiB
             capacity: 7381MiB
             capabilities: fat initialized
             configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro sectorsize=512 signature=20ac7dda state=mounted
  *-battery
       description: Lithium Ion Battery
       product: HP
       vendor: Hewlett-Packard
       physical id: 1
       version: 07/06/2010
       serial: 03397
       slot: Primary
       capacity: 48000mWh
       configuration: voltage=10.8V
lubuntu@lubuntu:~$ 

```

Thank you..

Have someone any ideas please?

I am stuck between using the Live USB Stick which doesn't work so fast, and trying to make working the last version of Lubuntu-Core(Minimal Installation). Of course I could install the previous version of Lubuntu but, maybe is better the last one.

Have I done something wrong, maybe is a bug?

Thank you.

---

### Post by MartyBuntu on 2015-06-25
There are no proprietary AMD drivers for your video card. Support for older series AMD cards such as yours has been discontinued.
You're stuck with the open source driver.

---

### Post by Xpdin on 2015-06-26
What do you recommend me to do MartyBuntu?

Does this mean that I can't use 15.04 ?

Thank you.

---

### Post by Vladlenin5000 on 2015-06-26
You can use 15.04. What you shouldn't be using, under no circumstance, are outdated, unsupported releases.
Indeed there's no proprietary drivers currently for your graphics card. You'll have to use the open source driver you already have.

---

### Post by mörgæs on 2015-06-26
You are opening a lot of threads regarding the same hardware.

It would be helpful to the posters to keep all of your questions in one or two threads so they don't have to begin from scratch every time.

---

### Post by Xpdin on 2015-06-28
My apologies mörgæs.

```
tasksel
```

helped me.. 


Thank you...

---

