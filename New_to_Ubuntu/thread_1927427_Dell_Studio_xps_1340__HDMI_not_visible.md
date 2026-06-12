---
title: "Dell Studio xps 1340  HDMI not visible"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by Morozov on 2012-02-18
Hi Everyone,
Dell Srudio xps 1340 users, does some figure out how to use HDMI output. Im running 11.10 Oneric 64 Bit with NVIDIA latest driver 295.20 and I don't see HDMI at all, I've been trough forum days and so far so some old ones with slight different issues (no sound, black zones etc.)
Please share if your video card working all &#733;Win7&#733; driver option
Regards

---

### Post by Morozov on 2012-02-18
[SIZE=2]Hi, I've been through post today and fount dated few days back on HDMI IPOD issue similar to my. 
I wonder if  you guys can help me with NVidia GeForce 9400M card. I'm running 11.10 64Bit  Oneric and manage to set second monitr (not quiet well ectually, it only work as twin view, when I select separate X screen and reboot X server I can go to second monitor with mouse, it has background wallpaperand just about it (I can't do nothing on it or with it)). I manage to load latest 295.20 NVIDIA driver from ubuntu-x-swat  but since I've installed Ubuntu (two month ago for a first time)  I've never manage to get HDMI working so if you please can lead me  through, what should I check to get things right...

Appreciated your help [/SIZE][SIZE=2]
Alex
with TV HDMI cable connected my xrandr and lspci and NVIDIA sys info below
alex@alex-Studio-XPS-1340:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0* 
   1024x768       51.0     52.0  
   840x525        53.0  
   832x624        54.0  
   800x600        55.0     56.0     57.0     58.0     59.0  
   800x512        60.0  
   720x450        61.0  
   720x400        62.0  
   700x525        63.0  
   680x384        64.0     65.0  
   640x512        66.0     67.0  
   640x480        68.0     69.0     70.0     71.0     72.0  
   640x400        73.0  
   640x350        74.0  
   576x432        75.0     76.0     77.0     78.0     79.0     80.0  
   512x384        81.0     82.0     83.0     84.0     85.0  
   416x312        86.0  
   400x300        87.0     88.0     89.0     90.0     91.0  
   360x200        92.0  
   320x240        93.0     94.0     95.0     96.0  
   320x200        97.0  
   320x175        98.0  
alex@alex-Studio-XPS-1340:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

[/SIZE]

---

### Post by pqwoerituytrueiwoq on 2012-02-18
1) plug in hdmi tv/monitor
2) [http://imgur.com/EbCX1](http://imgur.com/EbCX1)
3) set it the way you want it (twin view is good for a test /same screen resolutions)
4) if you can get hdmi sound please tell me how been trying for days... 

dont use xinerama  the display will lag like hell


one you have the second x server up run this command
go to screen 2:
xdotool mousemove --screen 1 50 50
go to screen 1:
xdotool mousemove --screen 0 50 50

should only be needed if both screens are positioned absolute

---

### Post by Morozov on 2012-02-19
hello my friend, That would be second move for me. First I need to find my HDMI port (I can't see it). Attached Nvidia server screen shoot with cable in and TV on. ( with the cable or without I have this CRT screen present and can only switch it on as separate screen (nothing happening with screen on and   settings saved to X config. file. I've got this screen from the moment I installed proprietary NVIDIA drivers. (Ubuntu display switching page became inactive, I can't ether detect screens or switch in between)

Regards
Alex

---

### Post by pqwoerituytrueiwoq on 2012-02-19
post output of lspci -v
is this hdmi part of the motherboard or on a discrete GPU?

i know with audio on my system
lucid's kernel would not load a driver
maveric's loads a driver but does not work
natty's loads a driver and it works (shows up in sound preferences) but seems mute
yes i unmuted everything in alsamixer on every chip

---

### Post by Morozov on 2012-02-19
Ok, here  lspci -v with that (CRT secont screen enabled as separate screen, cable to TV connected and TV saying no signal on HDMI)
I have I think build in video card (have seen it in some other posts)
```
alex@alex-Studio-XPS-1340:~$ xranrd --auto
No command 'xranrd' found, did you mean:
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xranrd: command not found
alex@alex-Studio-XPS-1340:~$ xrandr --auto
xrandr: Failed to get size of gamma for output default
alex@alex-Studio-XPS-1340:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 1c00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Dell Device 0271
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: Dell Device 0271
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 2000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: Dell Device 0271
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f0600000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f0886000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f0889000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f0887000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f0889400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    Memory at f0880000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: f0500000-f05fffff
    Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f0888000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30d0 [size=8]
    Memory at f0889c00 (32-bit, non-prefetchable) [size=256]
    Memory at f0889800 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0271
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 40
    I/O ports at 30e8 [size=8]
    I/O ports at 30dc [size=4]
    I/O ports at 30e0 [size=8]
    I/O ports at 30d8 [size=4]
    I/O ports at 30c0 [size=16]
    Memory at f0884000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: ac000000-aeffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: aa000000-aaffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000cdffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: f0200000-f03fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: f0400000-f04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0500000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0500800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0500c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Dell Device 0271
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0501000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852
    Kernel modules: r852

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0271
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at ae000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ac000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0271
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at aa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at cc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 5000 [size=128]
    [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb
```
regards

---

### Post by Morozov on 2012-02-19
sorry about that, this one above with( CRT second monitor in X server) disabled

---

### Post by pqwoerituytrueiwoq on 2012-02-19
i just reread your 1st post
so you got output on the screen it just un-useable eg can't type, menus acting oddly
if so turn compiz off
[FONT=Courier New]metacity --replace &[/FONT]

---

### Post by Morozov on 2012-02-19
Ok gents I fix the HDMI video output, it was cable socket on the laptop (it didn't like my cable for some reason any more (they were friends up to point I went from Win7 to Ubuntu). I've got video on twin view and sound through HDMI, I've mad some print screens if someone interested.
There is still long way to go by smoothing things up like separate screen on VGA cable (I'm getting wallpaper and mouse. I can't open any window or drag from one screen to another. I didn't try it on HDMI output (I'll update you later. 
Second would be a bug which at this time &#733;kills&#733; XServer when computer going to sleep mode, when I try to wake komp. up first thing I only see mouse on the black screen then all mouse dissapear and I can't get nothing (not even console). Only hard reset at this time clears this fault
Well one more thing to tune; I guess this would be resolution difference when switching on twin view causing laptop screen switch to 2D.
Regards

---

### Post by Morozov on 2012-02-19
Ok, Here is another question what to do with separate X screen how to start and work on two windows? Same story as with VGA cable connected from the moment it boots up second monitor is blank white. All colours and resolution on on laptop are normal. When mouse moved over to a second screen with left mouse click it's possible to get wallpaper then nothing (right click or left or any key stroke combination)
I'll try to play with Compriz and update you on changes.
Regards

---

### Post by Morozov on 2012-02-20
Separate screen still not working.... screens Freze up crashing desktop. Twin srceen is also tricky if screens have different resolution. I'd say the problem solved for now (I got HDMI working) but there is still long way to go with Nvidia driver (houpfully it will be handled better with 12.04LTS
Regards

---

