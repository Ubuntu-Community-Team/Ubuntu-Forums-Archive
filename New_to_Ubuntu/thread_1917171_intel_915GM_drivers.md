---
title: "intel 915GM drivers"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by mikeharris7 on 2012-01-29
I'm having the same problem. I was trying to run Nexuiz (FPS game) and got very slow choppy video playback. I have a Compaq NC6320 with the 915gm chipset. I discovered that Ubuntu (11.10 I think) is using a generic driver. I'm trying to figure out how to install the right one now.

---

### Post by Mark Phelps on 2012-01-29
Intel hasn't updated their 915 driver in YEARS.  The driver currently installed is most likely the ONLY one that will work now.

---

### Post by mikeharris7 on 2012-01-29
I'll bet. I snagged a few old laptops we were throwing out at work. The 6320 is pretty long in the tooth but throw some extra RAM in them and they're a solid little unit. 

I don't think it's using a 915 driver at all. When I go to system info and click on graphics for driver it just says 'unknown'.

---

### Post by Mark Phelps on 2012-01-29
System info is notoriously unreliable -- says the same on my PC and I am using AMD drivers.

---

### Post by snowpine on 2012-01-29
I just don't think it's a gaming-class graphics card. 

xorg-video-intel is installed by default in all Ubuntu releases.

---

### Post by Kixtosh on 2012-01-29
I used a Toshiba Portégé R205 for a while, with the Mobile Intel 915GMS Express card. I didn't have any problems whatsoever, but it's an "ultra-portable", so you would expect it to have some performance limitations, but it was a whole lot snappier than with Win XP (especially for boot and shut down times). I thought it was a pretty solid machine with Lucid Lynx 10.04 LTS.

What are you worried about in particular?

---

### Post by mikewhatever on 2012-01-29
> **mikeharris7 said:**
> I'll bet. I snagged a few old laptops we were throwing out at work. The 6320 is pretty long in the tooth but throw some extra RAM in them and they're a solid little unit. 

I don't think it's using a 915 driver at all. When I go to system info and click on graphics for driver it just says 'unknown'.

You can find out which driver is in use by looking at the output of the following:
```
lspci -knn | grep VGA -A1
```

---

