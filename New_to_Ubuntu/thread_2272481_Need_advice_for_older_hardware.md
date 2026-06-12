---
title: "Need advice for older hardware"
date: 2015-04-07
forum: New to Ubuntu
---

### Post by joe163 on 2015-04-07
Hello,

Really enjoying Ubuntu after this last re-install.  I'm using Ubuntu 14.04.  The problem I am having is when using Firefox or Google Chrome browsers.  At first, it wasn't so bad.  I'd open up a number of tabs and use the computer practically all day, but then at some point, I'd open up another tab, or refresh one that I already had open and then bam, the browser freezes, my whole computer freezes, and I have to do a hard reboot.

Well, now this problem is happening every hour or two with only a few tabs open.  Is there some setting that I can set in Google Chrome so that a few seconds after a web page becomes unresponsive, chrome will just die instead of freezing up my whole computer?  Or should I look at using other lower resource windows managers other than Unity?

I welcome any advice.

My output to lspci is attached.

Thanks.

---

### Post by kerry_s on 2015-04-07
are you using unity or are you using lubuntu ?

lubuntu is already light. if your using unity then yes you should try something else, compiz has been very buggy with intel graphics of late. i had good luck with unity in ubuntu 15, but it still felt slow. i'm currently using ubuntu-gnome cause i like to use dual screens & it seems to handle it best.

just work your way down the ubuntu's till you find the ui you like.

---

### Post by joe163 on 2015-04-07
Can I just install LXDE on my current OS install?  And will I have any problems using OpenVPN or with my current drivers for my wireless adapter which work out-of-the-box on standard Ubuntu 1404?

---

### Post by joe163 on 2015-04-07
I'm using Ubuntu with Unity, I don't know how on earth this post got tagged as lubuntu and I can't seem to change that with 'edit'.

(edit: on second thought, maybe it is a good idea that it was changed by someone to have the 'lubuntu' tag since my last question would be best answered by lubuntu gurus.  Thanks!)

---

### Post by mastablasta on 2015-04-07
yes, install lxde. not sure the exatct package. you can also try first with windows manager to see if that is really an issue (for example icewm for that 90's look).

it could also be RAM related or heat related. for heat install psensor. a good GUI utility. for memory run mem test. it could be that part of ram is damaged. otherwise hard to say. it could really be just drivers. had an ancient laptop with really low ram. windows XP worked on it slow, but it worked when it loaded. however at some point is started to crash. no good reason given. installed debian on it. though I will try before throwing it away. and suddenly it works with no isues whatsoever.

---

### Post by mörgæs on 2015-04-07
The 'specs' file in original post does not reveal much. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by joe163 on 2015-04-07
Ok, have added the attachment as requested.  Thanks.  Last I checked, all hardware is working fine, for 2009 technologies lol.  No problem with overheating as far as I can tell, everything is clean and I always work with the case open.

(edit: Sorry, you wanted that in code tags?  How do you mean?  Should I post the whole output here rather than using the attachment for ya?)

---

### Post by mörgæs on 2015-04-07
Yes, please edit the post, remove the attachment and post the contents in CODE tags.

---

### Post by joe163 on 2015-04-07
Ok, in edit post, I didn't see any option to wrap in code nor how to remove the attachment.  Anyhoo, here is the output:

```
computer
    description: Desktop Computer
    product: G41M-ES2L ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: G41M-ES2L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F4
          date: 07/22/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: [REMOVED]
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
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
             resources: irq:43 memory:e1000000-e13fffff memory:d0000000-dfffffff ioport:e000(size=8)
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:e1600000-e1603fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:7dd00000-7defffff ioport:80000000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:e0000000-e0ffffff ioport:e1400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:d000(size=256) memory:e1410000-e1410fff memory:e1400000-e140ffff memory:e1420000-e142ffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e100(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e200(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e300(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e400(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e1604000-e16043ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:e1500000-e15fffff
           *-pci
                description: PCI bridge
                product: PI7C8140A PCI-to-PCI Bridge
                vendor: Pericom Semiconductor
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pci pm hotswap normal_decode bus_master cap_list
                resources: memory:e1500000-e15fffff
              *-multimedia:0
                   description: Multimedia controller
                   product: SAA7134/SAA7135HL Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: c
                   bus info: pci@0000:04:0c.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15
                   resources: irq:20 memory:e1500000-e15003ff
              *-multimedia:1
                   description: Multimedia controller
                   product: SAA7134/SAA7135HL Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: d
                   bus info: pci@0000:04:0d.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15
                   resources: irq:19 memory:e1501000-e15013ff
              *-multimedia:2
                   description: Multimedia controller
                   product: SAA7134/SAA7135HL Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: e
                   bus info: pci@0000:04:0e.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15
                   resources: irq:18 memory:e1502000-e15023ff
              *-multimedia:3
                   description: Multimedia controller
                   product: SAA7134/SAA7135HL Video Broadcast Decoder
                   vendor: Philips Semiconductors
                   physical id: f
                   bus info: pci@0000:04:0f.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15
                   resources: irq:16 memory:e1503000-e15033ff
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH22NS50
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: TN02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HD502HJ
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 1AJ1
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000bf809
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2015-04-07 10:59:27 mount.fstype=ext2 mount.options=rw,relatime mounted=2015-04-07 10:59:27 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 465GiB
                capacity: 465GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 465GiB
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.13.0-48-generic firmware=1.3 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by mörgæs on 2015-04-07
It's not that old but as mentioned above Lubuntu/lxde would be more suitable than Ubuntu. 

As a first try you could add lxde, and if you still have problems then a fresh install of Lubuntu is the way to go.

---

### Post by RobGoss on 2015-04-07
I have Xubuntu 14.4 LTS on a older dell 2400 and out of all the distributions this one seems to perform the best, sometimes a lighter version will work the best on older machines.

---

### Post by grahammechanical on 2015-04-07
I have an Intel Core 2 Duo @ 2.40GHz with half the RAM that you have an Ubuntu and Unity runs fine on it 

 But I have noticed that nothing eats memory so much as web pages. This web site is very good but then it does not have dozens of flash elements with slide shows and videos. Some newspaper web sites are so crammed with flash advertisements that the page is unusable.

Ubuntu comes with Ubuntu Web Browser. It cannot compete with the usual web browsers but I think it accesses the mobile versions of many web sites as Browser is the browser for the Ubuntu phone. I also suspect that when a tab is not on screen it stops using resources because on Ubuntu phone once an application is off screen it stops using resources.

I have found that sites that crash Shockwave when accessed by Chromium and cause Chromium to freeze do not affect Ubuntu Web Browser. Every tab we have open uses resources. I have System Load Indicator installed and I can see the drop in memory used as I close tabs when using Chromium or Firefox.

Regards.

---

### Post by joe163 on 2015-04-07
Thank you all for the replies.  I have installed lxde and have logged into it now.  Will see how this goes now, if problematic, will do fresh install of lubuntu.  Yeah, browsers are the only reason why I am having problems with Unity.  Open that next tab, and if it is a resource hog, whole system freezes and I have to do a hard reboot.  Will see how things go now on lxde.  Thanks.

---

