---
title: "Trying to make Ubuntu work on my Lenovo Z570"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by rhino.freak on 2016-09-09
Hello all, a first time Linux user and installed Ubuntu 16.04 as a friend suggested.

Now I came here after a week of head banging and when I really don't have any other choice. I've tried numerous amounts of "solutions" to my problems but I couldn't fix some.

First of all: 

1. Brightness controls don't work. I'm always on maxed out brightness. Tried many solutions, writing 20-intel.conf files and 20-nvidia.conf files but they both ended up with my pc not booting up and had to delete those files at the end. Installed an app "brightness-control" but that too stopped working later.
Just found out I can change my brightness manually using this:

_[FONT=Whitney]echo 150 | [/FONT]_[FONT=Whitney]_sudo_[/FONT]_[FONT=Whitney] tee /sys/class/backlight/intel_backlight/brightness[/FONT]_

this I found from here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1255428](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1255428) -- this bug is unfixed still as I can see.


2. WiFi problems. My wireless card is Qualcomm Atheros AR9285. The thing is, sometimes the WiFi works perfectly, just like it should. No problems at all. But sometimes, after boot, the WiFi won't work. In the WiFi menu on top, Enable networking is ticked but Enable WiFi is unticked and ticking it doesn't do anything. I've tried network manager resets and many other solutions but nothing works. I just restart my pc and *hope* it works next time on boot.
Output of LSPCI - [http://pastebin.com/raw/ibNcaXec](http://pastebin.com/raw/ibNcaXec)

3. Booting problems. First of all I see a purple screen for about 15 seconds or so.. 
Then it shows up some code saying: 
/dev/sda2 clean etc etc.. 
Followed by a black screen for another 20 seconds then getting to the desktop.
It's slower than windows which is not how it's supposed to be.
During shutting down, I see Ubuntu logo and the loading dots animation gets stuck and I have to manually force close the laptop using the power button hold. -- found same issue here: [https://ubuntuforums.org/showthread.php?t=2292569](https://ubuntuforums.org/showthread.php?t=2292569)

Output of DMSEG- [http://pastebin.com/raw/CmhGffyY](http://pastebin.com/raw/CmhGffyY)


PC specs-
core i5-2410M @ 2.30Ghz
4gb Ram
1 gb Nvidia GeForce GT 520M graphics card
750gb HDD

Now I'm starting fresh again, will dedicate as much time as I can to fix these all issues and I want your help!
I'll provide any information you need please just ask. And sorry I'm still new to Ubuntu, I don't know much.

Ps: currently the Ubuntu is installed on all of my 750gb without partition, would someone please tell me how do I partition it safely so I can dual boot windows for my college softwares? 

Many thanks in advanced!

---

### Post by rhino.freak on 2016-09-12
I want to give an update to this:

The brightness issue, I have almost done a workaround with it by making scripts and assigning them keyboard shortcuts, thanks to my friend here. But since there's "SUDO" in the main brightness changing command, it doesn't work. Executing the command from terminal works since it asks me to type my password there. Any helps?
Wifi issue seems almost solved. It works on boot normally though when I restart, it doesn't. I can live with that I guess.

So only the slow boot problem remains.. help please!!

---

### Post by rhino.freak on 2016-09-14
is there no one who can give a reply atleast?

---

### Post by mastablasta on 2016-09-14
> **rhino.freak said:**
> I want to give an update to this:

The brightness issue, I have almost done a workaround with it by making scripts and assigning them keyboard shortcuts, thanks to my friend here. But since there's "SUDO" in the main brightness changing command, it doesn't work. Executing the command from terminal works since it asks me to type my password there. Any helps?

you need to add the script to sudoers file. check here for example:
[SIZE=2]http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password
[/SIZE]

slow boot - sorry i can't access pastebin at work. however you can on boot disable the splash screen. hold shift on boot to Access grub then delete:

```
[FONT=Courier New]quiet splash
```

from ```
GRUB_CMDLINE_LINUX_DEFAULT=”***quiet splash***”
```
[/FONT]
This should work and you should see text going on screen. in dmesg you can see what thing took a long time to be completed.

not sayign this is the case , but my experience with nVidia in Windows XP is it is dumb way to boot. i have a VGA monitor and HDMI TV connected to the desktop GPU. everything is set to VGA monitor being the only active screen. now here is what happens on boot. it first goes to TV (even if it's turned off) up until when it loads the OS in final stages it swtiches to VGA pšort and displays it all propperly. upon fresh driver install it would ignore the VGA even if i disconnect the HDMI port and leave VGA only on. 

so yeah i am not surprised if they made something messy Linux. particulary with optimus setup which i am not sure it is still supported.

---

### Post by mörgæs on 2016-09-15
In addition to the advice above I suggest that you run```
 sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. It will show the hardware details.

---

### Post by rhino.freak on 2016-09-15
Thanks for some pointers!
I'll do the boot and grub thingy at the earliest and report back!
Meanwhile, here's my sudo lshw output:
```
rohan-ideapad-z570            description: Notebook
    product: HuronRiver Platform (System SKUNumber)
    vendor: LENOVO
    version: Ideapad Z570
    serial: WB02578132WB01072119
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=notebook family=HuronRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=9E9BE700-B492-11E0-8C2F-BC502282A01E
  *-core
       description: Motherboard
       product: Emerald Lake
       vendor: LENOVO
       physical id: 0
       version: FAB1
       serial: WB02578132
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 45CN34WW
          date: 05/12/2011
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 30
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          serial: Not Supported by CPU
          slot: CPU
          size: 1221MHz
          capacity: 2900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 31
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 32
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 33
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: RMT1950MD58E8F1333
             vendor: Fujitsu
             physical id: 0
             serial: 42CF7618
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: RMT1950MD58E8F1333
             vendor: Fujitsu
             physical id: 2
             serial: 414BC228
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0000000-f0ffffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF119M [GeForce GT 520M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:30 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
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
             resources: irq:27 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:28 memory:f1605000-f160500f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f160a000-f160a3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: Lenovo easy camera
                      vendor: 5618006211B734WL
                      physical id: 5
                      bus info: usb@1:1.5
                      version: 25.17
                      serial: 200901010001
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:f1600000-f1603fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f1500000-f15fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: d0:df:9a:8c:ed:8b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.4.0-36-generic firmware=N/A ip=192.168.15.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f1500000-f150ffff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) ioport:f1400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 05
                serial: f0:de:f1:6e:dc:d7
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:25 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f1609000-f16093ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Generic USB device
                      product: USB2.0-CRW
                      vendor: Generic
                      physical id: 6
                      bus info: usb@2:1.6
                      version: 39.60
                      serial: 20100201396000000
                      capabilities: usb-2.00
                      configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:f1608000-f16087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f1604000-f16040ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD7500BPVT-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A02
             serial: WD-WXJ1A51A5126
             size: 698GiB (750GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=d4fe8376-8665-4e23-87c0-711b337de1cf logicalsectorsize=512 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: 0b30-c0f8
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 8b832385-71cd-4de0-b0d9-692a346c1a97
                size: 694GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-09-05 15:23:55 filesystem=ext4 lastmountpoint=/ modified=2016-09-15 22:13:27 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-09-15 22:13:33 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 6ce4e8ec-7f42-44f1-8dfe-1ed3c0182d04
                size: 4008MiB
                capacity: 4008MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8B1AS
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 8.20
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: Smart Battery
       vendor: Intel Corp.
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
  *-power UNCLAIMED
       description: TBD by ODM
       product: TBD by ODM
       vendor: TBD by ODM
       physical id: 2
       version: 1.0
       serial: TBD by ODM
       capacity: 32768mWh

```

---

### Post by mörgæs on 2016-09-16
The output shows that the BIOS number is 45CN34WW. 

Several updates have been released after 34. It might solve the shutdown problem though I can't promise anything.

---

### Post by rhino.freak on 2016-10-28
> **mörgæs said:**
> The output shows that the BIOS number is 45CN34WW. 

Several updates have been released after 34. It might solve the shutdown problem though I can't promise anything.

I tried to update the bios but can't do it. All the available methods to update is via Windows :/

Which brings me to my next question;
I have a total of 750gb hard drive and it appears to be that the Ubuntu is installed on my whole disk as 1 drive or something.
Like this:

/dev/sd1 - EFI System Partition - fat32 - 512MB
/dev/sd2 - ext4 - 694.22GB
/dev/sd3 - linux-swap - 3.92GB
 
When I click on "RESIZE /dev/sd2", the minimum size and maximum size are same as 710882MB. I cannot change the new size of the disk and create more partitions. Help please :(

---

### Post by mörgæs on 2016-10-29
If you do a live boot using Freedos can you then update the BIOS?

---

