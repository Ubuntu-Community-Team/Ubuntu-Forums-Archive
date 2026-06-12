---
title: "Dual Widescreen Display with different resolutions"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jcameron89 on 2008-08-03
I'm looking to install Ubuntu on my new desktop, which I have currently have a Samsung 216BW and a Samsung 940BW hooked up to. The native resolution on the 216BW is 1680x1050, and the 940BW is 1440x900. However, in the past I've had difficulty getting a single widescreen display to working properly in its native resolution with Ubuntu. If anyone can help me, what packages will I need to acquire with the Synaptic Package Manager? What changes would I need to make to my xorg.conf file? What hardware drivers would I need to install?

Here is my hardware:
SR5250NX(GN582AA)
Intel Pentium dual-core E2140(1.6GHz)
64 bit Dual Core Processor
1MB L2 Cache (Per Processor)
1GB DDR2 667 RAM
Hard Drive : 320GB SATA 7200RPM
SuperMulti DVD Burner with LightScribe Technology
Graphics : Integrated Intel GMA 950, BFG Tech GeForce 8600 GTS
Realtek AC '97 Audio
Integrated 10/100BaseT network interface

Thanks in advance for anyone who is able to help me out, with a solution or even just any advice at all.

---

### Post by ajmorris on 2008-08-03
> **jcameron89 said:**
> I'm looking to install Ubuntu on my new desktop, which I have currently have a Samsung 216BW and a Samsung 940BW hooked up to. The native resolution on the 216BW is 1680x1050, and the 940BW is 1440x900. However, in the past I've had difficulty getting a single widescreen display to working properly in its native resolution with Ubuntu. If anyone can help me, what packages will I need to acquire with the Synaptic Package Manager? What changes would I need to make to my xorg.conf file? What hardware drivers would I need to install?

Here is my hardware:
SR5250NX(GN582AA)
Intel Pentium dual-core E2140(1.6GHz)
64 bit Dual Core Processor
1MB L2 Cache (Per Processor)
1GB DDR2 667 RAM
Hard Drive : 320GB SATA 7200RPM
SuperMulti DVD Burner with LightScribe Technology
Graphics : Integrated Intel GMA 950, BFG Tech GeForce 8600 GTS
Realtek AC '97 Audio
Integrated 10/100BaseT network interface

Thanks in advance for anyone who is able to help me out, with a solution or even just any advice at all.

hi there,

As long as you are using a driver for your graphics card that can support the resolution. A single widescreen monitor should be able to display the correct resolution, as long as you have the mode specified in the corresponding depth mode in your /etc/X11/xorg.conf If after starting X with the single monitor, and you cannot get the resolution, you can try running displayconfig-gtk or xrandr -s <width>x<height>

AJ

---

### Post by MrHippocampus on 2008-08-03
If both of the monitors are plugged into the NVIDIA card then you should just have to install the nvidia-glx-new package to get the NVIDIA driver and then nvidia-settings to get the NVIDIA application which you can set up your dual screens with. Anything to do with dual screens and xrandr wont work with an NVIDIA card as the drivers have their own way of doing dual screens which is done through nvidia-settings.

---

### Post by jcameron89 on 2008-08-03
Ah, so as long as I install the appropriate nVidia package after gaining internet access, I'll be fine? That's good news. Thanks a lot for your help.

EDIT : So I don't clog up the forum with new threads, I have another question I'll put in here.

Will I have trouble finding the drivers for my chipset, LAN, and audio hardware as things currently stand in Ubuntu? I recall having a bit of trouble the last time I went through this process.

---

### Post by MrHippocampus on 2008-08-03
Normally its no trouble at all, for most things other than graphics cards the correct drivers are already being used. Basically if everything works with the livecd then you shouldn't have any driver problems.

---

### Post by jcameron89 on 2008-08-04
Whenever I go through Synaptic Package Manager to install "nvidia-settings" it prompts me that by installing this, I will have to remove "nvidia-glx-new". Is that ok? Sorry for the questions, I'm just a bit new to using nVidia hardware with Linux.

---

### Post by MrHippocampus on 2008-08-04
In that case nvidia-settings may already be installed (as part of nvidia-glx-new), it should be in the preferences/administration menus, if not open a terminal (Somewhere in the applications menu, can't for the life of me remember where) and type in "nvidia-settings" (without the quotes) and hit return.

---

