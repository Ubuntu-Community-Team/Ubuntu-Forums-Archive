---
title: "Post Ubuntu Installation: Details of Non-OS Software Installation, Hardware, Etc..."
date: 2021-12-28
forum: New to Ubuntu
---

### Post by linux-noobie2 on 2021-12-28
Hello Everybody, I'm linux-noobie2, or at least for now as linux-noobie2.

I had a free Ubuntu 8 "Hardy Heron" disc. Its driver support consists of dialup, or at least what it can support my given hardware at the time. I went back to Windows and moved on, until I decided to try a 64 bit security software, which was not a good idea for my 32 bit Windows OS. The application happened to configure with my boot loader. It was the end of Windows (BSOD) for my current computer. I started using Ubuntu 8 again and at least it still has some life left. I tried burning a new version into DVDs, but I cannot make the boot recognize the disc/DVD during startup. I decided that my computer does not have such capabilities.

I bought a USB with 17.04 and 18.04, both 64 bit, I was pretty nervous. Fortunately, it works! Even better, it has preloaded drivers with wide support range for plenty of hardware components. I was in the clear for progress! However, the help section wasn't as helpful or detailed. It got GUI, but no TUI navigation.

Anyways, toward the problems!

*Figure out how to install offline...
Manual installation path? The automated installation is a bit cluttered...
I couldn't really get all of the information in terms of the download and installation queries. I also see that the checksum is sometimes necessary as well. I am referencing from both Wine and Slade as cited examples.

Wine> **----------------- On Ubuntu & Linux Mint -----------------** 
$ sudo dpkg --add-architecture i386    [Enable 32-bit Arch]
$ wget -nc https://dl.winehq.org/wine-builds/winehq.key
$ sudo apt-key add winehq.key
$ sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ focal main'  [**Ubuntu 20.04 & Linux Mint 20**]
$ sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main' [**Ubuntu 18.04 & Linux Mint 19.x**]
$ sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main' [**Ubuntu 16.04 & Linux Mint 18.x**]


$ sudo apt-get update
$ sudo apt-get install --install-recommends winehq-stable$ sudo add-apt-repository ppa:cybermax-dexter/sdl2-backport
$ sudo apt-get update
$ sudo apt-get install --install-recommends winehq-stable

SLADE> sudo apt-add-repository 'deb http://debian.drdteam.org/ stable multiverse' wget -O- http://debian.drdteam.org/drdteam.gpg | sudo apt-key add -
sudo apt-get update
sudo apt-get install slade

I, on the other hand, just know how to use the following commands.
> sudo apt(-get) install "./filename" or "~/...directories/directories/directories.../filename" or "*/filename"
?xdg-open INSTALL.fileformat/REAMD.fileformat
sudo apt install -f
dpkg --list
sudo apt-get --purge remove "gimp"
sudo apt autoremove


Stuff like 
sudo add-apt-repository main
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt-get update

needs some detailing.

*See if hardware graphics are enabled
Device manager? How?

*If antivirus or the like is necessary

*Check for requirements and downloading recent version of Wine?

*The best of linux games? Dos? Amiga? PC98? Windows emulation? Oldies?
*Is it true that ubuntu and debian are different from other brands? If so, how?

And more to come! I'll be back.

---

### Post by grahammechanical on 2021-12-28
If you really are using Ubuntu 08.04 then you are using an operating system that has long ago reached end of supported life. It matters not if it runs on your hardware. You will not get any security fixes. You will not be able to install any additional software. The reason? All software for Ubuntu is stored in repositories on Ubuntu computer servers. These repositories have internet addresses linked to the Ubuntu version number. When a version of Ubuntu reaches End of Life those repositories are moved. So, the internet addresses that Ubuntu 08.04 has for its repositories is now inaccurate.

Please give details of your hardware and we can recommend a version of Ubuntu or its flavours that will be suitable for your machine.

Regards

---

### Post by linux-noobie2 on 2021-12-28
[SIZE=3]Hello grahammechanical,

R[/SIZE][SIZE=3]epositories can just be updated so it is not much of a problem. As for getting new versions, 
I already bought and installed Ubuntu 18.04 (for Wine v3 support). I was trying to get a 32 bit version, but to no avail. It's no problem, as my 64 bit supporting computers are the more to wrangle with. Could you allow access to the software url for manual download? I don't really like just automatic downloading. Some of the files I want might be in different versions, alpha state, or etc. I would like to collect and compile compressed packages of .deb, .rpm, or etc. They would be for offline use. I also need to know how to download custom/specific directory path and extract/install the packages to custom/specific directory path. I know it's not much of a big deal for Ubuntu itself, but there are non-OS softwares that don't take [/SIZE][SIZE=3][SIZE=3]custom/specific directory paths into consideration. [/SIZE]Anyways, the code section below entails the hardware specifications of my deemed computer. I'm not sure how the data would be helpful, but here you go!

