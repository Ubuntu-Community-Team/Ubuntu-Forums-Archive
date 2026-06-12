---
title: "[SOLVED] flickering graphics"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2008-10-18
The laptop I'm using (a Lenovo Z61m) tends to flicker whenever I use something even slightly graphic intensive. (such a SupertuxKart) It does use an ATI graphics card, would that have something to do with it?

---

### Post by philinux on 2008-10-18
Have a look in

System>Admin>Hardware Drivers.

See if a driver is offered for you to activate.

---

### Post by fikelfikel on 2008-10-18
Get the ATI Catalyst Control Center from Add/Remove. It solved my ATI problem, and can enhance the experience.

---

### Post by LunaticHiatus on 2008-10-18
It says "ATI accelerated graphics driver" is enabled and in use.

---

### Post by philinux on 2008-10-18
What are your system specs?

---

### Post by LunaticHiatus on 2008-10-18
Specs:

Processor Manufacturer  	Intel
Processor Type  	Core Duo
Processor Model  	T2400
Processor Speed  	1.83GHz
Processor Technology  	Enhanced SpeedStep Technology
 	Virtualization Technology
Bus Speed  	667MHz
L2 Cache  	2MB
Memory
Standard Memory  	1GB
Maximum Memory  	3GB
Memory Technology  	DDR2 SDRAM
Memory Standard  	DDR2-667/PC2-5300
Error Checking  	Non-parity
Number of Total Memory Slots  	2
Memory Card Support  	xD-Picture Card
 	Memory Stick
 	Secure Digital (SD) Card
 	MultiMediaCard (MMC)
Storage
Hard Drive Capacity  	120GB
Hard Drive RPM  	5400
Optical Drive Type  	DVD-Writer
Optical Media Support  	DVD-RAM/-R/-RW
Display & Graphics
Screen Size  	15.4"
Graphic Mode  	WXGA
Display Screen Type  	Active Matrix TFT Color LCD
Widescreen  	Yes
Display Resolution  	1280 x 800
Color Support  	16.7 Million Colors
Graphics Controller Manufacturer  	ATi
Graphics Controller Model  	Mobility Radeon X1300
Graphics Memory Capacity  	64MB

---

### Post by LunaticHiatus on 2008-10-18
bump....

---

### Post by stephanvaningen on 2008-10-18
Run:
```
/usr/bin/amdcccle
```
In preferences, set 'wait for vertical refresh' to 'Always on': what does that give you? ...

---

### Post by LunaticHiatus on 2008-10-18
/usr/bin/amdcccle

Takes me to the ATI catalyst control center and doesn't provide me with that option

---

### Post by eternalnewbee on 2008-10-18
> **LunaticHiatus said:**
> /usr/bin/amdcccle

Takes me to the ATI catalyst control center and doesn't provide me with that option

No solution from here, but just a note.
I recently bought an ATI graphic card and it was a disaster. Luckily they let me change it for an Nvidia card at the shop where I bought it. Then I did some digging in the forums and found out that ATI is not very Linux friendly. There are some workarounds, but not with all of them...
Good luck.

---

### Post by LunaticHiatus on 2008-10-18
Yeah, I knew ATI cards can be a bitch. I had a similar problem on my older micron but it was an older laptop anyway so I didn't think much of it

---

### Post by stephanvaningen on 2008-10-18
> **LunaticHiatus said:**
> /usr/bin/amdcccle

Takes me to the ATI catalyst control center and doesn't provide me with that option

Oh I'm sorry: It's in 3D -> More Settings

---

### Post by LunaticHiatus on 2008-10-18
ahh, Found it! still flickery though

---

### Post by stephanvaningen on 2008-10-18
And have you played around with any other settings of this program yet? (Make note of default settings so you cango back).

Is compiz enabled (What's the status in System -> Preferences -> Appearance)?

---

### Post by LunaticHiatus on 2008-10-18
compiz fusion is enabled and running fine.

havn't fiddled with the setting yet, mainly because I wouldn't know what to fiddle with

---

### Post by stephanvaningen on 2008-10-18
Just a thought, but I was wondering if there could be interference: I'ld think about trying to set Visual Effects to None and see where we stand then (just to continue diagnosing)...

---

### Post by LunaticHiatus on 2008-10-18
DAMN YOU ATI!!!!

there was interference with compiz fusion. If I set graphics to none it works fine.

---

### Post by fikelfikel on 2008-10-19
A good ATI graphics choice, I think is the Xpress 200. It works when just fine on any linux distro, in other words Linux-friendly.

---

### Post by stephanvaningen on 2008-10-19
> **LunaticHiatus said:**
> DAMN YOU ATI!!!!

there was interference with compiz fusion. If I set graphics to none it works fine.

In this case, I this morning found this on compiz-fusion forum:
--
Can you try this, and compiz should work while still having non-flickering video:
 ```
sudo gedit /etc/X11/xorg.conf
```
In the "Device" section, add:
 ```
Option   "TexturedVideo"   "Off"
```
(source: [http://forum.compiz-fusion.org/showpost.php?p=45637&postcount=5](http://forum.compiz-fusion.org/showpost.php?p=45637&postcount=5))

Remark: On my machine this change [caused this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/281433"), but that's another thing...

---

