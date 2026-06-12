---
title: "Installing fglrx - struggling following guide or improving graphical performance"
date: 2017-04-11
forum: New to Ubuntu
---

### Post by random turnip on 2017-04-11
Hi,

I've got an old laptop (Packard Bell SL51-B122) which uses an ATI Radeon HD3100 GPU (I think).  The performance is fairly poor on things like watching videos or playing basic or old games so I want to try and install a different driver.  I'm currently trying to follow [this]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") guide on Ubuntu Community.  

In the guide stap 2.3 says "Identify whether your AMD graphics card model series is supported by the fglrx driver. If the search returns the latest version of the Catalyst driver, then proceed to the next section. If the search returns a legacy version, you may have to use the open source driver."  When I search the site I get [this]("http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64") page, which I guess means I just have to use the driver currently installed?  Is there anything else I can do to improve performance?  I don't expect much out of a 512mb gpu, but I should be able to watch videos and play some simple 2D indie games.

---

### Post by Bashing-om on 2017-04-11
random turnip; Hey !

What release do you have ?
Be aware that 16.04++'s kernels no longer have proprietary (FGLRX) support as AMD has gone full bore to support open source .

[INDENT][INDENT]it is a big thing
[/INDENT][/INDENT]

---

### Post by QIII on 2017-04-11
Regardless of your Ubuntu release, fglrx will not work with that card and has not for many years.

Anything older than HD 5000 series cards lost support.

And, as indicated, fglrx does not work from 16.04 forward.

Edit:  I have updated the wiki article with a much stronger warning and a bit of clarification up front.

---

### Post by mastablasta on 2017-04-12
you can now only check if the opensource driver is propperly loaded and functioning well (the troubleshooting section in the opensource driver wiki)

---

### Post by mörgæs on 2017-04-12
> **random turnip said:**
> Is there anything else I can do to improve performance?

Let's see the hadware details. Please copy the command ```
sudo lshw -sanitize > lshw.txt
``` into the terminal and post the resulting lshw.txt in CODE tags.

---

### Post by random turnip on 2017-04-12
Thanks for all the replies guys.
> **Bashing-om said:**
> random turnip; Hey !

What release do you have ?
Be aware that 16.04++'s kernels no longer have proprietary (FGLRX) support as AMD has gone full bore to support open source .

[INDENT][INDENT]it is a big thing
[/INDENT][/INDENT]
Hi!

I have 16.04, freshly installed a few days ago.
Excellent that they have gone full open source for sure, but what does that mean for older cards?  Are they no longer available unless someone decides to code one?
> **QIII said:**
> Regardless of your Ubuntu release, fglrx will not work with that card and has not for many years.

Anything older than HD 5000 series cards lost support.

And, as indicated, fglrx does not work from 16.04 forward.

Edit:  I have updated the wiki article with a much stronger warning and a bit of clarification up front.
What exactly does it mean by "lost support"?  Simply that it doesn't get updates or that it won't work with newer updated systems at all?
> **mastablasta said:**
> you can now only check if the opensource driver is propperly loaded and functioning well (the troubleshooting section in the opensource driver wiki)
Thanks, will check this.
> **mörgæs said:**
> Let's see the hadware details. Please copy the command ```
sudo lshw -sanitize > lshw.txt
``` into the terminal and post the resulting lshw.txt in CODE tags.
Ok, here goes:
```

