---
title: "What 32-bit OS is best for streaming youtube?"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by fall2 on 2014-12-26
This is a question I should of asked from the start but here it is. Basically I'm running a computer that is just a little slower than recomended for streaming, so I'm dropping some frames. I downloaded Lubuntu 14.04 32-bit and running it now. I have 1g ram so I could run any Linux OS. Really all I care about is streaming youtube videos and other flash content. Are one of these a little better Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu and UbuntuGnome or maybe another Linux baised OS has a slight advantage?

 After using Lubuntu I'm starting to think I should have gone with Ubuntu or another linux. I know some OS do work better than others for streaming. If you tryed out multiple linux OS did one work better for you than another?

OS, Web browsers and Flash players all effect streaming video, I'm trying to figure out the best combo starting with my OS but any help from experienced people with slightly sub-par computers would be awesome.

---

### Post by mörgæs on 2014-12-26
A lot of people ask a similar question but focus should be on the applications, not the operative system.

While keeping Lubuntu I think the best you can do is experimenting with different browsers. Not only Chrome and Firefox but also Xxxterm, Opera and other light ones.

---

### Post by kerry_s on 2014-12-26
yeah, you just need a lighter browser. i recommend epiphany-browser or midori. epiphany seemed to play flash better for me.

just a thought  skip the browser all together & just grab the minitube app for youtube, it should be in the repo.
i'm on ubuntu mate 14.10 & it shows up in "apt-cache search minitube"

---

### Post by Impavidus on 2014-12-26
Use a light system and pick the right application. You may have to experiment a bit to find the right browser.
> **fall2 said:**
> ... youtube videos and other flash content. ...
I rarely have to enable the flash player to watch youtube.

---

### Post by Holger_Gehrke on 2014-12-26
Flash on Linux is generally not good because adobe has discontinued work  on Flash for Linux since Version 11. We only get security fixes but no  new features. Googles Chrome is supposedly somewhat better because it  has it's own (non-adobe) plugin for flash. 

Generally I avoid  Flash wherever possible. One way to do this is to use a  UserAgentSwitcher in the Browser to make the Server 'believe' that  you're using an iPhone. That often makes streaming sites send html5  Video instead of Flash.

---

### Post by fall2 on 2014-12-26
> **Holger_Gehrke said:**
> Flash on Linux is generally not good because adobe has discontinued work  on Flash for Linux since Version 11.

This is why I want to learn about other Ubuntu OS. Firefox has Adobe flash 16 the newest version and updates its add-ons by its self. It would be nice to know from some one who tryed other OS, so I could maybe keep FF and have it perform a little bit smoother. I myself would think Ubuntu 14.04 would work better than lubuntu 14.04 for streaming because there are more performance options and its not a clone OS. I might as well just try them all, just wan't to see if I can get some input so I didn't have to.

---

### Post by fall2 on 2014-12-26
> **fall2 said:**
> This is why I want to learn about other Ubuntu OS. Firefox has Adobe flash 16

nope never mind I have 11.2, strike that.

---

### Post by grahammechanical on 2014-12-26
I do not use Lubuntu but it is not correct to call it a "clone" OS. Lubuntu is Ubuntu with a different desktop environment and user interface. Have you considered that the problem may lay with your graphic adapter? Lubuntu will give a good user experience on hardware that is not up to running Ubuntu. If you want as much of your computer resources as possible to deal with video rendering, then an OS that requires less video rendering itself is what you should use.

A computer OS cannot make up for the deficiencies of our hardware.

---

### Post by Yellow Pasque on 2014-12-26
>  I myself would think Ubuntu 14.04 would work better than lubuntu 14.04 for streaming because there are more performance options
I'm not sure what performance options you're talking about. Be more specific.
If streaming is all you care about, then I don't see the logic in using a heavier desktop (like Unity, KDE, Gnome, etc.). Most likely, it wouldn't make a significant difference, but it may waste some CPU/GPU cycles, so your logic seems backwards to me.

What are the hardware specs here?

---

### Post by fall2 on 2014-12-26
> **grahammechanical said:**
>  Lubuntu is Ubuntu with a different desktop environment and user interface. 

Well yeah it has a lighter desktop that uses less ram. For me its all about the total amout of CPU usage the OS takes when running a browser while its playing a flash video. The visual looks have a little impact but its more about the demand on the CPU. How much CPU does it take to run a browser and a flash video. How much CPU does the OS use to start those programs and keep them running. These are stats you just can't find easy.

---

### Post by deadflowr on 2014-12-27
> **Holger_Gehrke said:**
> Flash on Linux is generally not good because adobe has discontinued work  on Flash for Linux since Version 11. We only get security fixes but no  new features. Googles Chrome is supposedly somewhat better because it  has it's own (non-adobe) plugin for flash. 


Flash on Google Chrome is still Adobe Flash, only it's special built to run in/with Chrome's Pepper Plugin API.
But it is still an Adobe product.

---

### Post by fall2 on 2014-12-27
> **mörgæs said:**
> A lot of people ask a similar question but focus should be on the applications, not the operative system.

While keeping Lubuntu I think the best you can do is experimenting with different browsers. Not only Chrome and Firefox but also Xxxterm, Opera and other light ones.

I Downloaded Opera from their web site, It took a while to set it up (visuals, add-ons and preferences). After I did I found out Opera cut 50% of my frames lost over the Firefox browser I was using.

