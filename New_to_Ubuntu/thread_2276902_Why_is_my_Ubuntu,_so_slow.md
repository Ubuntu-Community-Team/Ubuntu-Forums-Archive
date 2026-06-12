---
title: "Why is my Ubuntu, so slow?"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by Trandre on 2015-05-05
I have an Ubuntu 15.04, that is extreamly slow. I am waiting several secounds before the next click is responding and I can see the Unity slowly beeing uncovered for 10 seconds from each typings. 

What should I troubleshoot, to start to look for what is causing this slow behaviour?

```
  
fam-fem-ubuntu-server     
    description: Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 smp-1.4 smp
    configuration: cpus=1
  *-core
       description: Motherboard
       physical id: 0
     *-cpu
          product: AMD Athlon(tm) XP 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 0
          bus info: cpu@0
          version: 6.10.0
          size: 2150MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow vmmcall
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory
          description: System memory
          physical id: 1
          size: 1019MiB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:a000(size=4096) memory:e4000000-e5ffffff memory:d0000000-dfffffff
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:d0000000-d7ffffff ioport:a000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d8000000-dfffffff memory:e5010000-e501ffff
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:e6000000-e600ffff ioport:b000(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=32
             resources: irq:19 memory:e6010000-e60107ff ioport:b400(size=128)
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:20 ioport:b800(size=8) ioport:bc00(size=4) ioport:c000(size=8) ioport:c400(size=4) ioport:c800(size=16) ioport:cc00(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d000(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mass storage device
                   product: USB Reader
                   physical id: 1
                   bus info: usb@4:1
                   logical name: scsi0
                   version: 1.00
                   serial: 9206051
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12Mbit/s
                 *-disk:0
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:1
                      description: SCSI Disk
                      physical id: 0.0.1
                      bus info: scsi@0:0.0.1
                      logical name: /dev/sdb
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:2
                      description: SCSI Disk
                      physical id: 0.0.2
                      bus info: scsi@0:0.0.2
                      logical name: /dev/sdc
                      configuration: logicalsectorsize=512 sectorsize=512
                 *-disk:3
                      description: SCSI Disk
                      physical id: 0.0.3
                      bus info: scsi@0:0.0.3
                      logical name: /dev/sdd
                      configuration: logicalsectorsize=512 sectorsize=512
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:e000(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-15-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Primax Electronics, Ltd
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Keyboard
                   product: Microsoft
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@5:2
                   version: 6.34
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:e6011000-e60110ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-15-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Generic USB device
                   product: 802.11 n WLAN
                   vendor: Ralink
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:e400(size=256)
        *-communication:1 UNCLAIMED
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:e800(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:0e:a6:30:7b:23
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:ec00(size=256) memory:e6012000-e60120ff
     *-scsi:0
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160021A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sde
             version: 3.06
             serial: 5JS0EYLH
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=13d1d27a
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sde1
                logical name: /boot
                version: 1.0
                serial: d60988b5-e97d-498b-961f-cb42e9a12c02
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2015-05-05 21:54:05 mount.fstype=ext2 mount.options=rw,relatime mounted=2015-05-05 21:39:39 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sde2
                size: 148GiB
                capacity: 148GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sde5
                   serial: 0Mdxd9-STBc-yv1V-0tpl-Vvxt-lRTc-ICiyQe
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom:0
             description: DVD reader
             product: DVD+RW MP5240A
             vendor: RICOH
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             logical name: /media/tor-andre/Ubuntu server
             version: 1.11
             serial: E
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/tor-andre/Ubuntu server
                configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted
        *-cdrom:1
             description: DVD reader
             physical id: 0.1.0
             bus info: scsi@4:0.1.0
             logical name: /dev/sr1
             capabilities: audio dvd
             configuration: status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 34:21:09:09:20:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.19.0-15-generic firmware=0.29 ip=10.0.0.79 link=yes multicast=yes wireless=IEEE 802.11bgn


```

---

### Post by RobGoss on 2015-05-05
It might be a good idea to run a lighter version of Ubuntu. How much ram does your machine have? from the specs you posted it looks like you have 1-GB am I correct?

---

### Post by TheFu on 2015-05-05
Old CPU, limited RAM, old GPU.
For this situation, you need a lighter desktop LXDE, XFCE, something like that.  Probably best to start with Xubuntu and see if that works acceptably for your needs. Avoid desktops like Unity, gnome3, kde that require 3D-Accel GPUs.

---

### Post by Vladlenin5000 on 2015-05-05
> **TheFu said:**
> Old CPU, limited RAM, old GPU.
For this situation, you need a lighter desktop LXDE, XFCE, something like that.  Probably best to start with Xubuntu and see if that works acceptably for your needs. Avoid desktops like Unity, gnome3, kde that require 3D-Accel GPUs.

