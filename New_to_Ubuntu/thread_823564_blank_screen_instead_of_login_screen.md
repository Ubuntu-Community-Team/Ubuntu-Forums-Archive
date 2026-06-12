---
title: "blank screen instead of login screen"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ronka on 2008-06-09
I've a problem during the boot in Hardy 8.04. Almost every time (but not always!) when I boot I get a blank screen instead of the login-screen and the PC is completely blocked. The only option I have is to switch off the pc. Doing this for 3 or 4 times Ubuntu will eventually show the login-screen. After the login everything works fine.
Ron

---

### Post by ukripper on 2008-06-09
What graphics card are you using and which drivers? Are they  restricted drivers or you have installed yourself?

---

### Post by ronka on 2008-06-09
display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 0136
	Flags: bus master, fast devsel, latency 0
	Memory at 58400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

---

### Post by ukripper on 2008-06-09
try reconfiguring your xserver-xorg
here is the guide:
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by ronka on 2008-06-09
Thank you but reading the guide it says:
"This method does not work with Hardy Heron and probably all versions to follow (including Intrepid Ibex). This method seems to ONLY work with Gutsy Gibbon and older.
I think this is because the newer versions of xserver-xorg rely more on auto-detecting the configuration during runtime rather than looking at xorg.conf."
Should I try however?
Ron

---

