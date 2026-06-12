---
title: "Unable to play Facebook games ubuntu 12.04 LTS"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by Hankbonk on 2014-02-10
I am finally running Ubuntu 12.04 LTS .  But when I start up a Facebook game, The game starts up, but the game screen itself is squeezed horizontally into a rectangle, with green and purple colors .  According to me it's the flash player making a serious error, but there's no error message mentioned . 

I allready did a complete re-install of Ubuntu 12.04 LTS, hoping this would be solved, but it's the same .  Can anybody please help me with this ?

---

### Post by monkeybrain20122 on 2014-02-10
Well I don't play FB games but I heard they need up to date flash. If that is the case FF probably wouldn't work as Linux flash will be stuck in version 11.2 since adobe has decided to kill it except for security updates til 2017. So, the easy way to get up to date flash would be to install Chrome (adobe has a deal with google which will continue to bundle up to date flash for Linux but only through Chrome)

---

### Post by Hankbonk on 2014-02-11
I really appreciate your answer monkeybrain20122 : Before I re-installed Ubuntu 12.04 LTS, I remember that Chrome was allready installed by my friend .  I will install Chrome now, and I am confident that it will work there !

---

### Post by Hankbonk on 2014-02-11
I have installed Chrome Web Browser, but starting a game has the same result as in FireFox !  Do I have to install the chrome flash plugin, and how do I do that ?

---

### Post by Turnips on 2014-02-11
It should be automatic, I'm surprised it doesnt work.  Are you able to play flash games on other sites, such as this one?: [http://armorgames.com/play/4071/warfare-1944](http://armorgames.com/play/4071/warfare-1944)

---

### Post by Hankbonk on 2014-02-11
Dear Turnips, I tried .../warfare-1944 in FireFox and it makes the same error : The content is squeezed together horizontally in a green and purple rectangle, with no functionality at all !

---

### Post by Hankbonk on 2014-02-11
Both Chrome and FireFox use the same flash player : Adobe Shockwave version : 11.2 r202 .

---

### Post by monkeybrain20122 on 2014-02-11
Well for Chrome you may need to disable flash 11.2. Go to about://plugins on the url bar, then click "details" and scroll down to Adobe Flash. You will find two entries. One is 11.2 and the other is pepper flash 12 (?), disable flash 11.2.

---

### Post by Hankbonk on 2014-02-11
monkeybrain, there is nothing like "pepper flash" on the plugins display !

---

### Post by monkeybrain20122 on 2014-02-11
Hi, you have to click "Details" on the right end of the top row on the plugin page to expand it first. Then you will see something like the screenshot (I have 3 entries as I have installed pipelight's flash as well, but you should see two) Then disable flash 11.2 and enable flash 12.0r0 (location /opt/google/chrome/Pepperflash/libpepflashplayer.so)

---

### Post by Hankbonk on 2014-02-12
Monkeybrain, my details screen only displays the Shockwave flash 11.2, there is no extra with pepper flash 12.0 mentioned .  I do not know how to make a screenshot and embed it here, sorry .  What should I do ?  I will start searching for that pepper flash in the Software Center, awaiting your answer ...

---

### Post by Hankbonk on 2014-02-12
Pepper flash is not in the Ubuntu Software Center !

---

### Post by newb85 on 2014-02-12
You're not using a non-PAE kernel, are you?

---

### Post by mörgæs on 2014-02-12
PAE is irrelevant here.

Hankbonk, as I mentioned in another thread of yours it saves a lot of trouble if you always begin with a hardware description. Please run

```
sudo lshw -sanitize > lshw.txt 
```

and post lshw.txt in CODE tags.

---

### Post by monkeybrain20122 on 2014-02-12
> **Hankbonk said:**
> Monkeybrain, my details screen only displays the Shockwave flash 11.2, there is no extra with pepper flash 12.0 mentioned .  I do not know how to make a screenshot and embed it here, sorry .  What should I do ?  I will start searching for that pepper flash in the Software Center, awaiting your answer ...

Are you sure you have Chrome instead of Chromium? How did you install it?

---

### Post by Hankbonk on 2014-02-12
Dear Mörgaes,  here is the output you requested :

```
computer
    description: Desktop Computer
    product: OptiPlex GX270
    vendor: Winbond Electronics
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=enabled boot=hardware-failure-fw chassis=desktop cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0XF826
       vendor: Winbond Electronics
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A06
          date: 09/29/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.26GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: Microprocessor
          size: 2266MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_2
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 2
             slot: DIMM_3
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 3
             slot: DIMM_4
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=[REMOVED] latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST340016A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.75
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000088b5
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
                configuration: created=2014-02-11 01:57:07 filesystem=ext4 lastmountpoint=/ modified=2014-02-11 02:17:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-02-12 20:08:56 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1020MiB
                capacity: 1020MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1020MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM SD-616
             vendor: SAMSUNG
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: F000
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
```

---

### Post by Hankbonk on 2014-02-12
Dear monkeybrain, You are right : It's Chromium that I installed !!!  How do I get rid of it, and how shood I proceed?

---

### Post by Hankbonk on 2014-02-12
Dear monkeybrain, getting rid of Chromium will not be a problem, but in the Ubuntu Software Center, I can't find the Chrome web browser !  I think I will have to do it by linux commands in a terminal, but I don't know which commands .  Can you help me with that ?

---

### Post by Hankbonk on 2014-02-12
Dear monkeybrain, I succeeded in removing Chromium AND installing Chrome .  Then I disabled the shockwave 11.2 and NOW the other Flash player works correct !!!  I am greatly in your debt, and I will mark this thread as closed !

MILLE GRACI
Hankbonk

---

### Post by mörgæs on 2014-02-12
Good. As a side note: Lubuntu 13.10 would be a better option for the Optiplex 270 than Ubuntu. If you install this one you will need an xorg.conf for the Intel 8xx graphics:
[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html)

Though the problem is solved I'm leaving the link here as it might be beneficial to others who find the thread.

---

