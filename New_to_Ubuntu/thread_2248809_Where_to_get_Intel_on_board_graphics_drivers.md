---
title: "Where to get Intel on board graphics drivers?"
date: 2014-10-17
forum: New to Ubuntu
---

### Post by adj3 on 2014-10-17
Hello people,

Excuse my "noobness". I attempted to play Left 4 dead on Ubuntu using Valve's Steam and I couldn't play the game    	 	 	 	   because the video was lagging so much. I went to Intel's website to find drivers for my processor but couldn't find any for Ubuntu Linux. Any suggestions?

 
Thanks

---

### Post by d4m1r on 2014-10-17
What version of Ubuntu are you running and what specific model of Intel graphics?

If you are running Ubuntu 14.04, check out;

[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

---

### Post by papibe on 2014-10-17
Hi adj3.

Intel graphic drivers are shipped with Ubuntu. They are open source so they are included in all distributions.

I would not recommend downloading a driver from the Intel site. There are a couple of ppas that would upgrade your driver for an upstream version, but pre package for Ubuntu.

Could you open a terminal, run this command, and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by adj3 on 2014-10-17
My CPU is --------> Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz and I'm running Ubuntu 14.04

---

### Post by adj3 on 2014-10-17
The results were this. Can you please explain the commands you wrote earlier?


00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84ca]
    Kernel driver in use: i915

---

### Post by Frogs Hair on 2014-10-17
You can learn more about lspci with the following command though I can't give the specifics of the command pabibe posted.

```
man lspci
```

---

### Post by papibe on 2014-10-17
The command lists the hardware connected to the PCI bus, and the driver they use.

It looks like you're using the proper driver (i915).

IMHO, without disrespect, your machine is not exactly a 'gaming' machine. I'd recommend tunning down the graphics on the games themselves so you have a better experience.

If you feel like a upstream driver could make a difference, you may try to upgrade your driver this way: download a tool called 'Intel Graphics Installer 1.0.6 for Linux' from [here]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux"). Chose the proper Ubuntu package and follow the instruction.

This is not a driver, but a tool that would check your system and will offer and install the latest compatible driver for your system.

Let us know how that goes, and if it improves performance.
Regards.

---

### Post by Vladlenin5000 on 2014-10-17
The recommend graphics for Left4Dead 2 are Nvidia GT230 / ATI Radeon X800 XT therefore it should also run acceptably in a new powerful Intel HD. Anything below that will give poor results.
The drivers you already have are good. Newer version from the PPA or provided by the Intel installer won't give you better performance than what you already have.

---

### Post by adj3 on 2014-10-20
> **papibe said:**
> The command lists the hardware connected to the PCI bus, and the driver they use.

It looks like you're using the proper driver (i915).

IMHO, without disrespect, your machine is not exactly a 'gaming' machine. I'd recommend tunning down the graphics on the games themselves so you have a better experience.

If you feel like a upstream driver could make a difference, you may try to upgrade your driver this way: download a tool called 'Intel Graphics Installer 1.0.6 for Linux' from [here]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux"). Chose the proper Ubuntu package and follow the instruction.

This is not a driver, but a tool that would check your system and will offer and install the latest compatible driver for your system.

Let us know how that goes, and if it improves performance.
Regards.

Hello papibe, 
I did download the deb file form Intel's website and installed it but it doesn't work... firstly when I search Intel Graphics on my computer the software icon comes up all weirdly, like so [ATTACH=CONFIG]257386[/ATTACH]
Anyways when I open the software I get the following errors [ATTACH=CONFIG]257387[/ATTACH][ATTACH=CONFIG]257388[/ATTACH]

Thanks for the help

---

### Post by MrSteve on 2014-10-20
before you try to install the intel graphics installer 
please open a terminal and use these, copy and paste then enter your password

wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | \
sudo apt-key add -

and then 

wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | \
sudo apt-key add -

then use the ubuntu software centre to install the intel graphics installer .deb file 
after this then run the intel installer and it will then update your intel GPU to the latest stack

direct link to the intel graphic installer page ...
[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux)

---

### Post by mastablasta on 2014-10-21
using something else than Unity would also help. the desktop itself is consuming the GPU power. if oyu switched to xfce or something lighter (maybe even just a Windows manager) there should be at least some improvement.

otherwise turning down the resolution in game and reducing special effects should also help. 

be also sure to check how much ram is assigned to the GPU (you can see that in BIOS) and if possible assign more RAM to it.

---

### Post by MartyBuntu on 2014-10-21
You're asking a lot from drivers that won't help an under-powered machine...even if id does technically meet the minimum system requirements.

---

### Post by Vladlenin5000 on 2014-10-21
> **MartyBuntu said:**
> You're asking a lot from drivers that won't help an under-powered machine...even if id does technically meet the minimum system requirements.

+1

---

### Post by adj3 on 2014-10-24
Thank you all for your response. I am fully aware that my machine is  underpowered but my concern was why the particular game I named at the  beginning of this thread runs flawlessly when I had windows on the same  computer but runs awfully when I migrated to Ubuntu. Considering the  circumstance I naturally thought it was an Intel graphic driver issue.

---

### Post by pissedoffdude on 2014-10-24
> **adj3 said:**
> Thank you all for your response. I am fully aware that my machine is  underpowered but my concern was why the particular game I named at the  beginning of this thread runs flawlessly when I had windows on the same  computer but runs awfully when I migrated to Ubuntu. Considering the  circumstance I naturally thought it was an Intel graphic driver issue.

While Intel's drivers for Linux have basically  always been on par (and maybe even superior in some cases) to their Windows drivers, you're probably not gonna get the same performance you get on Windows due to the use of OpenGL.  Even on Windows, OpenGL performance has always been  somewhat flaky with Intel video drivers.  It's most likely the case that the Windows version uses d3d, whereas the linux version uses OpenGL.  See if there's an OpenGL option (not all games have this) for the Windows version and test the frames per second against the Linux version

---

