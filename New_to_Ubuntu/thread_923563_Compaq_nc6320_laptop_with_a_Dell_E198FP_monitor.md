---
title: "Compaq nc6320 laptop with a Dell E198FP monitor"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by dizz1s4u on 2008-09-18
Hello All,
I am new to Ubuntu and love it.  There are Windows users all around me with dual monitor support and when I was on windows, I had it.  Since the migration, however, I have only been able to run one monitor and really need the desktop space (and coolness) of two.  Any help for this specific combo would be great.  Also, I have looked at the threads for nvidia, etc, but that only caused problems on my machine and I had to restore the backed up file.

---

### Post by northern lights on 2008-09-18
Given the nature of your thread, I'm assuming your machine's got an nvidia card with two VGA/DVI outs.

If so, you should be able to enable TwinView either under "System > Administration > NVIDIA X Server Settings", or, should that not yet exist, by running ```
sudo apt-get update && sudo apt-get install nvidia-settings nvidia-xconfig
```(nvidia-xconfig being of secondary interest) and the subsequent execution of 'nvidia-settings'.

---

### Post by dizz1s4u on 2008-09-18
I do not know what my driver is.  I just mentioned nvidia because that was the only thing I could find in the forums.

---

### Post by northern lights on 2008-09-18
> **dizz1s4u said:**
> I do not know what my driver is.  I just mentioned nvidia because that was the only thing I could find in the forums.Fair enough. Ignore the above for a moment at least and instead post the output of ```
sudo lshw -C display
```
Thank you.

---

### Post by dizz1s4u on 2008-09-18
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

