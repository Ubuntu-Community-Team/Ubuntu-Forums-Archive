---
title: "Ati &amp; Nvidia graphic cards for each monitor"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by pinochan on 2013-01-26
Hello all.

It's one week since I have been trying to configure my dual screen desktop. I followed thousands of guides but with no luck.

I have two graphic cards:
(lspci result)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [ATI Radeon HD 6800 Series]
02:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7900 GS] (rev a1)

And two screens. AMD is giving signal to the first screen, and the desktop is shown correctly.
NVidia is supposed to give signal to the secondary screen, but I'm only able to see "Ubunto" logo, and all consoles (Crtl+alt+{F1-F6}). 

It is a clear installation of ubuntu on a new SSD.

This is my xorg.conf

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "Screen0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Unknown"
    ModelName    "Unknown"
    HorizSync    28.0 - 33.0
    VertRefresh  43.0 - 72.0
    Option        "DPMS"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "SwapScreens" "off"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"
    BusID       "PCI:2:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

These parameters are taken by unplugging the graphical cards and configuring each card separately. Once for ADM and another for Nvidia.
Afterwards I used aticonfig tool:
aticonfig --initial=dual-head --screen-layout=left
and with the result xorg.conf modified the parameters to mach my hardware.

I tried with xinerama on and off, but nothing happens.
I don’t have any active additional device.
If I enter catalyst control center, It doesnt detect secondary screen(nvidia)
(With Windows, catalyst control center, detects both screens)
It seems I cant have nvidia driver and Amd simultaneously.

Do you know if it is possible to set up both screens using different graphic cards? What am i doing rong?

Thank you!

---

### Post by cariboo on 2013-01-27
Why can't you connect both monitors to the much newer ATI/AMD graphics card? What type of connectors does the adapter have?

---

### Post by pinochan on 2013-01-27
Hi.

The Ati has 2 connectors:

[LIST]
[*]DVI-D single link
[*]DVD-I dual link
[/LIST]
I would like to use both cards because I dont want to penalize Ati with another screen as i want all its capacity to the main screen.

I hope there is some kind of walkarround or solution :)

Thank you!

---

### Post by Alcidious on 2013-01-30
Yeah, I'm having a similar issue; I've been looking at threads trying to figure out what to do.  I have a 12.10 Ubuntu install on a desktop, and I've got two ARM Radeon 5200? ATI cards. 

I don't want to use just one card for both monitors, either. When I've tried that, the computer just can't handle it. It's just slow as can be. 

Also, my nice, big, HP flatscreen monitor has a higher resolution and superior quality, while the second screen is my last computers Dell Screen that's the traditional 12"x12" (square...?) shape. 

I think the problem is my kernel reads both cards, but for some reason only one card is connecting to a monitor. Any help or success helping the originator of this thread would by highly appreciated!


Here is my readout:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
        Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "0-DFP4"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
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
   1600x900       60.0*+
   1280x1024      60.0  
   1440x900       60.0  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)

---

### Post by pinochan on 2013-02-01
Hi Alcidious. 
 
I still havent achieved to use extended desktop. I think it is only a question of time that i go back to windows as nobody seems to know how to do it... 
 
As far as i read, and without any guarantee of success, I would try this: 
 

[LIST]
[*]delete xorg.conf
[*]make sure you dont have any privative controler installed
[*]go to software center and look for "amd" the first entrance should be ATI binary controller fot X.org (or something like that, I am translating)
[*]I think once installed you have to reboot...
[*]open a terminal and with admin priviledges run:
[/LIST]
sudo aticonfig --initial=dual-head --screen-layout=left
sudo aticonfig --xinerama=on


[LIST]
[*]- this will generate a new xorg.conf with the parameters of boths graphic cards and monitors.
[/LIST]

Hopefully will add some sections to your original xorg.conf. Because I think that you misses some information about one device and one screen.

I should be something like this (with the automatic config file, try to figure out a new config if it doesnt works) . In red my guess changes to your file.
 
Section "ServerLayout" 
Identifier "aticonfig Layout" 
Screen 0 "aticonfig-Screen[0]-0" 0 0 
[COLOR=DarkRed]Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"[/COLOR]
EndSection 
 
Section "Module" 
EndSection 
 
Section "Monitor" 
Identifier "aticonfig-Monitor[0]-0" 
Option     "VendorName" "ATI Proprietary Driver" 
Option     "ModelName" "Generic Autodetecting Monitor" 
Option     "DPMS" "true" 
Option     "PreferredMode" "1600x900" 
Option     "TargetRefresh" "60" 
Option     "Position" "0 0" 
Option     "Rotate" "normal" 
Option     "Disable" "false" 
EndSection 
 
Section "Monitor" 
Identifier "0-DFP4" 
Option     "VendorName" "ATI Proprietary Driver" 
Option     "ModelName" "Generic Autodetecting Monitor" 
Option     "DPMS" "true" 
EndSection 
 
Section "Device" 
Identifier "aticonfig-Device[0]-0" 
Driver "fglrx" 
Option     "Monitor-DFP4" "0-DFP4" 
BusID "PCI:2:0:0" 
EndSection 
 
[COLOR=DarkRed]Section "Device" 
Identifier "aticonfig-Device[0]-1" 
Driver "fglrx" 
Option     "Monitor-DFP4" "0-DFP4" 
BusID "******" <-- the result of lspci | grep VGA
EndSection [/COLOR]

Section "Screen" 
Identifier "aticonfig-Screen[0]-0" 
Device "aticonfig-Device[0]-0" 
DefaultDepth 24 
SubSection "Display" 
Viewport 0 0 
Depth 24 
EndSubSection 
EndSection

[COLOR=DarkRed]Section "Screen" 
Identifier "aticonfig-Screen[0]-1" 
Device "aticonfig-Device[0]-1" 
DefaultDepth 24 
SubSection "Display" 
Viewport 0 0 
Depth 24 
EndSubSection 
EndSection[/COLOR]


Once rebooted, the new config should be applied and running AMD catalyst control center application, you should be able to detect both screens.

Tell me if you had better luck than me!

-----------------------------------------------------------------------------------------------------------------------
My apologies if i had said some nonsense. Im not an expert at all, actually I am a completely begginer.

---

### Post by Alcidious on 2013-02-01
Pinochan,

Thank you! I will let you know how it works out later tonight when I have some time to work on my machine. I think I'll figure it out. 

I've found that getting help sometimes requires posting in several forums (i.e.-general help, hardware, screens) or even different linux forums altogether.  I think the Ubuntu Forums maybe aren't as active as they have been in the past, but you might be able to submit a troubleshooting request to the launchpad and/or canonical people, and get professional help.

Using linux is sometimes a pain in the butt, and often it will take significant time to fix or successfully troubleshoot a problem.  But in my opinion, it is always worth it! I have learned so much about computers b/c of linux, and you can always change things yourself once you become skilled. 

Things are sometimes easier in Windows, but your stuck with Windows. I don't like Microsoft, and I like the open-source concept, and that is why I use Ubuntu. But one day soon I might change to Slackware, or Arch-linux, or some other linux distro. I think it is definitely worthwhile to keep using it... because if you know linux really well, it is far superior to any other operating system b/c it will do EXACTLY what you tell it to do.

---

