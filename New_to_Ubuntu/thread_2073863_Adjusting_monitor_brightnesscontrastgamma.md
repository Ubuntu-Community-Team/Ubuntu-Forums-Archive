---
title: "Adjusting monitor brightness/contrast/gamma"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by Kaarna on 2012-10-20
[COLOR="Silver"]I've run out of ideas after struggling for hours with this incredibly frustrating issue. You are my only hope left.

I've been desperately trying to manually calibrate my monitor. My monitor itself is an old, really low-tier piece of LCD junk and one cannot even properly adjust its brightness or contrast by hand, so my only option left is to alter these values using an application.

This was not a problem when I was using Windows, since I could adjust them through my GPU drivers (AMD Catalyst). I tried to install these drivers for my Lubuntu as well, but either I messed something up or my card (ATI Radeon HD 4870) isn't supported.
..or perhaps 12.10 isn't supported, I can't really tell.

So, I've been searching the internet for a solution only to find applications that don't work, are way too confusing for a beginner like me or require a "calibrator" to work. It annoys me to no end that it seems like there is no simple application to just allow the user to alter the monitor's brightness, contrast and gamma.

I bet there is some really simple answer that I just haven't thought about.
Any help would be greatly appreciated.[/COLOR]


**EDIT:** I managed to figure it out on my own.
I made a script that modifies the contrast using xcalib on startup.

If anyone else is having similar problems, I made an .sh-file with:

[I]#!/bin/bash 
bash -c 'sleep 5 && xcalib -contrast 88 -alter'
exit 0[/I]

Then I added the path to that .sh-file in /etc/xdg/lxsession/Lubuntu/autostart

Just change the xcalib command to suit your particular needs.
I'm sure there are simpler ways to do this, but this works at least.

---

