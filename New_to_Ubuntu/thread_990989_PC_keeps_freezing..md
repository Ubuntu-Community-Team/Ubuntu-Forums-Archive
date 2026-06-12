---
title: "PC keeps freezing."
date: 2008-11-23
forum: New to Ubuntu
---

### Post by misswham on 2008-11-23
I have been having the problem of my pc freezing to the point where i have to reboot by pushing the on and off button on the tower.  It just started 3 days ago.  It has become chronic.  I dont know why it is doing this.  Any Ideas?

---

### Post by 01100001 on 2008-11-23
What applications are you running when the PC freezes ? What is your PCs configuration ? What distro do you have installed ?

---

### Post by xravexheavenx on 2008-11-23
How does your CPU and RAM usage look before it freezes?
Is it completely randomly or does it happen on a certain event?

Try Alt+Ctrl+Backspace to reboot X when it freezes to see if it is just an X issue.

---

### Post by Dedoimedo on 2008-11-23
Can you provide more details?
As many as you can ...
Thanks,
Dedoimedo

---

### Post by Gone fishing on 2008-11-23
If its random - I'd probably go for hardware.

Is the CPU overheating - fins blocked by dust? after its frozen whats the CPU temp?
is the RAM OK? the live CD has a mem test function.
Is the graphics card overheating? is it in its slot correctly?
Power supply OK?

---

### Post by misswham on 2008-11-23
Pidgeon is freezing and when i surf it freezes.  No particular order.  Also the pc is moving very slowly at times.  I dont know anything about ram and all that stuff.  This JUST started fri nite.  When I say freeze I mean the pc gets stuck and then the page i am on goes that dark grey and sometimes i will try to close and it asks force quit and i hit that and it just freezes solid.  it happens with pidgeon and surfing on firefox.

---

### Post by jadhav333 on 2008-11-23
do u...
  have  nvidia / ati display card
  have a wifi / wimax connection
    chances are there is compatibility issue between the two and linux 
    kernel.

Is ur problem similar to:
  [https://answers.launchpad.net/ubuntu/+question/52240]("https://answers.launchpad.net/ubuntu/+question/52240")

---

### Post by hypert on 2008-11-23
What do you have installed on your computer 8.10,8.4.

---

### Post by misswham on 2008-11-23
i have 8.4.  i have invidia, but i have had linux 8.4 for 6mths and this just started happening.

---

### Post by Michael.Godawski on 2008-11-23
It is not the ultimate answer but:

I also had some freezes with 8.04. But since the new release they are all gone. So try to use the newest version.

Perhaps we start with some basic specs; please post the results of these commands:

```
sudo lshw
lspci
free
```

---

### Post by Tomatz on 2008-11-23
Firstly, have you updated/upgraded recently?

Also, check this thread on how to shutdown cleanly during a freeze:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

---

### Post by hypert on 2008-11-23
When i upgraded to ubuntu 8.10 it keep freezing I opened Applications and clicked on system tools and clicked virus scanner  go to the top to scan click it go down to recursive scan click file system and then ok it while take a while but when computer  freezes up its usally because of a virus.

---

### Post by iponeverything on 2008-11-23
You could try slapping the linux-backports-modules-<version>-generic


```
sudo apt-get install linux-backports-modules-2.x.xx-x-generic
```

it cleared up my lockups on 8.0.4

---

### Post by Tomatz on 2008-11-23
> **hypert said:**
> When i upgraded to ubuntu 8.10 it keep freezing I opened Applications and clicked on system tools and clicked virus scanner  go to the top to scan click it go down to recursive scan click file system and then ok it while take a while but when computer  freezes up its usally because of a virus.

Your thinking windows lol ;)



Its probably a hardware incompatibility with the kernel and/or drivers (possibly graphics drivers)

Try installing the backported (latest) kernel modules as said. If you have no joy with that:

Open a terminal and type **lshw**.

Post the output here ;)

---

### Post by Tomatz on 2008-11-23
> **iponeverything said:**
> You could try slapping the linux-backports-modules-<version>-generic


```
sudo apt-get install linux-backports-modules-2.x.xx-x-generic
```

it cleared up my lockups on 8.0.4

**_This is a good suggestion._**

