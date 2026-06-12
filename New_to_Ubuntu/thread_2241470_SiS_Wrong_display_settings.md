---
title: "SiS: Wrong display settings"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by colin26 on 2014-08-26
Hi,

New to Linux and Ubuntu but thought I would play.

I have an old Novatech laptop into which I have uploaded Ubuntu 14.04.   On boot up the display is far too big for the screen at 640x480 and this is the only display shown in the Screen Display menu.   However, if I plug in an external monitor both the laptop screen and the external monitor boot up in 1280x768 mode.   If I remove the external monitor the laptop screen remains at 1280x768 and the Screen Display menu shows this as the only mode and as the built in display.

If I reboot the machine without the external monitor it reverts to 640x480 and displays the following message -

   Could not apply stored configuration for monitors
   None of the selected modes were compatible with the possible modes.
   Trying modes for CRTC380
   CRTC380:   trying mode 640x480 @ 73Hz with output at 1280x768 @ 76Hz [pass 1]
   CRTC380:   trying mode 640x480 @ 73Hz with output at 1280x768 @ 76Hz [pass 2]

lshw -c video produces the following -

* - display unclaimed
     description:   VGA compaticle controller
     product:     771/671 PCIE VGA Display Adapter
     vendor:      Silicon Integrated Systems [SiS]
     physical id: 0
     bus info:   pci@0000.01:00.0
     version:    10
     width:      32 bits
     clock:      66Hz
     capabilities: vga_controller compatible
     configuration:   latency=0
     reserves: memory: c0000000-cfffffff memory: b0000000-b001ffff io port: 9000 (size 128)

default xrandr -
     Failed to get size of gamma for output default
     Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
     default connected primary 640x480+0+0 0mm x 0mm
     640x480     73.0*

With external monitor connected -
     Failed to get size of gamma for output default
     Screen 0: minimum 1280 x 768, current 1280 x 768, maximum 1280 x 768
     default connected primary 1280x768+0+0 0mm x 0mm
     1280x 768     76.0*


Only 1 screen shows at any one time in Screen Display menu and this is as the built in display.

Anyone else had this problem or do I throw the laptop in the recycling bin?

---

### Post by mörgæs on 2014-08-27
Hi, welcome to the fora.

Does this help?
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by colin26 on 2014-08-27
Thanks, but in this case 14.04 is what I uploaded.   I will read that thread in detail though before going any further.

---

