---
title: "How to check drivers/DMA/other in Ubuntu?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by discmaster on 2008-06-07
As with windows where you can check device manager & other areas for devices, drivers installed, chipset/mainboard info., & other stuff - How do I go about checking all that in Ubuntu? Are there programs to run? CLI commands?

Also, what about a pgm. to run that will measure the health/temperature of the pc in linux? Something like Hardware Monitor for windows?

Thanks! :popcorn:

---

### Post by Paqman on 2008-06-07
> **discmaster said:**
> As with windows where you can check device manager & other areas for devices, drivers installed, chipset/mainboard info., & other stuff - How do I go about checking all that in Ubuntu? Are there programs to run? CLI commands?

If you go to Preferences > Hardware Information you can see technical info about your hardware.
Drivers are handled by the package management system, so you can see them through Synaptic just like all your other software.

> 
Also, what about a pgm. to run that will measure the health/temperature of the pc in linux? Something like Hardware Monitor for windows?


Try installing [sensors-applet](apt:sensors-applet) then right click on a panel to add it.

---

### Post by autocrosser on 2008-06-07
There is a very good HowTo in Tutorials & Tips to configure Lm-Sensors--  [http://ubuntuforums.org/showthread.php?t=2780&highlight=sensor](http://ubuntuforums.org/showthread.php?t=2780&highlight=sensor)

I install a very old-school panel--Gkrellm. It's configureable, skinable & shows a wealth of info in a small space.  You can also look into Conky..there is info in the tutorials area about it also.

For hardware, you can also install Sysinfo--available in Synaptic.

---

### Post by kogos on 2008-11-11
> **Paqman said:**
> .....If you go to Preferences > Hardware Information you can see technical info about your hardware.....


Unfortunately, with Intrepid 8.10, hardware information is removed... any other idea to check dma without installing any new software? there must be a command or something to do that.

---