^^^^
This.
And adding to the list is a bad VIA chipset. I remember running a machine with similar configuration including the chipset and it strugled even with Windows XP, at times freezing out of the blue (often, with the original motherboard drivers, and less often with the updated ones from VIA)*.
The graphics card/chip is, in terms of support from AMD (current owner of ATI), a legacy product for which no proprietary drivers are available (compatible with newer Linux kernels). As such whathever you're getting with the default Radeon driver (community, open source) is what you'll ever get, hence the strong recommendation for variants with lighter desktops as Unity requires a fairly recent and powerful graphics card/integrated chip, served with a good drivers with 3D support and a side of lots of RAM




* I know it was  a crappy chipset/motherboard because the same CPU, RAM and HDD were later used with a different motherboard (nForce chipset, if I'm not mistaken) and everything worked fine, some 3-4 yeras more.

---

### Post by Trandre on 2015-05-05
Thanks guys, I have only used Ubuntu before, but watched some reviews on the Xubuntu, and liked it. 
I see that you can convert to xubuntu by using the sudo apt-get install xubuntu-desktop.

Q1:Do I understand it correct, when I think it is only the desktop environment you change and everything else is the same?
Q2: I would really like to use the machine as a server aswell, can I change to Xubuntu and still keep the server features such as open ssh etc?
Q3: Is there any low hanging fruits in hardware upgrade I can do such as buying more RAM, that I could do to make it perform better?

---

### Post by TheFu on 2015-05-05
> **Trandre said:**
> 
Q3: Is there any low hanging fruits in hardware upgrade I can do such as buying more RAM, that I could do to make it perform better?

At this stage, you should swap the MB, CPU, and use an onboard GPU.  I saw a deal for a G3258 Intel and MB for $88 recently. Spend $20 on DDS3 RAM and the new system will be 50x faster than what you have even with the onboard GPU.  You can go a little cheaper using an AMD equiv, but the performance will only be 40x more. It has been about 2 months since I looked at all the options for this price range.  I spent $126 on that Intel CPU/MB combo in Feb. It is an amazing CPU for the price.

Both will use about 35W normally, 20W if there isn't much work being done. That is probably 100W less than your current system. 65W if **really** busy.

I'm guessing on the performance - sorta trying to make a point.  Oh - sata drives can be reused. IDE cannot. PSU can probably be reused, but it is probably old enough to be less than solid. PSUs do wear out.

Q2 - server processes can be run on any Linux.  Openssh can always be run.
Q1 - usually that is fine, but sometimes there are incompatible settings. Best to create a new userid for each new desktop. Desktop settings are stored under each HOME directory by userid. There might not be any issues, but it is best to be safe.

---

### Post by mörgæs on 2015-05-06
I suggest that you try L/Xubuntu for a couple of weeks before deciding upon hardware. If performance is still low I recommend swapping the graphics card, if you find something which fits to the slot.

---

### Post by mastablasta on 2015-05-06
> **Trandre said:**
> 
Q1:Do I understand it correct, when I think it is only the desktop environment you change and everything else is the same?


yes.

> 
Q2: I would really like to use the machine as a server aswell, can I change to Xubuntu and still keep the server features such as open ssh etc?

yes. you do not need a desktop on server... I mean usually server machines have no monitor.

> 
Q3: Is there any low hanging fruits in hardware upgrade I can do such as buying more RAM, that I could do to make it perform better?

your first major problem: 
```
description: VGA compatible controller  product: RV280 [Radeon 9200 SE]
```
solution new GPU. problem is this is (if it is even a card) and AGP card. they do not make many of those. though they do exists out there. you could find a used one. you need something with as much RAM as possible. option 2 is PCI card. not many of those. and option 3 is probably out since you likely do not have the PCIe slot. even if oyu do only few NVidias will work with old PCIe slots. forget about latest AMD cards.

problem 2 is ram - more is better - having at least 2 GB available is good. 4 GB is preferred.

finally the CPU - it's not that fast, but for browsing some light old games it is good enough providing you have enough ram, and good GPU.

best solution but also most expencive one is as TheFu suggested - replace motherboard. power supply and CPU with new ones. instead of classic CPU get an APU (=AMD CPU with GPU chip - they are cheap and perform well).

if you are low on money, then try to get older AGP GPU (radeon 9600 & above have good support, as well as 3650 series (yes, they still made those with AGP). some old nvidias have propiretary drivers support. but I dont' know which ones. Make sure the power supply is good enough. then upgrade RAM to 4GB (or at least to 2GB).

the slowness you experience is actually from the GPU chip. it is not well supported, so the CPU which is already weak is used to draw the desktop and all special effects (instead of the GPU)- and since ram is also low adding a few apps into memory will force the OS to use the hard disk which will all slow it down a lot. but of course this kind of slow down will only happen when RAM is full while as I understand you already experience slow desktop on boot.

---

### Post by alex375 on 2015-05-06
maybe you need agp nvidia card. All other cant cause it
maybe 3 things - Broken hardware
inproper installation
incompatibility

---

### Post by TheFu on 2015-05-06
mastablasta - nice coverage.

Passmarks ... 
Athlon(tm) XP 3000+ = 399
Pentium G3258 (not overclocked) = 4010

About 10x faster overall. The G3258 can be overclocked 25% (I don't, but others do) with the stock CPU cooler included in the box to over 4Ghz with little risk of instability. This CPU is extremely popular due to the price/performance - basically we get the performance of a Core i5 (1st gen) for the price and power use of a Celeron. The next step up is a new Core i3 for $200/cpu. 

For video transcoding the performance increase is amazing. The onboard Intel GPU is far beyond what most non-gamers need and will work great for 80% of games.

It all comes down to budget. Don't forget that you can probably just connect the old HDD to any new system and it will probably be fine with the Linux boot. No reinstall needed.

---

### Post by Trandre on 2015-05-06
Thank you guys for all the good advice, and detailed answers. I have a lot to continue further on now :idea:

---

### Post by mörgæs on 2015-05-06
You're welcome.
Please post back when you have done some experimenting. There might be some ideas in the link in my signature.

---

### Post by mattharris4 on 2015-05-07
I certainly would not run Ubuntu with only 1Gb of RAM.  I cannot even run Lubuntu fully within that limit.  I know others have suggested replacing the CPU, GPU and even the whole motherboard here but if the computer is as old as I suspect it is (at least six years old) IMO it isn't worth putting that much money into this computer.  However, RAM is cheap.  I would install another GB into this computer and then try Lubuntu with it.  

If increasing RAM and using Lubuntu doesn't make the computer run reasonably well (being a US resident) I would buy a refurb desktop from Tiger Direct or Newegg with 8GB of RAM, the processor that would come with that level refurb would likely run circles around what you have although the features list will name the processor it has in it, you can do a Google search for it and several websites will come up with ratings info and they tend to use the same benchmark programs, compare with the 399 your current processor rates.  Even my laptop with the woefully underpowered AMD E1-2100 1.0 GHz CPU that rates 617 (this processor is meant for low-power laptops or tablets to save power -- it is a 9W processor compared to most computers' 30-65W) rates much higher than your CPU does.  In comparison most computer CPUs meant for desktops sold today rate over 2000.  Avoid Intel Atom and Celeron CPUs as well as AMD E1 CPUs.  There is one older low-line AMD CPU that is also slow but I do not recall what that is, do the Google search and you will know quite quickly if you want that CPU in your computer or not, most rate 2000+ overall, you want at least 1250 overall rating if possible.  These are all Passmarks ratings.  Here is one site you can search for ratings with: [http://www.cpubenchmark.net/index.php](http://www.cpubenchmark.net/index.php) .

The only main issues besides having the $200 to spend is whether will Tiger Direct or Newegg ship to Norway -- both are based in the US, the shipping cost and the customs duties you might encounter (although $200 doesn't usually attract much in duty charges in most countries, for the US we are allowed to ship in $200 a day in most imports and not pay any customs duty).  If importing a refurb is a big issue is there any refurb sellers in Norway that are trustworthy and sell refurbished computers at the same reasonable prices they sell for here?  Nothing is coming up in a Google search of the English language site and I don't speak Norweigan to check that Google site.  The Microsoft site comes up with one company (Arrow Value Recovery) which does not sell direct to consumers.  That site comes up with Greentech PC but most of their site is in Norweigan so I cannot make heads or tails of some of it.  What is in English tells me the computers are refurbished and come with Win 7 (you would dual-boot install with your preferred Canonical OS, these do not likely have a UEFI so the install should go smoothly).  From what I can make heads and tails of they have a desktop for 1,495 krone which is $200.22 US.  This computer is not as fully featured as the US refurbs for the same price (only 4GB RAM and 160GB HDD instead of 8GB RAM and 1TB HDD in the US equivalent) but it likely would run any Canonical OS fine (I cannot tell what CPU it has but anything is much better than what you have).  Look carefully and check the CPU's rating as specified in the first paragraph before buying.

---

### Post by mastablasta on 2015-05-08
> **mattharris4 said:**
> 
If increasing RAM and using Lubuntu doesn't make the computer run reasonably well (being a US resident) I would buy a refurb desktop from Tiger Direct or Newegg with 8GB of RAM, the processor that would come with that level refurb would likely run circles around what you have although the features list will name the processor it has in it, you can do a Google search for it and several websites will come up with ratings info and they tend to use the same benchmark programs, compare with the 399 your current processor rates.  Even my laptop with the woefully underpowered AMD E1-2100 1.0 GHz CPU that rates 617 (this processor is meant for low-power laptops or tablets to save power -- it is a 9W processor compared to most computers' 30-65W) rates much higher than your CPU does.  In comparison most computer CPUs meant for desktops sold today rate over 2000.  Avoid Intel Atom and Celeron CPUs as well as AMD E1 CPUs.  There is one older low-line AMD CPU that is also slow but I do not recall what that is, do the Google search and you will know quite quickly if you want that CPU in your computer or not, most rate 2000+ overall, you want at least 1250 overall rating if possible.  These are all Passmarks ratings.  Here is one site you can search for ratings with: [http://www.cpubenchmark.net/index.php](http://www.cpubenchmark.net/index.php) .
.

depends for what you need the CPU for.

I have a similar CPU as OP - Athlon 64 XP 3200+ - it's average passmark on site you posted is 495. it has windows XP on (it will likely get Kubuntu in the future). it can run most games up to 2012. depends what you are after. but when it says dual core is needed this one performs just fine. I played all Stalkers, the old UT2004, Boiling point, Oblivion, Europa universalis 3, Iron cross, Need for speed underground 2, Doom 3, Supertux cart, Minecraft, Minetest...... basically most games up to about 2010 have no problem running on it. I played many of them on this PC. it also works well for office work, web browsing, web page management etc. secret? it has 4GB ram (but was actually working well even with 2 GB) and AMD radeon HD 3650 512 MB. it takes time to boot into windows and load all antivirus and firewall applications, but once it's loaded it works well. 

I also have AMD E-450 (average passmark 783) - it runs windows 7 starter (has 2GB ram). takes a bit of time to boot but once it boots it again works well for the taks. I use it mostly for browsing and editing webpages. but it can also play some older games, like UT 2004, Enemy territory...

Now I have Core i3-4130 3,40 ghz at work. this one has score 4801. so the performance on it should blow me away. only it doesn't as I do only office things (MS office, SAP, Emails) and web browsing (various work related web apps) I don't really notice the difference.  it's fluent doesn't bother me... but nothing noticeable. probably because i do not have some intensive CPU tasks. if I did some calculations on it or play games I would notice performance increase, but for this normal use it is good enough. 

so these passmark scores don't help much. I always check what I can run with it to know approximately how powerfull it is and also to see if I can do things I want to do on it without getting annoyed at slowdowns.


--

to the OP I have setup with Athlon 3200+ and ATI 9200 128 MB (not the SE one). The ATI 9200 is descent chip, but it has bad support in Linux. the chip and setup can run old Half life games and mods and Morrowind fine (I would say certain games up to about 2004) in windows XP but will be able to run only some basic things in Linux. it' s because it doesn't have full 3D acceleration. hence if you can upgrade it (replace it) and increase the ram while at it, it will be a fine setup even for some light gaming.

---

### Post by mattharris4 on 2015-05-08
Mastablasta, my issue with low-powered computers (at least my laptop which is about a year old) is usually when I try to run two or three different programs on Lubuntu (say Firefox, Rhythmbox and Libre Office) where the processor bogs down and pages start freezing up.  This is even more prominent when running Win 8.1 running two or three programs (an example would be Firefox, Windows Media Player and an AVG Anti-Virus scan/update) where WMP will freeze up every time in this scenario.  I have plenty of RAM (4GB), in Win 8.1 I usually have about 1500MB left over in this scenario, in Lubuntu I have about 2200-2500MB available).  I don't usually have these issues with my Pentium 4 desktop even though it is about eight years old (Passmark scores for that era Pentiums are well over 1000).  

With the cost of computers having dropped considerably in the past year and knowing what I know now I would probably purchase an i3 equipped computer with at least 4GB RAM if I were buying a laptop today.  Since I would want to run Linux on it I would not purchase a new HP computer, yes you can alter the kernel manually to run on them (Oldfred has instructions on this posted to the forum) but why go through that when I can buy a Dell or Lenovo and not have to monkey with the kernel and possibly need Linus himself to bail me out of any mistakes in transcribing to make it work (unfortunately Oldfred's instructions don't say how to correct any mistakes).  You can buy a new i3 equipped Dell for less than $500 or a Core 2 equipped refurb laptop from Tiger Direct for about $200, both should run circles around the low-powered CPU computers (although the i3 would be light years faster than any Core 2 equipped computer).

---