Video Card
lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

Wireless Card
lspci | grep Wireless
[/SIZE][SIZE=3]```
n/a, but I can the hardware. Plus the OS is perusing another driver to work with it.
```[/SIZE][SIZE=3]An exhaustive, detailed list of hardware:
Careful, it's quite the detail!
[/SIZE]```
[FONT=courier new][SIZE=3]description: Space-saving Computer
    product: OptiPlex 780
    vendor: Dell Inc.
    serial: 7KYPMM1
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=space-saving power-on_password=enabled uuid=44454C4C-4B00-1059-8050-B7C04F4D4D31
  *-core
       description: Motherboard
       product: 03NVJ6
       vendor: Dell Inc.
       physical id: 0
       version: A01
       serial: ..CN7360406F0583.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A15
          date: 08/06/2013
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: CPU
          size: 3GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm pti tpr_shadow vnmi flexpriority dtherm
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 6MiB
             capacity: 6MiB
             capabilities: internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: M378B5673FH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 635BA108
             slot: DIMM_1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns) [empty]
             vendor: FFFFFFFFFFFF
             physical id: 1
             serial: FFFFFFFF
             slot: DIMM_3
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: M378B5673FH0-CH9
             vendor: Samsung
             physical id: 2
             serial: 635BA15F
             slot: DIMM_2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns) [empty]
             vendor: FFFFFFFFFFFF
             physical id: 3
             serial: FFFFFFFF
             slot: DIMM_4
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 memory:f7900000-f79fffff
        *-display:0
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f7c00000-f7ffffff memory:e0000000-efffffff ioport:ecb0(size=8) memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f7b00000-f7bfffff
        *-communication:0
             description: Communication controller
             product: 4 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:32 memory:feda6000-feda600f
        *-ide
             description: IDE interface
             product: 4 Series Chipset PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi pci_native_mode-only_controller__supports_bus_mastering bus_master cap_list
             configuration: driver=ata_generic latency=0
             resources: irq:18 ioport:fe80(size=8) ioport:fe90(size=4) ioport:fea0(size=8) ioport:feb0(size=4) ioport:fef0(size=16)
        *-communication:1
             description: Serial controller
             product: 4 Series Chipset Serial KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:ecb8(size=8) memory:f7ad8000-f7ad8fff
        *-network
             description: Ethernet interface
             product: 82567LM-3 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 02
             serial: b8:ac:6f:ae:49:7d
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.4-3 ip=192.168.1.244 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:30 memory:f7ae0000-f7afffff memory:f7ad9000-f7ad9fff ioport:ece0(size=32)
        *-usb:0
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.4.0-91-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.4.0-91-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:fc00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.4.0-91-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:f7ada000-f7ada3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-91-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: Generic USB device
                   product: 802.11n NIC
                   vendor: Realtek
                   physical id: 4
                   bus info: usb@1:4
                   version: 0.00
                   serial: 00E04C0001
                   capabilities: usb-2.00
                   configuration: driver=r8188eu maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 82801JD/DO (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:33 memory:f7adc000-f7adffff
        *-pci:1
             description: PCI bridge
             product: 82801JD/DO (ICH10 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:f7800000-f78fffff ioport:fc000000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801JD/DO (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:f7700000-f77fffff ioport:fc200000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff80(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.4.0-91-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff60(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.4.0-91-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.4.0-91-generic uhci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@8:1
                   version: 54.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: SIGMACHIP
                   physical id: 2
                   bus info: usb@8:2
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
        *-usb:7
             description: USB controller
             product: 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ff980000-ff9803ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-91-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801JDO (ICH10DO) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: RAID bus controller
             product: SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:31 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=32) memory:ff970000-ff9707ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JD/DO (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7adb000-f7adb0ff ioport:980(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160318AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: HP34
             serial: 5VY3F6VW
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=fe6f54be
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: c720201f-39dc-4119-9a35-eb3074579acb
                size: 731MiB
                capacity: 731MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2021-12-25 08:42:24 filesystem=ext4 lastmountpoint=/boot modified=2021-12-28 16:15:43 mount.fstype=ext4 mount.options=rw,relatime mounted=2021-12-28 16:15:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 148GiB
                capacity: 148GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: 3d1ae14a-90ce-4c95-88ca-e4f11ad85b1d
                   size: 148GiB
                   capacity: 148GiB
                   width: 512 bits
                   capabilities: encrypted luks initialized
                   configuration: bits=512 cipher=aes filesystem=luks hash=sha256 mode=xts-plain64 version=1
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM DV-28SW
             vendor: TEAC
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: D.2F
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlxc025e9cb477e
       serial: c0:25:e9:cb:47:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociated[/SIZE][SIZE=3]
[/SIZE][/FONT]
```

---

