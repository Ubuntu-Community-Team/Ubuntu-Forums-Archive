---
title: "AMD64 + ATI Problems"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by gavinjay on 2008-06-18
Hi all,

My first post.

Real noob to ubuntu/linux...

hated it for many years... swore by MS =/ 
...and now im here.

Im very technically inclined anyway, and a fast learner... willing to learn lots.


So I m running 64 bit ubuntu on my amd x64 cpu with ATIX1600
Things arent going well.

I have the ATI drivers enabled and inuse under Hardware Drivers.
im running compiz 
and have the ATI Catalyst Control center installed
it used to work
now it doesnt... i think ever since i installed and then enabled all the settings (in Appearance - Visual Settings - Extra) for compiz

It crashes when trying to run it saying...
Initialization error
There was a problem initializing Catalyst Control Cernter Linux edition. IT could be caused by the following.

No ATI graphics adapter is installed, or the ATI driver is not functioning properly.
Please instll the ATI driver appropriate for you ATI hardware, or configure using aticonfig.




Also trying to get my DWA 520 running, with no sucess.

Ill try to post as much details as possible.

Any help is greatly appreciated.

Gavin.


lshw:

gavinjay-u                
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=E084E06E-F19B-DA11-9284-0015F2E2DEFC
  *-core
       description: Motherboard
       product: A8R-MVP
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0602 (03/02/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.1
          serial: To Be Filled By O.E.M.
          slot: Socket 939
          size: 2200MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI-X Root Port
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: RV530 [Radeon X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV530 [Radeon X1600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ALi Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-network:0 UNCLAIMED
                description: Network controller
                product: AR5416 802.11abgn Wireless PCI Adapter
                vendor: Atheros Communications Inc.
                physical id: 12
                bus info: pci@0000:02:12.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 13
                bus info: pci@0000:02:13.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network:1
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 14
                bus info: pci@0000:02:14.0
                logical name: eth0
                version: 13
                serial: 00:15:f2:e2:de:fc
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=199.34.57.102 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=32 mingnt=16 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: High Definition Audio/AC'97 Host Controller
             vendor: ALi Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 maxlatency=80 mingnt=16 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: ALi Corporation
             vendor: ALi Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 1e.1
             bus info: pci@0000:00:1e.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: c8
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=32 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM_GSA-H10L
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: LX08
                   serial: M006CFA3724
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma4 status=nodisc
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD reader
                   product: SAMSUNG DVD-ROM SD-616E
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: F503
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2 status=nodisc
        *-ide:1
             description: IDE interface
             product: ULi M5288 SATA
             vendor: ALi Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=128 module=ahci
           *-disk:0
                description: ATA Disk
                product: WDC WD360GD-00FN
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 35.0
                serial: WD-WMAH91220290
                size: 34GiB (37GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1446e3b8
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: f19c2182-983b-463e-8ad2-5c74cd4e8ee6
                   size: 33GiB
                   capacity: 33GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-17 17:47:56 filesystem=ext3 modified=2008-06-18 09:45:19 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-06-18 09:36:58 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1490MiB
                   capacity: 1490MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1490MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: HDS728080PLA380
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: PF2O
                serial: PF1B75E7SPGYMM
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7f1c9ad0
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: fb184d0b-0b16-451a-9fa2-b5031028425c
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-18 00:29:02 filesystem=ext3 modified=2008-06-18 00:29:18 state=clean
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp



lspci:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)
00:1e.0 ISA bridge: ALi Corporation Unknown device 1575
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8)
00:1f.1 IDE interface: ALi Corporation ULi M5288 SATA (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:12.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
02:13.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:14.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by ajgreeny on 2008-06-18
If you are running 8.04 and have recently updated your kernel you may need to reinstall the proprietary ati driver.  Any kernel updates will mean that the driver has gone back to the system default, probably ati, instead of fglrx.

Have a look in synaptic>>File>>History to see if you updated to the 2.6.24-19 yesterday.  If so, that will be the problem, I think.

---

### Post by bufsabre666 on 2008-06-18
first try the old

```
sudo aticonfig -initial --force
```

then ctrl+alt+bckspce

if that doesnt work reinstall them with envy


```
sudo apt-get update && sudo apt-get install envyng-core envyng-gtk
```

when thats done eith open the gui version under applications->system tools
or
```
sudo envyng -t
```

install the ati drivers this way, it configures your system for you, installs CCC and is alot more of an updated version than the one form the restricted manager

---

### Post by gavinjay on 2008-06-19
well i got the ATI driver working...
loads fo problems and frustration.

in addition...
i think i broke my TV.

i have a monitor on here now and was running it on what i eventually want to be my main screen...
i think the default settings in the ATI control cernter had the settings too high for the refresh rate...
now my LCD is left with this weird flickering =/
is it permenant? dunno.

soo i got the vid stuff going ok.

but the dlink...
DWA 542...
Cant seem to find easy to follow stuff on the net about it...
does having that + a 64 bit OS change anything?

---

### Post by gavinjay on 2008-07-04
so i still have no idea how to get my dlink card working...
i dled the drivers and i have them enabled under "hardware drivers"

sae with the ATI
but now it stopped working again..

i was playing around with a few things..
trying to get my X1600 to default to a resolution of 60hz on my screens
cuz its hooked up to one monnitor and one LCD tv
not capable of anything higher than 60hz
i realised that when the tv was ruined! funny flickeing on it
after it was running with my ubuntu system

thats now gone away thankfully
but only as long as i dont let it run at 85hz for too long

85 hz was the default
i played around in xorg.conf to add some settings for the vertical/horizontal refresh

then my ati card went all funny again.

its now booting up and running in low graphics mode.

i tried to ununstall fglrx and reinstall
i tried to remove some compiz apps and reinstall
and the python compiz app
which was what fixed the ati problem the first time...

now im running in low gfx mode
it says its using my ati driver (hardware drivers)

when i try this command:
sudo aticonfig --intital --force it says 

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11


any help??

---

### Post by ZabiGG on 2008-07-05
In linux, you have to solve one issue at a time. Let's start with your graphics card.

Your xorg.conf file is probably corrupted.

You will have to use a terminal. Please write down these steps and follow them to the letter.

1) enter
```
CRTL-ALT-F1
```you will enter terminal mode

2) enter your username
3) enter your password

4) you need to shut down the graphical user interface. If you are using Gnome, enter:
```
sudo /etc/init.d/gdm stop
```(you might be asked for your password again. enter it)

- if you are using kubuntu, replace gdm by kdm

5) you need to create a fresh xorg.conf file. Enter:
```
sudo dpkg-reconfigure xserver-xorg
```

6) answer the questions, use the arrows to move and select, enter once on OK.

7) the system will create a new file and backup the old one

8) delete the old ATI configuration file if it exists. The rm command is very dangerous and should be used as instructed here only. If you don't specify the exact path and file, you might delete your entire system.
```
sudo rm /etc/ati/amdpcsdb
```9) create a new configuration file for your ATI driver. Enter
```
sudo aticonfig --initial -f
```10) you need to restart the graphical user interface. Enter:
```
sudo /etc/init.d/gdm start
```- if you are using kubuntu, replace gdm by kdm

11) type
```
exit
```12) Move to the graphical user interface. Enter:
```
CRTL-ALT-F7
```13) Before you log in, click: Session > GNOME (or KDM, as applies)
(if your last login was in low graphics mode, you will revert to low-graphics mode until you specify a normal gnome login as instructed) 

14) Log in

15) System > Preferences > Screen resolution -- to choose your screen resolution.

Hope this helps,

Z.

---

