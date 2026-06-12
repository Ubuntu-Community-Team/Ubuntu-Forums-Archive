---
title: "New install 12.04 Computer stuck in dual monitor mode but..."
date: 2013-06-10
forum: New to Ubuntu
---

### Post by rdd85 on 2013-06-10
I am an absolute beginner with linux so bear with me. I just installed ubuntu 12.04 on my vaio all in one pc. The screen has a line running across the bottom and a line running down the right side. When I go to display settings it has 2 monitors showing. One says laptop and the other says unknown. I have only ever had 1 monitor hooked up. I think this may be the problem but I don't know how to fix it. please help.

*edit: Maybe I should clarify that I don't want to stay in dual monitor mode and I know this is the problem. I also don't know how to use Ubuntu that well yet so please don't ask for me to pull up some kind of log file and if I need to use a complex command please break it down in easy to understand terms for me. My mind does not seem to let me understand things unless I can put it all together, this is also why I am bad at math I think. Thanks in advace.

---

### Post by rdd85 on 2013-06-11
Please someone at least give me a psuedo comforting response... Please?

---

### Post by cub on 2013-06-11
I don't understand what it looks like, could you do a screenshot? Is it an ATI or nivida graphic card in the laptop? And have you installed their drivers?

---

### Post by rdd85 on 2013-06-11
I really dont know what happened. When I went to bed I had a screen capture that showed 2 monitors and when I woke up it seems like they are gone. Now the problem seems to be that I cant view the full screen. I dont know how to describe it except it looks like I need to stretch the screen to fit. There is a solid gray bar running vertically down the right side of the screen. I cannot move my mouse through it and it is like the screen stops there. It is almost like it is the wrong ratio aspect or whatever. This does not show up in a screen shot though. If I change the resolution it goes back to the old problem which I did poorly describing I guess.

BTW (dont know if this is supposed to be all caps) I dont know what kind of graphics because system info says unknown. It also seems as if the screen might be zoomed in or something

I also just noticed my built in speakers dont work.

---

### Post by cub on 2013-06-11
Ok, could provide the model number for the pc?

---

### Post by robert shearer on 2013-06-11
> **cub said:**
> Ok, could provide the model number for the pc?

open a terminal (Ctrl+Alt+t ) and run...
```
sudo lshw
```

Then paste back the output here inside 'code tags' (Highlight the pasted text and click on the # symbol in the edit icons above)

lshw= list hardware  so we can tailor our suggestions to your hardware. :)

---

### Post by rdd85 on 2013-06-11
The model number is Sony Vaio VGC-JS160J

```

]mary-pc                       description: All In One
    product: VGC-JS160J (N/A)
    vendor: Sony Corporation
    version: C6U06HHV
    serial: 28281031-3002031
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=all-in-one family=N/A sku=N/A uuid=97E40980-72CB-11DD-80DA-001DBA2151D9
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R0200T4
          date: 08/01/2008
          size: 64KiB
          capacity: 4032KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
          serial: N/A
          slot: N/A
          size: 2500MHz
          capacity: 2500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2
             physical id: 0
             slot: SODIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2
             physical id: 1
             slot: SODIMM2
             size: 2GiB
             width: 64 bits
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
             resources: irq:42 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:ec00(size=8)
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
             resources: memory:fe800000-fe8fffff
        *-communication
             description: Communication controller
             product: 4 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:fe9fbc00-fe9fbc0f
        *-network
             description: Ethernet interface
             product: 82567V-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 00
             serial: 00:1d:ba:21:51:d9
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=1.8-5 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:41 memory:fe9c0000-fe9dffff memory:fe9fa000-fe9fafff ioport:e880(size=32)
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e800(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:e480(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fe9fb800-fe9fbbff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fe9f4000-fe9f7fff
        *-pci:0
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:fea00000-feafffff ioport:b7e00000(size=2097152)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:1f:e1:d4:d2:89
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.5.0-32-generic firmware=N/A ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:feaf0000-feafffff
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e400(size=32)
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e080(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e000(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe9fb400-fe9fb7ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:feb00000-febfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:febff800-febfffff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 3.1
                bus info: pci@0000:02:03.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:febff400-febff4ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 3.2
                bus info: pci@0000:02:03.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:17 memory:febff000-febff0ff
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) ioport:d080(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe9fb000-fe9fb0ff ioport:400(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAJS-5
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCASY1875294
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00043147
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: fcebe605-a971-4a2a-b6da-019223f002be
                size: 461GiB
                capacity: 461GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-10 13:37:41 filesystem=ext4 lastmountpoint=/ modified=2013-06-10 13:58:59 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-06-11 03:28:43 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3899MiB
                capacity: 3899MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3899MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: BD ROM BC-5500S
             vendor: Optiarc
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.75
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
mary@mary-pc:~$ 
```

---

### Post by rdd85 on 2013-06-11
I just a new problem. My screen goes black every few mins for just a second. Is all this just driver issues?

