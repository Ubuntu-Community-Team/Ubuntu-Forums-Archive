---
title: "Desktop effects can't enable"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by bokgeneraal on 2011-10-28
Just installed Ubuntu Oneiric. Then installed kubuntu-full. But then I released that the desktop effects could not be enabled. I noticed that the kubuntu-full installation installed nvidia drivers. I have a Intel graphics card. i ran the following command with the following output:
Command : sudo lshw -C video
Output: 
 *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f4000000-f43fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
 ...

---

### Post by bokgeneraal on 2011-11-01
Is there a way to reset the graphics to use the same settings as when the OS was installed. When I installed , all effects worked.

---

### Post by 2F4U on 2011-11-01
A default install of U/K/X/Lubuntu always contains drivers for several graphics cards, including nVidia, ATI, Intel, etc. However, its unlikely that the system uses nVidia drivers for an Intel card. The most likely reason that you can't enable all desktop effects is that your graphics card is not capable enough.

---

### Post by bokgeneraal on 2011-11-01
When I installed Oneiric all the effects where enabled and worked. Only after installing kubuntu-full did the effects get disabled.

---

### Post by bokgeneraal on 2011-11-04
Reinstalled Ubuntu. Instead of installing kubuntu-full I installed Kubuntu-desktop instead.
This solved the problem.

---

### Post by grahammechanical on 2011-11-04
I have never tried Kubuntu. I think that I should give it a try. I do know that unlike Ubuntu, which is based on the Gnome desktop environment, Kubuntu is based on the K desktop environment (KDE). I expect that there will be big differences in look and style between Ubuntu and Kubuntu. I expect that there will be different desktop effects available in Kubuntu to those in Ubuntu. I think that I shall try Kubuntu in its own partition. I did that with Edubuntu last year.

Regards.

---

