---
title: "Ubuntu 14.04 LTS won't boot properly"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by nathanbell770 on 2014-11-09
Hello, 

I'm new to the forums and new to Ubuntu and I've got some problems that I've searched for solutions to and I can't seem to fix them on my own.

The tldr version is that I had Ubuntu 14.04 LTS(amdx64) working perfectly alongside Windows 8.1 for a few weeks. Each OS had its own HDD so there were no Ubuntu partitions on the Windows HDD and vice versa. For reasons unknown to me they both stopped working properly. Ubuntu would freeze at the splash screen before I could login and Windows 8.1 wouldn't retain the display drivers I installed after reboot.

My system consists of:
Motherboard: ASrock FM2A88X-ITX+
CPU: AMD Kaveri A10-7850K
Video Card: MSI Radeon R7 250 2GB GD3
Ram: 16 GB AMD R9 DDR3-2400 (2x8GB)
HDD: 2x 1TB Seagate 7200 RPM Hybrid 3.5" Internal Drives
Monitors: Acer T232HLBMIDZ(HDMI) and Viewsonic VX2250(Dual Link DVI)


When I started having problems I decided to clone my Windows OS and use it on a different PC altogether. I thought this would allow GRUB to load Ubuntu without having to Dual-boot. I migrated everything over to the other pc, wiped the drives and started with a fresh install***. I still continued to have problems such as freezing at the splash, or, if I got past the splash the GUI was pixelated and unusable because nothing could be deciphered. I also had dual monitor setup working well and now if I try to setup dual monitors in Catalyst one scales and works well and the other blacks out. Also, GRUB recognizes a Windows 7 boot manager, but I've never had Windows 7 installed on this PC at all.

***It should be noted that the only way I could get Ubuntu working was to use the mini.iso and install a barebones desktop, but once I installed programs like VLC, Firefox, Synaptic, after the reboot things started to go awry. 

I'm mostly frustrated and confused because when I installed Ubuntu the first time using WUBI for 14.04 it guided me through the install process and partitioned everything and there were no problems. Now, Ubuntu is the only OS on this PC and I can't get it to work properly. 

I don't know what log files are needed, but, if anyone can help me I'll get them and post them here. 

I really like Ubuntu's functionality, but, I just don't understand how to get back to where I was when I was dual booting.

---

### Post by whitesmith on 2014-11-09
> **nathanbell770 said:**
> I'm mostly frustrated and confused because when I installed Ubuntu the first time using WUBI for 14.04 it guided me through the install process and partitioned everything and there were no problems. Now, Ubuntu is the only OS on this PC and I can't get it to work properly.

Your problem may derive from WUBI support having was dropped. Win 8 is not compatible with WUBI, although I'm not sure why Ubuntu x.x would not work in a dual-boot (**not** side-by side; this is WUBI) configuration. Perhaps one of out hardware gurus can answer that for you.

---

### Post by grahammechanical on 2014-11-09
> [COLOR=#000000]CPU: AMD Kaveri A10-7850K + [/COLOR][COLOR=#000000]Video Card: MSI Radeon R7 250 2GB GD3[/COLOR]

That,  in my opinion, is the source of the problem. It is Hybrid graphics

> [COLOR=#000000][FONT=Calibri]We changed the game for PCs by revolutionizing the accelerated desktop processor that combines the power of a multicore CPU with AMD Radeon&#8482; graphics all in one energy-efficient chip.[/FONT][/COLOR]

[http://www.amd.com/en-us/products/processors/desktop/a-series-apu](http://www.amd.com/en-us/products/processors/desktop/a-series-apu)

+ the Radeon R7

This is the best that I can offer:

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards

---

### Post by nathanbell770 on 2014-11-09
> 
[LIST]
[*]**AMD systems:**

[LIST]
[*]Make sure that no other fglrx driver is installed. 
[*]Install fglrx. 

[*]Reboot the system (restarting X won't be enough). 
[*]NOTE: you can easily switch between GPUs using AMD's control panel.
[/LIST]
[/LIST]


This is what the wiki recommends, so, this may seem like a stupid question, but, how do I ensure that I ONLY have fglrx installed and no other display drivers? I've only been using Linux for about two weeks and I don't exactly know how to find this sort of thing in Terminal.

Thanks

---

