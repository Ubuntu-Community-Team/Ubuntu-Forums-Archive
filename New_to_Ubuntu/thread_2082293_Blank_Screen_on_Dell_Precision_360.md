---
title: "Blank Screen on Dell Precision 360"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by bbithead on 2012-11-09
I have used RHEL for many years at work, so I want to install Ubuntu on a PC at home. I'm a noob at this.
 
Created disk image of Ubuntu 12.10, loaded it into the Dell Precision 360 (force a CD startup, BIOS battery is dead), reads disk fine, conencts to network, etc,. gets to the Ubuntu desktop where I am asked to "Try..." or "Install...". I Navigate around first, though some of the icons on top bar. Eventually I click the "Try..." button. It goes through some gyrations, then eventually ends up on a black screen. I tried clicking where icons at left on desktop might be, seems to start something. I can then mouve mouse which senses edges and corners. When playing around on this black screen, eventually get messages like this (some variations):
[ 575.572011] [drm] nouveau 0000:01:00.0: Failed to idle channel 1.
 
The eventually back to a Ubuntu desktop where it asks for Login credentials. 
 
All I want is to run Linux at home - any ideas? Any help is greatly appreciated!!
PC is Dell Precision 360 Intel Pentium 4 CPU, 1.5GB RAM, 2.6?GHz, 2 HDD partitions about 40GB each, nVIDIA QuadroFX 500. 
 
Thank you,
BBithead

---

### Post by bogan on 2012-11-09
Hi!. [B]bbithead,
[/B]
 At the 'black Screen', what do you get when pressing 'Ctrl+Alt+F1' [or F2-6]?

You should get a 'TTY'; a Text Terminal screen with a Log-in prompt. [ 'Ctrl+Alt+F7'  would return to the GUI screen, or hung text if there is no GUI.]

I think that is what you describe.

The Quadro FX 500 requires the nvidia 173.14.36 driver for full performance but should run on the default driver in the LiveCD for 12.10, even if at a reduced level.

For the problems with installing see Post#3 of this Installations &Updates Forum 'Black Screen' Sticky Thread:
[http://ubuntuforums.org/showthread.php?t=1743535&page=109](http://ubuntuforums.org/showthread.php?t=1743535&page=109)

Post #2 has an index, and Post#1 is a step-by-step Trouble-Shooter, but is not aimed at installation problems, assuming a completed install.

Chao!,** bogan**.

---

