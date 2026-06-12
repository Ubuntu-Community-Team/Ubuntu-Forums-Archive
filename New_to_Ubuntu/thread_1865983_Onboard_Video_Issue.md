---
title: "Onboard Video Issue"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by djevans3 on 2011-10-20
I'm new to Ubuntu (and Linus overall) but proficient in Windows.  Don't know a terminal from a command prompt, haha.  I believe I'm not getting the best graphics possible since I can't get the virtual desktops to scroll, a little box comes up in the center  of the screen with the desktops.  I have an onboard Intel video and Ubuntu 11.10 installed the i915 driver which is appropriate, but it appears there is another component which is unclaimed and could be preventing my graphics from being acceptable.  Under the System Info it say the video driver is "unknown".

 *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff

Any ideas and tips on how to correct is beneficial, thanks.

---

### Post by djevans3 on 2011-10-21
After scouring the net I found out part of my issue is that my card will only support Unity 2D because it can only support OpenGL to 1.3.  If I want to experience 3D I'll need to find a PCI video card on the cheap which can render preferable 2.0 or better....damn Dell for not using AGP!

---

