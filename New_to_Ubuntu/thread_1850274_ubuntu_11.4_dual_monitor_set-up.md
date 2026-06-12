---
title: "ubuntu 11.4 dual monitor set-up"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by mars-o on 2011-09-26
Hi,

i just installed ubuntu 11.4 today, and i have problems with my dual monitor. i have nvidia geforce video card too.

my 2nd monitor is not detected, and my 1st one is unknown.
[IMG]http://www.freeimagehosting.net/5a306[/IMG][http://www.freeimagehosting.net/5a306](http://www.freeimagehosting.net/5a306)
[IMG]http://www.freeimagehosting.net/940b7[/IMG]
and my driver is activated but not used.
[IMG]http://www.freeimagehosting.net/5a306[/IMG][http://www.freeimagehosting.net/940b7](http://www.freeimagehosting.net/940b7)

i run these commands in terminal,ithink this info is needed to solve this?

```

mars@mars-playground:~$ lspci | grep nVidia  00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
mars@mars-playground:~$ sudo lshw -C display[sudo] password for mars: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fb000000-fb07ffff
mars@mars-playground:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1360x768       51.0     52.0  
   1024x768       53.0     54.0     55.0  
   960x600        56.0  
   960x540        57.0  
   840x525        58.0     59.0     60.0     61.0  
   832x624        62.0  
   800x600        63.0     64.0     65.0     66.0  
   720x450        67.0  
   700x525        68.0     69.0  
   680x384        70.0     71.0  
   640x480        72.0     73.0     74.0     75.0     76.0  
   512x384        77.0     78.0  
   400x300        79.0  
   320x240        80.0     81.0  

```your help is much appreciated.

thank you so much.

---

### Post by HolyDonut on 2011-09-26
I haven't figured out how to get cloned screens or extended desktop to work but I have figured out how to at least use my external monitor as the only monitor. 

(I also haven't figured out how to close the lid of my laptop without shutting off both my laptop and external screens. )

Hopefully you're using the NVIDIA proprietary drivers, if so:

Don't use the Monitors application. Use the NVIDIA X Server Settings application.

Once you're in the NVIDIA X Server Settings, go to X Server Display Configuration.

Then press the Detect Displays button. Select your external monitor (will show as Disabled) You want to then press the Configure button and choose the TwinView option. 

Then select your laptop monitor (mine was called AU0). Then press the Configure button and choose disable. 

Then click the Apply button. 
[B][I]
You might have problems when you first try this. I had to manually set my external monitor's resolution to 1920x1080 (it can't support 1920x1200 but this stupid NVIDIA app tried to do that anyway) and the refresh rate to 60Hz (auto doesn't work for me). [/I][/B]

But this should be all you need for using your external monitor. :!:DON'T PULL THE MONITOR CABLE FROM YOUR LAPTOP WITHOUT REPEATING THIS PROCESS TO RE-ENABLE YOUR LAPTOP MONITOR. DON'T SAVE THE SETTINGS TO THE X CONFIGURATION FILE:!: At least that didn't work well for me (it gave me a blank black screen and I only fixed it by doing a lot of Google searches and I can't remember what I did).

Hopefully this helps.

---

### Post by mars-o on 2011-09-26
Thank you so much @holydonut! :) my 2nd monitor is now ok as extended desktop.:)

btw, after applying the settings, i click 'save to X configuration file. Is that correct?

---

