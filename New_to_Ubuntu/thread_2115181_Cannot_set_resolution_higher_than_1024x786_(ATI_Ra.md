---
title: "Cannot set resolution higher than 1024x786 (ATI Radeon 9550 128MB)"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by DenHeldert on 2013-02-12
Hi all,

I just started using Ubuntu 2 days ago.
Everything went fine, and its easier to use then I thought it would be.
I have one problem though... When configuring my monitor, I cannot set the display higher than 1024x786. I would really like an resolution of 1280x1024, wich I know is supported since I always set it like that when using Windows.

My hardware:
ATI Radeon 9550 128MB
Compaq FS740 CRT Monitor

Really hope someone can help!

Regards,

Nick.

EDIT:
I just tried [this]("http://askubuntu.com/questions/94420/how-do-i-improve-performance-on-an-ati-radeon-9550") but the installer says 'my graphics card is not supported and the installer will now exit'

---

### Post by robert shearer on 2013-02-12
Ubuntu nowdays probes the monitor at each boot and sets the relevant resolution as per the native setting for that monitor.
Unfortunately it expects a report from the monitor and this is not always supplied by CRT's.

Option one... use a LCD monitor.... have you access to a recycling facility that sells cheap lcd screens...?

option two.... set a custom xorg file that dictates a resolution on boot to suit your CRT. (unfortunately this means that without reconfiguring or cancelling the custom xorg file you cannot hook up another monitor and expect it to work)
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Option three.....
 [http://ubuntuforums.org/showthread.php?t=1978302](http://ubuntuforums.org/showthread.php?t=1978302)
seems to be some hack with the VGA cable of the CRT.
I have not tried this and only mention it as a last resort option.

Your card is no longer supported by  ATI  so stick with the Ubuntu supplied open source driver, it really is very good with those older unsupported cards.

---

### Post by DenHeldert on 2013-02-12
Thank you very much for your reply!
Buying an LCD Monitor is no option for me. This is a money-issue.

I looked at option 2, and actually read something like that at Google.
I understand I need to create/modify a file or program called xorg.
I noticed the 'Basic Skeleton' at the top of the page.

- I assume I need to fill in my specific data?
- If yes, what do I need to fill in? I got no clue what I'm looking at.
- Where do I fill that in or place the file?

I also browsed to the section 'Monitor Resolution' but as far as I am concerned,
these pages are written in Chinese. 
I really haven't got a single clue how to achieve this.


Could you please help me get started?

Regards,

Nick.

---

### Post by mastablasta on 2013-02-12
you need to go here on that page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
 
then look at this: 
radeon driver 
&#8226;VGA-0 - Analog VGA output 
&#8226;LVDS - Laptop panel 
&#8226;S-video - Integrated TV output 
&#8226;DVI-0 - DVI output 
 
and then go down to where it says 
**Setting resolution changes in xorg.conf**
 
to get an example. otherwise there is more info in man pages.
 
----
you can also use xrandr mentioned on that website. 
 
see under 
**Adding undetected resolutions**
 
and then a bit lower are instructions on how to set it to be statical not just for current session. i would do it with xrandr as it seems simpler.
 
all of these are preety old school configs... :)

---

### Post by DenHeldert on 2013-02-12
Here is what I did:

**Desktop Shell**

```
login@mypcname ~ $ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
``````
login@mypcname ~ $ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
``````
login@mypcname ~ $ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
``````
login@mypcname ~ $ xrandr --addmode VGA-0 1280x1024_60.00
``````
login@mypcname ~ $ xrandr --output VGA-0 --mode 1280x1024_60.00
```**Console mode:**

```
sudo service mdm stop
``````
sudo X -configure
``````
sudo service mdm start
```**Desktop**

- Renamed xorg.conf.new to xorg.conf
-Apllied the changes in the Monitor section and the Screen Sections:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card0"
    Driver      "modesetting"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "ColorTiling"            # [<bool>]
        #Option     "ColorTiling2D"          # [<bool>]
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "EXAVSync"               # [<bool>]
        #Option     "EXAPixmaps"             # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
    Identifier  "Card1"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card2"
    Driver      "fbdev"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card3"
    Driver      "vesa"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes   "1280x1024"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```**Desktop Shell**

```
sudo cp xorg.conf /etc/X11
```Reboot again.



Result: Ubuntu is so slow, I practically cannot do anything.
I tried the exact same thing using Linux Mint, and there all went fine.
I would really like to use Ubuntu though...

---

### Post by robert shearer on 2013-02-12
> Result: Ubuntu is so slow, I practically cannot do anything.
I tried the exact same thing using Linux Mint, and there all went fine.
I would really like to use Ubuntu though... 

So you now have the desktop resolution you were looking for...?

We assume that the rest of your hardware is of a similar vintage to your monitor and graphics card....?
In which case the performance of Ubuntu with the Unity desktop will be glacial.

What desktop are you using in Mint ???
Try installing that and using it in Ubuntu.
(options could include...
```
sudo apt-get install **lubuntu-desktop**
```
or
```
sudo apt-get install **xubuntu-desktop**
```
both are less resource hungry than Unity.)

Other desktops such as Mint's Mate or Cinnamon can be installed from ppa's. Reply if you need more details.

What are your system specs....
```
sudo lshw
```
run in a terminal and post here within code tags (#...# as in the options bar above the posting window)

---

### Post by DenHeldert on 2013-02-13
Yes, my specs are quite low:

```
description: Desktop Computer
    product: Evo D310
    vendor: Compaq
    serial: 6S32LDBZS00W
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=9E387160-194A-D711-A244-3728CB93511A
  *-core
       description: Motherboard
       product: 0804h
       vendor: Compaq
       physical id: 0
       serial: 6S32LDBZS00W
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 1
          version: 686O2 v3.18
          date: 05/28/2003
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.9
          slot: XU1 PROCESSOR
          size: 2800MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 512KiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: M3 68L6423ETN-CB3
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: 65E202F1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: K
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 1
             serial: 3BDC0773
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 25
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e4000000-e7ffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:2000(size=4096) memory:f8200000-f84fffff memory:e8000000-f81fffff
           *-display:0
                description: VGA compatible controller
                product: RV350 AS [Radeon 9550]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:18 memory:e8000000-efffffff ioport:2000(size=256) memory:f8400000-f840ffff memory:f8000000-f801ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AS [Radeon 9550] (Secondary)
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:f0000000-f7ffffff memory:f8410000-f841ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3440(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3460(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8a00000-f8a003ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:1000(size=4096) memory:f8500000-f87fffff
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 81
                serial: 00:0b:cd:28:dc:4f
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.178.22 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:f8500000-f8500fff ioport:1000(size=64)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:34a0(size=16) memory:60100000-601003ff
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:3000(size=256) ioport:3400(size=64) memory:f8a00400-f8a005ff memory:f8a00600-f8a006ff
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: MAXTOR 6L040J2
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A93.
             serial: 662130241449
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0006c232
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 2ce9fedf-3333-4b01-ac59-86c837230ceb
                size: 35GiB
                capacity: 35GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-02-12 15:58:13 filesystem=ext4 lastmountpoint=/ modified=2013-02-12 19:31:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-02-12 19:31:05 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1535MiB
                capacity: 1535MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1535MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 4
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 14GiB (15GB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=00c27c16
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/niksboss/14G USB
                version: FAT32
                serial: 18b5-c6b5
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
```But all runs fine until I save the xorg.conf in the X11 folder.
I also tried this with a fresh install, without modifying the resolution first.

So *only creating the file* results in the system running tediously slow?

edit: I am definitely going to try that Lubuntu desktop today. It looks much like what I am using now with Mint (MATE desktop)
And thanks for the patience guys, first time Linux user here after 15 years of Windows.
edit2: Can I just install the MATE desktop in Ubuntu?

---

### Post by mastablasta on 2013-02-13
Unity is 3D accelerated. it needs a bit of muscle to move.... an option woudl be to use ubuntu 12.04 and install unity 2D (which was still available for that version). Unity 2D works and acts liek original except it is software accelerated. It doens't need so good GPU and CPU. as robert said best to give the system specs so we know what we are dealing with and then can also help you choose the best desktop environment for the system.

---

### Post by mastablasta on 2013-02-13
> 
[edit: I am definitely going to try that Lubuntu desktop today. It looks much like what I am using now with Mint (MATE desktop)
And thanks for the patience guys, first time Linux user here after 15 years of Windows.
edit2: Can I just install the MATE desktop in Ubuntu?
 
ah you just posted the specs when i typed the post. 
 
ram though slow version should be fine. CPU also. so the only issue is graphics card or porbably only support for it.
 
i suggest using 12.04 with Unity 2D or Gnome fallback mode. 
 
you can install Mate in Ubuntu with a PPA. Mate is a fork of old Gnome. just search the google for how to - for example: 
[http://www.noobslab.com/2012/11/install-mate-14-desktop-in-ubuntu.html](http://www.noobslab.com/2012/11/install-mate-14-desktop-in-ubuntu.html)
 
However a better option might be to use XFCE (found in Xubuntu). i think it is easier to configure than LXDE (Lubuntu). The XFCE desktop is also more mature. while LXDE is still under development. 
 
Other interesting light desktops are Razor qt (like light KDE, still under development), IceWM (windows manager looks kind of like win98) and E17 (found in ubuntu based Bodhi linux)

---

### Post by DenHeldert on 2013-02-13
Ok, Ill give that a try.
Are there any security-related issues in using 12.04 instead of 12.10?

And can you please comment on what I said about creating the xorg.conf file in the X11 folder?
As I said, all runs fine (including Unity) until I create it.
Even without modifing anything.

---

### Post by mastablasta on 2013-02-13
> **DenHeldert said:**
> Ok, Ill give that a try.
Are there any security-related issues in using 12.04 instead of 12.10?

no. 12.04 is supported for 5 years as it is LTS (long term support) release. means it will get security updates and bugfixes for 5 years. 12.10 is supported for 18 months. basically 12.10 is development, kind of testing but stable short term support release. it has plenty new features added that might work smooth or not. usually these new features will get expanded and then polished for next LTS which is in April 2014. the 12.10 also has newer kernel and newer drivers which is better if you have new hardware. but doens't matter as much for the old maschines.
 
> 
And can you please comment on what I said about creating the xorg.conf file in the X11 folder?
As I said, all runs fine (including Unity) until I create it.
Even without modifing anything.
 
unfortunatelly i do not know much about xorg.conf file. or why it would cause system to slow down. it's been too long since i used one. i am sure someone else will know more. though these files are not used often lately. but they are still used on certain occasions.
 
edit: try askign on ubuntu IRC channel or maybe xorg have their own IRC channel.

---

### Post by DenHeldert on 2013-02-13
I created and modified the xorg.conf file in Ubuntu 12.10 and all works fine now.

Thanks all, for the help.

---