The actual version is:

**linux-backports-modules-2.6.24-16-generic**

To install, open a terminal and copy and paste the following:

```
sudo apt-get install linux-backports-modules-2.6.24-16-generic
```

;)

---

### Post by misswham on 2008-11-23
this is the outcome of the sudo command

 *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.11.2
          size: 2GHz
          capacity: 2GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi4
          logical name: scsi5
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-disk
             description: ATA Disk
             product: WDC WD2500BB-22R
             vendor: Western Digital
             physical id: 0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 20.0
             serial: WD-WMANK3703306
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=3c3c3c3c
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 04ef25eb-2901-1446-8fd9-ffdd1120a3a5
                size: 69GiB
                capacity: 69GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-10-26 15:37:43 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 163GiB
                capacity: 163GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   logical name: /dev/.static/dev
                   capacity: 161GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 2588MiB
                   capabilities: nofs
        *-cdrom
             description: DVD writer
             product: DVDRW SHW-160P6S
             vendor: LITE-ON
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: PGS1
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: SB Audigy LS
             vendor: Creative Labs
             physical id: 6
             bus info: pci@0000:04:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant
             physical id: 7
             bus info: pci@0000:04:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:04:09.0
             version: c0
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:19:21:02:c1:9c
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.15.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 8
          bus info: usb@1:6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             version: 1.01
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             version: 1.02
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             version: 1.03
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde


lspci commands

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:07.0 Communication controller: Conexant HSF 56k Data/Fax Modem
04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

free

            total       used       free     shared    buffers     cached
Mem:        905280     565716     339564          0      15244     323968
-/+ buffers/cache:     226504     678776
Swap:      2650684          0    2650684


this is the outcome from the three commands above

---

### Post by misswham on 2008-11-23
which key is the printscreen key?

---

### Post by perlluver on 2008-11-23
Print screen is also System Request or SysRq.  Have you tired turning off compiz?  Go to System>Preferences>Appearance, go to the last tab visual effects, and select none.  When I get grey screens, they are usually from compiz.

---

### Post by Tomatz on 2008-11-23
Hmmm doubt it would be a gpu driver problem as nvidia support is quite good under linux.

Did you try installing the backported kernel modules?

```
sudo apt-get install linux-backports-modules-2.6.24-16-generic
```

---

### Post by theamber on 2008-11-24
By the process of elimination, try different Ram sticks, try different hard disk.Try different operating system. Monitor the temp. of the CPU when it freezes. Narrow down the specific area of the problem it could be most likely in your mother board a bad connection may need to use a hot air heat gun to resolder it.

---

### Post by misswham on 2008-11-25
oh my I havent a CLUE what the last person said.  I am a novice when it comes to stuff like that.  I am internet savvy but not hardware savvy.

---

### Post by Olivier2371 on 2008-11-25
Can you give me the make and model of your laptop(eg..Acer9302wsmi)

---

### Post by Tomatz on 2008-11-25
> **misswham said:**
> oh my I havent a CLUE what the last person said.  I am a novice when it comes to stuff like that.  I am internet savvy but not hardware savvy.

Sorry ;)

Go to ***applications (top Rh), accessories, terminal***

**Copy and paste** the following command into the terminal:
```

sudo apt-get install linux-backports-modules-2.6.24-16-generic
```

Press **return**

Enter your **password** (no text will appear)

Once done **restart the computer**


Hopefully that will fix the problem ;)

---

### Post by Olivier2371 on 2008-11-25
Tomatz,

I am not so sure that will fix the problem. I have the same hardware than misswham and that didn't solve it for me. 

I had to disable the visual effect in the appearance window.

I am still trying to find the answer to my riddle.

---

### Post by Tomatz on 2008-11-25
> **Olivier2371 said:**
> Tomatz,

I am not so sure that will fix the problem. I have the same hardware than misswham and that didn't solve it for me. 

I had to disable the visual effect in the appearance window.

I am still trying to find the answer to my riddle.

Is it intel chipset (gpu)?

---

### Post by Olivier2371 on 2008-11-25
Tomatz,

What do you mean by Is it intel chipset (gpu)? 

She has GeForce go x-press 6150 LE.
I have geforce go x-press 6100.

