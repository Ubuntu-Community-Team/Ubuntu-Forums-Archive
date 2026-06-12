---
title: "Enabling OpenGL?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Anonono on 2008-09-30
I tried to enable the 3D Mode in 'Chess', but it came up with this error:
> You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Please contact your system administrator to resolve these problems, until then you will be able to play chess in 2D mode.
Is there a way to enable it, or something? And I don't care about plaing Chess in 3D, I just want to play 3D games (Like I can in XP).

---

### Post by JoshuaRL on 2008-09-30
Hello, and sorry you're having problems.  Could you list what your specs are?  Specifically, what is your video card and what driver are you using for it?

---

### Post by Anonono on 2008-10-01
It's integrated graphics, I'm not sure what type. Is there a way to view system information in ubuntu?

---

### Post by mcduck on 2008-10-01
You should try with some other 3D game.

The message you get with the Chess is not because you wouldn't have working 3D acceleration or OpenGL support, but simply because the libraries the Chess needs to run in 3D mode aren't installed by default (in other words, even with a fully working 3D acceleration the Chess wil still give you the same message).

---

### Post by Zill on 2008-10-01
> **Anonono said:**
> It's integrated graphics, I'm not sure what type. Is there a way to view system information in ubuntu?
```
sudo lshw -html > ~/Desktop/hardware.html
```
will create a file called hardware.html on your Desktop.  Click on this file to view it in your default web browser.

```
glxinfo
```
will show if GL Direct Rendering is enabled.

---

### Post by Anonono on 2008-10-01
Okay, so direct rendering isn't enabled. What part of the system info should I post?

---

### Post by Zill on 2008-10-02
> **Anonono said:**
> Okay, so direct rendering isn't enabled. What part of the system info should I post?
... all sections that mention graphics or display ;-)

eg. In my listing this is under the section "pci" and sub-section "display".

---

### Post by Anonono on 2008-10-02
I think I got it...

```
id:	
pci
description: 	Host bridge
product: 	661FX/M661FX/M661MX Host
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	11
width: 	32 bits
clock: 	33MHz
configuration:	
driver	=	agpgart-sis
latency	=	32
module	=	sis_agp
id:	
pci
description: 	PCI bridge
product: 	SiS AGP Port (virtual PCI-to-PCI bridge)
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pci normal_decode bus_master
id:	
display
description: 	VGA compatible controller
product: 	661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pm agp agp-3.0 vga_controller cap_list
configuration:	
latency	=	0
id:	
isa
description: 	ISA bridge
product: 	SiS964 [MuTIOL Media IO]
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	36
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master
configuration:	
latency	=	0
id:	
ide:0
description: 	IDE interface
product: 	5513 [IDE]
vendor: 	Silicon Integrated Systems [SiS]
physical id: 	
2.5
bus info: 	
pci@0000:00:02.5
logical name: 	
scsi0
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	ide pm bus_master cap_list emulated
configuration:	
driver	=	pata_sis
latency	=	128
module	=	pata_sis
```

---

### Post by Zill on 2008-10-02
Looks like you might be out of luck according to [this]("http://www.winischhofer.eu/linuxsispart1.shtml#12") link :-(
> Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.
I recommend you buy a cheap nvidia card, such as the GeForce FX5200, and you should then get good openGL direct rendering performance.  Just make sure you install the correct drivers after card installation ;-)

---

