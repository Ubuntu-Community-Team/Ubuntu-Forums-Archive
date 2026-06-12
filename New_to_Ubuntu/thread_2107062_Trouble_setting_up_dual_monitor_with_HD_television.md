---
title: "Trouble setting up dual monitor with HD television"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by jcobban on 2013-01-20
My computer has an HDMI output, so I want to use my HD TV as a second monitor.  This works but I cannot exploit the full 1080x1920 resolution because the maximum virtual screen size is 1600x1600.  The main display on my laptop is 768x1366, so I can just squeeze in the TV as a second monitor if I use it at the same resolution, but I would really like to have both displays at full resolution, which would require a maximum virtual screen size of 1920 horizontal by 1848 vertical.  I have read through the xorg configuration documentation but I am baffled as to what I actually have to do.  I cannot see anywhere in the existing configuration files where the current maximum screen size is set.

---

### Post by audiomick on 2013-01-21
Post the output of 
```
sudo lshw -c video
```
so people can see what graphics card you are dealing with.

Have you installed proprietary video drivers?

---

### Post by jcobban on 2013-01-25
> **audiomick said:**
> Post the output of 
```
sudo lshw -c video
```
so people can see what graphics card you are dealing with.

Have you installed proprietary video drivers?

$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: BeaverCreek [Mobility Radeon HD 6620G]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:54 memory:b0000000-bfffffff ioport:f000(size=256) memory:ff700000-ff73ffff

As you can see I have installed the proprietary fglrx driver.

---

### Post by jcobban on 2013-01-28
I have verified that the graphics hardware on my laptop is capable of driving the HDMI-attached television at full 1080p resolution with an extended virtual screen that includes the laptop display by booting into Windows.

When I have the TV plugged in xrandr displays:
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1536, maximum 1600 x 1600
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +   40.1  
   1360x768       60.0     40.1  
   1280x768       60.0*    40.1  
   1280x720       60.0     40.1  
   1024x768       60.0     40.1  
   1024x600       60.0     40.1  
   800x600        60.0     40.1  
   800x480        60.0     40.1  
   640x480        60.0     40.1  
DFP1 connected 1280x768+0+768 (normal left inverted right x axis y axis) 890mm x 500mm
   1400x1050      60.0     30.0     24.0  
   1600x900       60.0     30.0     24.0  
   1280x1024      60.0     30.0     24.0  
   1440x900       59.9     30.0     24.0  
   1280x960       60.0     30.0     24.0  
   1280x800       74.9     59.8     30.0     24.0  
   1280x768       59.9*    30.0     24.0  
   1280x720       60.0     59.9     30.0     24.0  
   1024x768       30.0     24.0     60.0  
   1152x648       59.9  
   1024x600       30.0     24.0     60.0  
   800x600        30.0     24.0     60.3     56.2  
   800x480        30.0     24.0     60.3     56.2  
   720x480        30.0     24.0     30.0     60.0     30.0     59.9  
   640x480        30.0     24.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)

Note that 1080x1920 resolution is not listed as a choice.  Possibly this is because just by itself that would exceed the maximum 1600x1600 virtual window.

I just want to know where the 1600x1600 maximum resolution of the virtual screen comes from so I can override it.  I do not understand the wiki on supporting multiple screens.

---

### Post by jcobban on 2013-01-28
I removed the proprietary fglrx driver and the maximum virtual screen size changed to 8192x8192 and my TV now comes up by default in 1920x1080 resolution.  I got a bunch of missing AMD microcode messages during boot, and I had to power my laptop off and back on.  And the reason I had switched to the fglrx driver is back:  Ubuntu does not suspend when I close the laptop!  lspci returns:

 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G]

This is a relatively new level, the computer is less than a year old, although, of course, it is already obsolete.

---