Her motherboard is based around NVIDIA C51, so is mine.

---

### Post by halitech on 2008-11-25
do you have the LiveCD (typical install CD for Ubuntu)? if you do, try booting it and when it first starts, you should see an option to run memtest86+. Run that for a few hours and see what happens.

---

### Post by Tomatz on 2008-11-25
> **Olivier2371 said:**
> Tomatz,

What do you mean by Is it intel chipset (gpu)? 

She has GeForce go x-press 6150 LE.
I have geforce go x-press 6100.

Her motherboard is based around NVIDIA C51, so is mine.

Intel gpu's can cause problems but its obviously not that.

Try the memtest (good and valid point) but i doubt its that as it only happens with compiz enabled;)


P.s are you using intrepid or hardy?


@OP

Run the following command in a terminal:

```
metacity --replace
```

See if the problem persists ;)

---

### Post by halitech on 2008-11-25
it *might* be a case that only when compiz is enabled that its using enough ram to get to the trouble point in the ram. Not saying it is but its an eay thing to rule out this way.

---

### Post by Olivier2371 on 2008-11-25
Personally I have already tried the memory check(took long enough).
Me  I am running on 8.04. I already have the latest kernel.

For the moment it escape me. But they aren't any problem which doesn't have a solution.

It's between the theme manager and compiz.

---

### Post by OisinT on 2008-11-25
Hey.. I'm having serious freezing problems also with 8.10 even when nothing much is running.  I ran the commands you suggested and it looks to me like I'm in serious need of more memory.  Would you think this is my problem?

```
oisint@OisinT1:~$ sudo lshw
[sudo] password for oisint: 
oisint1                   
    description: Desktop Computer
    product: RA917AA-ABU m7580.uk
    vendor: HP Pavilion 061
    version: 0ny0114RE101EMER200
    serial: CZX6318WJW GB630
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00CEE57F-E98F-1110-A5EF-8D30641B1DAF
  *-core
       description: Motherboard
       product: EMERY2
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 2.00
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.15 (06/23/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Pentium(R) D CPU 3.20GHz
          slot: Socket 775
          size: 2400MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 10
             slot: L3 Cache
             capabilities: synchronous internal varies
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 6
          bus info: cpu@1
          version: Intel(R) Pentium(R) D CPU 3.20GHz
          slot: Socket 775
          size: 2400MHz
          capacity: 3800MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: d
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: f
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 11
             slot: L3 Cache
             capabilities: synchronous internal varies
     *-memory
          description: System Memory
          physical id: 2e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7600 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
           *-network:0 UNCLAIMED
                description: Ethernet controller
                product: AR5413 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=168 maxlatency=28 mingnt=10
           *-multimedia
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 4
                bus info: pci@0000:02:04.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134
           *-network:1
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:17:31:f0:2b:af
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801GH (ICH7DH) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD-RAM writer
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open
           *-cdrom:1
                description: DVD reader
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio dvd
                configuration: status=open
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk:0
                description: ATA Disk
                product: ST3200827AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AH
                serial: 4ND4DZAX
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cab10bee
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 2cdd4917-fb62-4291-9ce9-89ae4d4afe24
                   size: 180GiB
                   capacity: 180GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-09-11 02:08:08 filesystem=ext3 modified=2008-11-25 14:40:24 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-25 14:40:24 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5891MiB
                   capacity: 5891MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5890MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3200827AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 3.AH
                serial: 4ND4EG6L
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cd1ebaaf
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/SecondaryDrive
                   version: 3.1
                   serial: 185954c3-5374-c04e-9016-310b2d152121
                   size: 186GiB
                   capacity: 186GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-08-02 22:33:24 filesystem=ntfs label=NEW_VOLUME mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi:0
          physical id: 1
          bus info: usb@4:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
     *-scsi:1
          physical id: 2
          bus info: usb@5:4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:b3:d9:c7:0b:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
oisint@OisinT1:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
02:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
02:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
oisint@OisinT1:~$ free
             total       used       free     shared    buffers     cached
Mem:       2056036    2029896      26140          0     180368     777788
-/+ buffers/cache:    1071740     984296
Swap:      6032368     117744    5914624

```

