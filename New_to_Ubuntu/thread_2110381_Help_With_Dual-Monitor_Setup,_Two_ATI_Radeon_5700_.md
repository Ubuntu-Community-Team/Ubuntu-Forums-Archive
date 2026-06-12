---
title: "Help With Dual-Monitor Setup, Two ATI Radeon 5700 graphics cards"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by Alcidious on 2013-01-30
Hey Y'all,

Running Ubuntu 12.10 on Desktop. I have been researching editing the /etc/X11conf. file.  The computer will recognize the second monitor if I plug #2 into one card, along with already present #1 monitor; but the system slows to a crawl.  

(Also, I commented in to another post with similar issues (but he has two different drivers):[http://ubuntuforums.org/showthread.php?t=2109069](http://ubuntuforums.org/showthread.php?t=2109069)

Thanks for any help!

Here's some terminal output, and the contents of my X11config file:

Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
Option	 "PreferredMode" "1600x900"
Option	 "TargetRefresh" "60"
Option	 "Position" "0 0"
Option	 "Rotate" "normal"
Option	 "Disable" "false"
EndSection

Section "Monitor"
Identifier "0-DFP4"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option	 "Monitor-DFP4" "0-DFP4"
BusID "PCI:2:0:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection


And here is some more data from my terminal:
alcidious25@extremis:~$ sudo lshw -c video
*-display 
description: VGA compatible controller
product: Juniper [Radeon HD 5700 Series]
vendor: Advanced Micro Devices [AMD] nee ATI
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=fglrx_pci latency=0
resources: irq:50 memory:d0000000-dfffffff memory:c0300000-c031ffff ioport:3000(size=256) memory:c0340000-c035ffff
*-display
description: VGA compatible controller
product: Juniper [Radeon HD 5700 Series]
vendor: Advanced Micro Devices [AMD] nee ATI
physical id: 0
bus info: pci@0000:03:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=fglrx_pci latency=0
resources: irq:51 memory:e0000000-efffffff memory:c0200000-c021ffff ioport:2000(size=256) memory:c0240000-c025ffff
*alcidious25@extremis:~$ sudo lshw -c video
*-display 
*-display 
description: VGA compatible controller
product: Juniper [Radeon HD 5700 Series]
vendor: Advanced Micro Devices [AMD] nee ATI
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=fglrx_pci latency=0
resources: irq:50 memory:d0000000-dfffffff memory:c0300000-c031ffff ioport:3000(size=256) memory:c0340000-c035ffff
*-display
description: VGA compatible controller
product: Juniper [Radeon HD 5700 Series]
vendor: Advanced Micro Devices [AMD] nee ATI
physical id: 0
bus info: pci@0000:03:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=fglrx_pci latency=0
resources: irq:51 memory:e0000000-efffffff memory:c0200000-c021ffff ioport:2000(size=256) memory:c0240000-c025ffff
alcidious25@extremis:~$ *-display
*-display: command not found
alcidious25@extremis:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 250mm
1600x900 60.0*+
1280x1024 60.0 
1440x900 60.0 
1280x960 60.0 
1280x768 60.0 
1280x720 60.0 
1024x768 60.0 
800x600 60.3 
640x480 59.9 
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)

---

### Post by Alcidious on 2013-01-30
I forgot to mention, I want the other monitor to be hooked up through my second graphics card.  I'm pretty sure all i need to do is edit the etc/x11org.conf file so that it picks up my monitor, but I need some help navigating that particular nugget...

---

### Post by Mark Phelps on 2013-01-30
You shouldn't have to edit anything to detect the second monitor.

Once in the desktop, use the Dash to bring up the Display settings.  On that panel, it likely has Mirror checked.  Uncheck that and it should then show two monitors.

---