I can't get cromes add-ons to work and I didn't look like Xxxterm had any add-on options.

The only downside to Opera was there is not an add-on to load lighter mobile versions of websites like Firefox has.

I should also note I turned Firefox's hardware acceleration off and that dropped maybe 5% of frames lost.

---

### Post by mörgæs on 2014-12-27
Maybe we should take a look at the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by fall2 on 2014-12-27
> **mörgæs said:**
> Maybe we should take a look at the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Here you go morgaes anything you can do would be great.




 ```

computer
    description: Notebook
    product: Gateway 400VTX
    vendor: Gateway
    version: Rev 1
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Gateway 400VTX
       vendor: Gateway
       physical id: 0
       version: Rev 1.0
     *-firmware
          description: BIOS
          vendor: Gateway
          physical id: 0
          version: 38.00.35
          date: 03/12/2003
          size: 108KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Celeron(R) CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: uFCPGA2
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SRAM Synchronous 200 MHz (5.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 200 MHz (5.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:10 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:40000000-43ffffff
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:11 memory:48000000-48000fff ioport:3400(size=256) ioport:3800(size=256) memory:40000000-43ffffff memory:4c000000-4fffffff
           *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
                resources: irq:11 memory:e0200000-e0200fff
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 83
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=[REMOVED] latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:11 memory:e0201000-e0201fff ioport:3000(size=64)
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:10 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:44000000-440003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1600(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:10 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHV2040A
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0000
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000c4b5b
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 36GiB
                capacity: 36GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-26 18:33:30 filesystem=ext4 lastmountpoint=/ modified=2014-12-27 09:59:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-27 09:59:51 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1013MiB
                capacity: 1013MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1013MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw dvd
             configuration: status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: CardReader CF RW
             vendor: USB2.0
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0.0>
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: CardReader Combo
             vendor: USB2.0
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 0.0>
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                 logical name: /dev/sdc
```

---

### Post by mörgæs on 2014-12-27
Sorry, this is weak hardware and one must accept a low performance. Celeron processor, small L2 cache, 1 GB of memory but it's the slow kind... 

For the Intel 8xx graphics it might help to add an xorg.conf. See the link in my signature for details.

---

### Post by fall2 on 2014-12-27
> **mörgæs said:**
> Sorry, this is weak hardware and one must accept a low performance. Celeron processor, small L2 cache, 1 GB of memory but it's the slow kind... 

For the Intel 8xx graphics it might help to add an xorg.conf. See the link in my signature for details.

I think your on to something, I do have blacked out lines in my FF browser in the HTTP bar. I will try this and see what happens.

---

### Post by fall2 on 2014-12-27
Ok I went to location /etc/X11/ and tried to make a file and I was denied permission. how do I get permission? and all I have to do for the record is put this into the xorg.conf file and save right?
```

 Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection
```

---

### Post by mörgæs on 2014-12-28
The guide is updated now regarding this.

---

### Post by fall2 on 2014-12-28
There we go, Now Opera in Lubuntu is playing videos equal to Firefox in my old Windows XP OS.
 I should note I tried to use the "save as" and the file disappeared on reboot, I had to use "save" the second time and it worked.

---

### Post by fall2 on 2014-12-28
Is there any way to turn the sound accelerations to basic accelerations only or medium accelerations(Medium would be better). My sound works fine but I know if I do something like this it would reduce the strain on the CPU while watching videos. 

Another thing that helped in XP was a program that let me permanently set priority to the adobe flash process up +1.

If you know the way to make these changes, that would just be awesome. If not thanks for the help.

Answer:
 			 				[INDENT] 					 	Code:
 	gksu leafpad /etc/pulse/daemon.conf

The setting you may want to look at changing is 
resample-method to resample-method=trivial for lowest CPU 
usage.

 

After you make changes, you can save the file,  exit leafpad and restart pulseaudio:
 	Code:
 	pulseaudio -k 
 				[/INDENT] 			
  			   		
This change helped improve flash video a little with lost frames or choppy videos.

---

### Post by mörgæs on 2014-12-28
I can't help much with sound. My guess is that the workload for managing sound is minimal compared to video but I'm not expert. 

If you want a better answer I suggest the Multimedia forum.

---

### Post by kerry_s on 2014-12-28
i got a lite 1 for ya to put on your to try list. "elementary os" its ubuntu 12 lts based, has just the very basic apps installed. i been playing with it since yesterday & i must say this may be a keeper. the midori browser plays flash great(i have chrome installed as backup browser), just a tip, use the terminal to install the restricted stuff: sudo apt-get install ubuntu-restricted-extras
the software center locked up on me, cause you have to accept the agreement, which it didn't show to me.
only warning though is the ui is pretty locked down, i guess they don't want people screwing up there hard work, but it's a dead simple setup.
[http://elementaryos.org/](http://elementaryos.org/)

---

### Post by monkeybrain20122 on 2014-12-29
The best way is not to use flash at all on Youtube. Install gecko-mediaplayer from repo, greasemonkey addon for Firefox and then install Viewtube on Firefox with greasemonkey
[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

You can also install standalone Youtube viewers such as Smtube and minitube

For smtube, add this ppa

[https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)

For minitube, download .deb from

[http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)

---

