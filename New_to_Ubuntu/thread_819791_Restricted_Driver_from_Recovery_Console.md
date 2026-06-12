---
title: "Restricted Driver from Recovery Console?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by bettyhills on 2008-06-05
Can anyone give me complete commands to issue at the cursor in the Recovery Console that will install the restricted Nvidia driver?

Using Ubuntu 7.10 that was working perfectly, I have been having trouble with my screen display since the June 3 Update Manager update.  Following forum advice, I uninstalled all generic kernel files via Synaptic.  On the reboot, I incorrectly selected "generic/default" video driver.  Now I can boot into Ubuntu but cannot get past the confetti on the screen to install the required restricted Nvidia driver.  I am caught in a loop.

From the Recovery Console, I also disabled the Nvidia drivers per advice in another section of the forum, to no avail...  Still have a screen full of confetti.

Normal boot into Linux, gives a scrambled screen.  However, it is possible for me to boot into Linux Recovery Mode.  

Can anyone give me complete commands to issue at the cursor in the Recovery Console that will install the restricted Nvidia driver and enable it?

---

### Post by mikewhatever on 2008-06-05
It would help to know what card model you have. There are 3 different nvidia drivers in the repositories, nvidia-glx, nvidia-glx-new and nvidia-glx-legacy. If you don't know your model, find out with <sudo lshw -C display>. Generally speaking, <sudo aptitude install nvidia-glx> should be it.

---

### Post by bettyhills on 2008-06-05
That command gives me 
*-display
VGA compatible controller
product: C51 [GeForce 6150 LE]
physical id: 5
bus info: pci@0000:00:05.0
version: a2
width: 64 bits
clock: 66mhz
capabiliies: pm msi vga bus_master cap_list
confirguation: latency=0

Can you tell me which driver to use?

Also, after I use <sudo aptitude install nvidia-correctdriver>, how do I safely exit Recovery Console saving the changes?  Right now (after the Update Manager update), NOTHING shuts down the machine from Ubuntu.  It just hangs.

AND... how do I **enable** this restricted driver in the Recovery Console (exact commands?)?

Thank you for your help.

---

### Post by mikewhatever on 2008-06-06
Use <aptitude install nvidia-glx> to install the driver. You don't need to save any changes, once everything is installed. That done, type nvidia-xconfig to update your xorg.conf configuration file. To reboot nicely type <reboot>. As a side note, there is no need for sudo in recovery mode.

---