---

### Post by rdd85 on 2013-06-12
It has been 24 hours so I am bumping this thread. I tried the suggestion that Howefield gave me. It still does the same thing even on 13.04. I also went to additional drivers and it said I have no new proprietary drivers.

---

### Post by cub on 2013-06-12
No, it wouldn't, it seems to be an Intel graphic card. My bet in a usual case would a loose cable but looking at picture of the model that does not seem possible. There was no issue with the screen using Windows?

---

### Post by rdd85 on 2013-06-12
none at all. I had Vista on it and it actually(surprisingly) worked flawlessly for over 4 years without even 1 reinstall.

I also noticed that in a browser I can't scroll all the way down to the bottom of the page. It is like the bottom eighth of the page is below where my screen can get to.

---

### Post by cub on 2013-06-13
It all sounds very weird, you could not provide a screenshot?

---

### Post by rdd85 on 2013-06-13
I took a screen cap but it looks perfectly normsl. The problem is that the bar I was refering to on the right side of the screen appears to be like where the computer thinks the screen ends. I don't remember if I mentioned this but I get no sound either. I tried to use killall pulseaudio and that command did nothing. I also went to alsamixer and there was nothing muted or anything. I think it is the fact that it is integrated graphics and audio and the drivers are not installed.

---

### Post by cub on 2013-06-13
Could be. If you are a bit adventurous you could download the 13.04 to an usb drive and see how it performs when booting up. No installation, just boot from the usb.

---

### Post by rdd85 on 2013-06-13
I have done this already. I installed 13.04 twice and 12.04 three times on both 32 bit and 64 bit. I went to the sony website but the drivers are for windows only. I cannot revert back to windows because the hard drive has been reformatted including the hidden partition. I am at a complete loss and don't know what to do.

---

### Post by robert shearer on 2013-06-13
Open system settings either from the launcher or top right of the screen and select 'software and updates'.
In the window that opens choose the right hand tab 'Additional Drivers' and see if there are recommended display drivers to install.
Report back.

Edit.. I see you have tried that already...looks like the display is not providing data  for autoconfiguration.
When you boot from the live usb or cd is the display ok..? Presumably it is otherwise you would not have installed to hard drive...?

---

### Post by rdd85 on 2013-06-14
> **robert shearer said:**
> Open system settings either from the launcher or top right of the screen and select 'software and updates'.
In the window that opens choose the right hand tab 'Additional Drivers' and see if there are recommended display drivers to install.
Report back.

Edit.. I see you have tried that already...looks like the display is not providing data  for autoconfiguration.
When you boot from the live usb or cd is the display ok..? Presumably it is otherwise you would not have installed to hard drive...?

Yeah ... about that. I installed first without testing it. I did however notice something was amiss when the first screen that is that wierd shade of purple shows it was just a small box of purple. Once the desktop loaded with the cd I figured it was just a conflict with windows and it would go away after install. I was wrong of course.

Either way I tried everything that has been suggested to me and I can see no reason as to why this is happening. I need this problem fixed though. As I mentioned before I cannot go back to windows because I reformated the whole drive.

---

### Post by robert shearer on 2013-06-15
Ah, that makes a difference then..
You could try booting the live media with the nomodeset option but as you have already installed lets try a workaround...

How to temporarily set kernel boot options on an installed OS 

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a **single boot** by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub.

Select the default ubuntu kernel (usually the top one), and rather than pressing enter, **press E to edit**.

Press DOWN ARROW until you get to the line that starts with...
```
linux /boot
```

and press **END** key to position your cursor at the end of the that line usually ending with &#8220;quiet splash&#8221;.
Now **SPACE** and type   **nomodeset**   then press control+X to boot.

If this works then we can set it as a permanent option in grub.
Report and we can expand...

---

### Post by rdd85 on 2013-06-16
I tried this and it attempted to boot in low graphics mode. After this screen I had the black screen with the cursor but there were a lot of vertical blue lines runnning down the bottom of the screen. It never made it past this screen.

---

### Post by rdd85 on 2013-06-18
I still cannot figure out the problem. I installed linux mint as well and the same problems occur.

---

### Post by cub on 2013-06-18
Mint is also Debian/Ubuntu based. Longshot, but perhaps you should try out another distro like [http://fedoraproject.org/](http://fedoraproject.org/) and see if the drivers there might do some difference?

---

### Post by rdd85 on 2013-06-18
I'll give it a try right now.

---

### Post by rdd85 on 2013-06-18
I just installed Fedora and it did the exact same thing as the other distros. This is so frustrating.

---

### Post by rdd85 on 2013-06-20
I guess no one can help me with this. That's a shame because this is the only board for Ubuntu that seems to actually have people posting.

---

### Post by cub on 2013-06-23
Yeah, I'm running out of ideas. My next step would be to try get hold of a Windows Vista 64 bit version to install to verify it's not hardware related.

---

