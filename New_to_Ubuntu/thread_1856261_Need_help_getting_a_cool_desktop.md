---
title: "Need help getting a cool desktop"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by 450rOOST on 2011-10-07
11.04 installed.  I searched around and tried some things, I installed conky.  Then I just got 'gcalcli'  but the thread I was following was from 2008 so I don't know if all the same commands and applications are the same.

I've seen screenhots of a cpu usage, weather, name and info.  I saw a bunch of cool stuff in this thread [http://ubuntuforums.org/showthread.php?t=281865&highlight=post+conkry](http://ubuntuforums.org/showthread.php?t=281865&highlight=post+conkry)

If anyone want to shoot me some tips that would be cool.  Thanks.

---

### Post by Vaphell on 2011-10-07
check this thread out, it splits VinDSL's conky setup to atoms.
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

### Post by Gawains Green Knight on 2011-10-07
Very cool! Does this work on 11:10?

---

### Post by wildmanne39 on 2011-10-07
Hi, yes it will run in 11.10.

I am using it on 11.04 also.

@450rOOST if you want to make your desktop cooler you can setup the cube and effects in 11.04 by using the guide in my signature.
Thank you

---

### Post by 450rOOST on 2011-10-08
need some help with a basic quetion.

I started the program screenruler, it comes up, how do I keep that running and go back to a command line.