also, what are the current linux-backports-modules-<version>-generic for 8.10?

---

### Post by iponeverything on 2008-11-25
I don't think that there is a backports from jaunty available for ibex as I don't think that the kernels being used for each have diverged. Jaunty is still quite fresh.

Not having enough memory is not the cause of lockups - your box will slow down a lot if goes to swap, but not lockup. And 2 Gigs is more that enough for most people. Of course it does depend on what your doing, running VM's for example will require more memory.

It might be better if you started a fresh thread, I don't think that problem is the same as the OP.

---

### Post by Tomatz on 2008-11-26
> **iponeverything said:**
> I don't think that there is a backports from jaunty available for ibex as I don't think that the kernels being used for each have diverged. Jaunty is still quite fresh.

Not having enough memory is not the cause of lockups - your box will slow down a lot if goes to swap, but not lockup. And 2 Gigs is more that enough for most people. Of course it does depend on what your doing, running VM's for example will require more memory.

It might be better if you started a fresh thread, I don't think that problem is the same as the OP.

The OP is running hardy ;)

---

### Post by Tomatz on 2008-11-26
> **Olivier2371 said:**
> Personally I have already tried the memory check(took long enough).
Me  I am running on 8.04. I already have the latest kernel.

For the moment it escape me. But they aren't any problem which doesn't have a solution.

It's between the theme manager and compiz.


You could try upgrading to the latest version of compiz:

[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)

If you need any help, post back ;)

---

### Post by Olivier2371 on 2008-11-26
Thanks for the advise but I have done it already.

The problem still remain.

---

### Post by Tomatz on 2008-11-26
> **Olivier2371 said:**
> Thanks for the advise but I have done it already.

The problem still remain.

Have you tried envyng?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Olivier2371 on 2008-11-26
Sorry for not responding earlier,

No I haven't tried it yet, but if I want to play with effect I usually switch to Enlightenment.

But thanks for the link.

Well ok I give it a try.

---

### Post by Tomatz on 2008-11-26
> **Olivier2371 said:**
> Sorry for not responding earlier,

No I haven't tried it yet, but if I want to play with effect I usually switch to Enlightenment.

But thanks for the link.

Well ok I give it a try.

Cool :)

Just be careful. Reinstalling GPU drivers can be a pig lol.

---

### Post by Olivier2371 on 2008-11-26
Well I have installed Envyng. What's very strange is I am sure I had the latest driver for the GPU, but envy downloaded it directly from NVIDIA, and installed it. At the moment I am running compiz-fuzion.

What's strange in that in he appearance windows for the desktop effect nothing is selected. But the system hasn't froze yet, so I cross my fingers.

---

### Post by Tomatz on 2008-11-26
> **Olivier2371 said:**
> Well I have installed Envyng. What's very strange is I am sure I had the latest driver for the GPU, but envy downloaded it directly from NVIDIA, and installed it. At the moment I am running compiz-fuzion.

What's strange in that in he appearance windows for the desktop effect nothing is selected. But the system hasn't froze yet, so I cross my fingers.

Use compizconfig instead:

```
sudo apt-get install compizconfig-settings-manager
```

Its much better anyway.

P.s

It will be under ***system, preferences***

---

### Post by Olivier2371 on 2008-11-26
yes, everything has already been set.

Thanks

What happened with OisinT?

---

### Post by Tomatz on 2008-11-27
I dunno? He's quite a new user so i'll pm him in a bit with full instructions.

:)

---

### Post by Olivier2371 on 2008-11-27
Tomatz,

By the way the system froze again twice this morning. I have disabled compiz, and everything is find now.

I think I will stick with Enlightenment.

---

### Post by Tomatz on 2008-11-27
> **Olivier2371 said:**
> Tomatz,

By the way the system froze again twice this morning. I have disabled compiz, and everything is find now.

I think I will stick with Enlightenment.

Damn :(

Thought we had it fixed then. I remember back when gutsy first came out compiz kept freezing my system. The only way i could fix it was by compiling compiz from source. Maybe something you could look into? Its pretty straightforward once you get all the deps installed.

;)

---

### Post by Olivier2371 on 2008-11-27
Yes, I know what you mean. But for the moment I will be working on enlightenment.

---