computer
    description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-06-27 17:08+0000X-Generator: Launchpad (build 18115)
    product: EasyNote SL51
    vendor: Packard Bell BV
    version: PC25Q02301
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=oem-specific uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PF2
       vendor: Packard Bell BV
       physical id: 0
       version: Rev 1
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: PBPF1200.P11
          date: 10/24/2008
          size: 107KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-72
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: Engineering Sample
          slot: Socket S1G2
          size: 2100MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid eagerfpu pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit hw_pstate vmmcall lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             physical id: 1
             slot: S2
             size: 1GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:cfd00000-cfefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780MC [Mobility Radeon HD 3100]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff memory:c0000-dffff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:a000(size=4096) memory:c0400000-c04fffff ioport:f0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:28 ioport:a000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:c0400000-c041ffff
        *-pci:3
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:c0500000-c06fffff ioport:c0700000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f0200000-f02fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:0a:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:f0201400-f02014ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:0a:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f0201800-f02018ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:0a:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:f0201c00-f0201cff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8430(size=8) ioport:8424(size=4) ioport:8428(size=8) ioport:8420(size=4) ioport:8400(size=16) memory:f0308000-f03083ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:f0304000-f0304fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.8.0-46-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:f0305000-f0305fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.8.0-46-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f0308400-f03084ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-46-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: FE03FF-99-1
                   vendor: Foxlink
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.04
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Generic USB device
                   product: RTL8187B_WLAN_Adapter
                   vendor: Manufacturer_Realtek
                   physical id: 5
                   bus info: usb@1:5
                   version: 2.00
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rtl8187 maxpower=500mA speed=480Mbit/s
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f0306000-f0306fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.8.0-46-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f0307000-f0307fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.8.0-46-generic ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:f0308800-f03088ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-46-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
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
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8410(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f0300000-f0303fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=06274a0d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 230GiB
                capacity: 230GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2017-04-08 21:04:38 filesystem=ext4 lastmountpoint=/ modified=2017-04-12 21:35:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-04-11 20:22:32 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2813MiB
                capacity: 2813MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2813MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-T50N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: RP05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlx0017c458b438
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=4.8.0-46-generic firmware=N/A ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11

```

---

### Post by mörgæs on 2017-04-12
The hardware is fine according to my standards. Have you considered a fresh install of Lubuntu?

---

### Post by random turnip on 2017-04-13
What's the difference between Ubuntu and Lubuntu?  I could do it, I guess now would be the time since I haven't got all that much installed right now.

---

### Post by mastablasta on 2017-04-13
You can try it before you install it by using live session.
the main difference is the interface. while Ubuntu needs 3D acceleration for it Lubuntu uses 2D drawing to draw the GUI. this means it doesn't need much resources from the graphics chip. 

you can actually add Lubuntu to Ubuntu if you wish. you will then select it at the beginning, but bare in mind that some services might double then (maybe some network manager or similar) a way arround this is for example to add lxde package rather than whole Lubuntu desktop desktop.

if you want to install (add) Lubuntu to current instalation just search for package lubuntu-desktop in software center.


in windows the WinXP had 2D desktop, while Win7 with Aero needs 3D acceleration to draw it.

Other linux desktops that work nicely and with 2D acceleration are XFCE (found in Xubuntu) and Mate (Ubuntu Mate). KDE (Kubuntu) can also be made to run in "2D" mode by removing various desktop effect in options. though it iwll still take up more ram than the others.I am not sure if the option still exists in 16.04, but in 14.04 there were low-fat packages available which made it light and it just flew on old machines.

in any case choosing and using a lighter desktop environment will free up the GPU for other tasks.


however, you still need to see if you actually have hardware graphics acceleration (the GPU does the drawing stuff) or software graphics acceleration  (the CPU+RAM does the drawing, which is much slower than if the GPU is doing it). software acceleration + light desktop environment will work reasonably well for internet browsing, but will be terrible for nearly any kind of games or other GPU intensive tasks.

---

### Post by random turnip on 2017-04-13
Is there a simple way to check if i'm using hardware acceleration?  Looking on google right now and seen a few different ways, but they all seem to either refer to Intel chips or fglrx, so not applicable to me.

Will using a lighter environment really help in a game when all that it only running in the background anyway?

---

### Post by deadflowr on 2017-04-13
Install mesa-utils and run
```
glxinfo | grep render
```

---

### Post by random turnip on 2017-04-16
Thanks.  It came back with the following:
[ATTACH=CONFIG]274582[/ATTACH]

I take it from the "direct rendering: yes" that it means it's working and I've just got to put up with it?

---

### Post by Yellow Pasque on 2017-04-16
Yes, the driver is fine and you have 3D hardware acceleration.
You may be able to get better video plaback:
```
sudo apt-get install vdpauinfo mesa-vdpau-drivers mpv
```
Then, try to play a video:
```
mpv --hwdec=vdpau videofilename
```

> I take it from the "direct rendering: yes" that it means it's working and I've just got to put up with it? 
Other than using a lighter desktop and the tip above, I don't know what else will help you. The Radeon 3100 is not a powerful GPU and I've seen others complain about its performance.

> The hardware is fine according to my standards. Have you considered a fresh install of Lubuntu? 
Yeah, the hardware should handle lubuntu, ubuntu mate or xubuntu.
Just avoid the heavier desktops (Unity, Gnome Shell, KDE)

---

### Post by random turnip on 2017-04-16
Ok thanks guys, looks like I'll try and install of Xubuntu or something then and see what happens.

---