[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/screenruler.png[/IMG]

---

### Post by 450rOOST on 2011-10-08
> **wildmanne39 said:**
> Hi, yes it will run in 11.10.

I am using it on 11.04 also.

@450rOOST if you want to make your desktop cooler you can setup the cube and effects in 11.04 by using the guide in my signature.
Thank you

wildmanne, I went through that guide, enabled the cube, but I it's not working yet.  Any guesses on what I could try.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/cube.png[/IMG]

---

### Post by wildmanne39 on 2011-10-08
Hi, do you have 3d capability? 

Can you see the unity desktop or do you have to use classic mode?

Did you restart your computer after you setup the cube?

Did you set your desktop to four desktops instead of two.

Since you are running in classic did you revert to the previous version of compiz before you setup the cube?
Thank you

---

### Post by 450rOOST on 2011-10-08
> **wildmanne39 said:**
> Hi, do you have 3d capability? 
***I think so, but I guess I'm not sure***

Can you see the unity desktop or do you have to use classic mode?
***classic, I do not know how to change to unity.***

Did you restart your computer after you setup the cube?
***Yes***

Did you set your desktop to four desktops instead of two.
***Yes***

Since you are running in classic did you revert to the previous version of compiz before you setup the cube?
***I think so, I followed the directions, I will try them again.  I just have such little knowledge so far, I don't know what is being talked about.  ***
Thank you

I will go back through the directions first and post back.

---

### Post by 450rOOST on 2011-10-08
I must not be using the right version of compiz, because under effects, he said he check something like 'Show gears'  I don't have that option.

I'll check it out.

---

### Post by wildmanne39 on 2011-10-08
Hi, at the login screen click on your user name then go to the bottom of the screen and see what options you have to boot into.

The one that says just ubuntu is unity if you can boot into it then you have 3d capability if you can not then you may not have installed your video card driver in additional drivers or your system can not run unity there for no 3d effects.
Thank you

---

### Post by 450rOOST on 2011-10-08
> **wildmanne39 said:**
> Hi, at the login screen click on your user name then go to the bottom of the screen and see what options you have to boot into.

The one that says just ubuntu is unity if you can boot into it then you have 3d capability if you can not then you may not have installed your video card driver in additional drivers or your system can not run unity there for no 3d effects.
Thank you

for some reason, it's not going to the login screen like it was before, it just loads up, but then a box comes up and and says it needs my password for a key login or something, I'll restart and see what it says.

I went to additional drivers, it says I've downloaded it but it is not active, how do I activate it?

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/AddDrivers-Graphics-1.png[/IMG]

---

### Post by wildmanne39 on 2011-10-08
Hi, in the first picture of that guide does your synaptic look like that one with the green squares next to the same things that are in that picture.

Do not reinstall compiz yet, it could just be that you did not install all the plugins.

Please post the results of these two commands so I will have a better understanding if you have 3d capability.

```
/usr/lib/nux/unity_support_test -p
```
```
sudo lshw
```
Thank you

---

### Post by wildmanne39 on 2011-10-08
Hi, that is just a bug it is really activated so you do not need to worry about it.

It is in the login screen that I want you to click on your username and follow the directions in my previous post please.
Thank you

---

### Post by 450rOOST on 2011-10-08
> **wildmanne39 said:**
> Hi, that is just a bug it is really activated so you do not need to worry about it.

It is in the login screen that I want you to click on your username and follow the directions in my previous post please.
Thank you

I never get a chance to choose my username, it passes that and goes straight to this.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/IMAG0049.jpg[/IMG]

---

### Post by 450rOOST on 2011-10-08
```
smoker@smoker-Dell-System-XPS-L502X:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
smoker@smoker-Dell-System-XPS-L502X:~$ 


```

```
       product: 0YR8NN
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: .G07TRQ1.CN4864317P0326.
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A06
          date: 07/20/2011
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
          vendor: Intel Corp.
          physical id: 19
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 id=0 threads=8
        *-cache:0
             description: L1 cache
             physical id: 1a
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 1b
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 1c
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-back unified
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 0
             serial: B134F1FF
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: B134F1FE
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:f0000000-f10fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
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
             resources: irq:52 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)
        *-communication UNCLAIMED
             description: Communication controller
             product: 6 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f1c05000-f1c0500f
        *-usb:0
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f1c0a000-f1c0a3ff
        *-multimedia
             description: Audio device
             product: 6 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:53 memory:f1c00000-f1c03fff
        *-pci:1
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f1b00000-f1bfffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1030
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 34
                serial: ac:72:89:39:62:23
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic-pae firmware=17.168.5.2 build 35905 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:51 memory:f1b00000-f1b01fff
        *-pci:3
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f1a00000-f1afffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:f1a00000-f1a01fff
        *-pci:4
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f1900000-f19fffff
        *-pci:5
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) ioport:f1800000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 06
                serial: 14:fe:b5:bc:47:98
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:41 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff
        *-usb:1
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f1c09000-f1c093ff
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:f1c08000-f1c087ff
           *-disk
                description: ATA Disk
                product: WDC WD7500BPKT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX81A61J0591
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=bb77d889
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 5e4ca718-dd45-4e46-99e8-2d56beab7a47
                   size: 587GiB
                   capacity: 587GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-09-09 02:20:35 filesystem=ntfs label=OSDisk state=clean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: ab8b6573-bc49-4f33-924b-c37ba902925c
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 89a56c63-8366-4292-b616-285017a9d405
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-10-06 00:47:07 filesystem=ext4 lastmountpoint=/ modified=2011-10-06 01:05:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,stripe=1,data=ordered mounted=2011-10-08 20:13:14 state=mounted
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: 22f8cb55-2f48-405f-9cce-84a7277a38a8
                   size: 79GiB
                   capacity: 79GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-10-06 00:47:09 filesystem=ext4 lastmountpoint=/home modified=2011-10-08 20:13:16 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,stripe=1,data=ordered mounted=2011-10-08 20:13:16 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW DS-8A5SH
                vendor: PLDS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: XD13
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f1c04000-f1c040ff ioport:efa0(size=32)
  *-battery
       product: DELL
       vendor: SDI
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
       capacity: 57720mWh
       configuration: voltage=11.1V
smoker@smoker-Dell-System-XPS-L502X:~$ 

```

---

### Post by wildmanne39 on 2011-10-08
Hi, enter your password then logout and it will take you to the login screen.
Thank you

---

### Post by 450rOOST on 2011-10-08
> **wildmanne39 said:**
> Hi, enter your password then logout and it will take you to the login screen.
Thank you

I can boot into 'ubuntu'  or 'ubuntu classic'  I am in ubuntu right now.

---

### Post by wildmanne39 on 2011-10-08
Hi, so you have the launcher on the left of the screen when you move your cursor all the way to the left?

According to the information OPEN GL is not working and you have two video cards one an intel and that is known to be a problem especially if the nivida card is optimus, do you know if it is?

Please post the results of this command:
```
lspci | grep VGA
```
Thank you

---

### Post by 450rOOST on 2011-10-08
I do not have the launcher on the left side of the screen, even when I take hover the mouse over there.

```
smoker@smoker-Dell-System-XPS-L502X:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
smoker@smoker-Dell-System-XPS-L502X:~$ 


```

---

### Post by wildmanne39 on 2011-10-08
Hi, that is what I thought, you can not run 3d at this time without some work around I researched but I did not find an answer.

This is beyond my skill set at this time hopefully someone will jump in that has more experience with this issue.
Thank you

---

### Post by 450rOOST on 2011-10-08
> **wildmanne39 said:**
> Hi, that is what I thought, you can not run 3d at this time without some work around I researched but I did not find an answer.

This is beyond my skill set at this time hopefully someone will jump in that has more experience with this issue.
Thank you

no worries, thanks a lost man.  I kinda of figured out some conky stuff, I'm gonna play with that more.  conky looks cool.

---

### Post by wildmanne39 on 2011-10-09
Hi, your welcome!

---

