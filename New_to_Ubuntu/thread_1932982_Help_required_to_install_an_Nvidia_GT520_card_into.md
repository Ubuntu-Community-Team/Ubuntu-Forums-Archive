---
title: "Help required to install an Nvidia GT520 card into 11.10"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by Dave Daytona on 2012-02-28
Hi, I'm a total newbie with Ubuntu, installed Windows and built PCs  numerous times over the years, but this O/S is utterly new to me. 

I am trying to install Ubuntu 11.10 64-bit with a Nvidia/Asus GT520 graphics card. I can get as far as 11.10 & the Proprietary drivers installed but I can only see the flatscreen on the DVI cable, the Plasma screen on the VGA cable remains off. In the System Tools folder the icon about Displays is only showing the Dell screen as connected, if I click 'detect displays' the VGA is not detected. 
If I swap the hard drive with one containing Win XP O/S the screens are fine, so I assume the hardware is OK. Ultimately what I want is to use the extended desktop/workspace across the 2 screens as I can do in XP. Could someone help correct this problem. 
Please do it step by step, this is a new O/S to me and it's a bit bewildering. :oops:


Copied from Belarc Advisor:
*MotherBoard: Gigabyte GA-A75M-D2H*[I] - Bus Clock: 100 megahertz
3.00 gigahertz AMD A8-3870 APU with Radeon HD Graphics
256 kilobyte primary memory cache
1024 kilobyte tertiary memory cache
64-bit ready
Multi-core (4 total)
[/I]Nvidia/Asus GT520 graphics card with Plasma screen on VGA cable and Dell flatscreen on DVI cable.

---

### Post by cariboo on 2012-03-01
If you are using Unity, upen the Dash (click the bfb) and type:

```
nv
```

and press return. If you are running something else, open a terminal and type:

```
nvidia-settings
```

this will bring up the Nvidia Xserver Settings applet, and allow you to setup your two monitors.

---

### Post by Dave Daytona on 2012-03-04
Thank you, now working.:D

---

