---
title: "Dell Dimension 2400 screen 'jumping' around"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Huzudra on 2008-08-23
Alright, I've had 7.1 and 8.04 beta installed on this exact (ok new hard drive) machine before with this same board, cpu, and ram without issue, even playing some 3D games.

the problem:
the screen jumps side to side in a very artifacty ghosty sort of way.  at first i thought it was a heat problem since its a warm room and the dimension 2400 has pretty low airflow. so i opened the case and yes the northbridge was pretty hot (i think the NB also holds the video 'card')  the display only has problems when scrolling windows, dropdown menus dropping down, moving from window to window, and loading pages (the page is loading and filling the window).  sitting still and typing on a page the display is fine.

what i've done so far:
turned off visual effects
tested the ram in memtest86 overnight (passed)
added a 120mm fan to blow cool air at the chipset
taken the side panel off and have 120mm fan blowing air at the chipset.

what i have not done:
reinstalled Ubuntu

the hardware:
P4 2.6
1GB PC3200 (@PC2700 speed)
80GB WD Caviar something or other (IDE)
generic black dell CDROM (IDE)
Gateway 2000 EV700 Monitor
Generic Keyboard
Generic USB Mouse

after adding the 120mm fan to direct cool air at the chipset the problem is still exactly the same.  i'd like to get this resolved so i can loan this PC to a friend who's getting DSL so she has a system thats malware resistant.


problem not solved, but worked around perhaps.  since this is a slower PC i did a clean install of Xubuntu. problem seems gone.  however, prior to this i installed the xubuntu desktop on ubuntu and the problem remained. i did that to see if it were a problem with X or maybe a hardware problem.  i'm still unsure if the fault lies with hardware or software. time will tell!

---

### Post by swoll1980 on 2008-08-30
> **Huzudra said:**
> Alright, I've had 7.1 and 8.04 beta installed on this exact (ok new hard drive) machine before with this same board, cpu, and ram without issue, even playing some 3D games.

the problem:
the screen jumps side to side in a very artifacty ghosty sort of way.  at first i thought it was a heat problem since its a warm room and the dimension 2400 has pretty low airflow. so i opened the case and yes the northbridge was pretty hot (i think the NB also holds the video 'card')  the display only has problems when scrolling windows, dropdown menus dropping down, moving from window to window, and loading pages (the page is loading and filling the window).  sitting still and typing on a page the display is fine.

what i've done so far:
turned off visual effects
tested the ram in memtest86 overnight (passed)
added a 120mm fan to blow cool air at the chipset
taken the side panel off and have 120mm fan blowing air at the chipset.

what i have not done:
reinstalled Ubuntu

the hardware:
P4 2.6
1GB PC3200 (@PC2700 speed)
80GB WD Caviar something or other (IDE)
generic black dell CDROM (IDE)
Gateway 2000 EV700 Monitor
Generic Keyboard
Generic USB Mouse

after adding the 120mm fan to direct cool air at the chipset the problem is still exactly the same.  i'd like to get this resolved so i can loan this PC to a friend who's getting DSL so she has a system thats malware resistant.


problem not solved, but worked around perhaps.  since this is a slower PC i did a clean install of Xubuntu. problem seems gone.  however, prior to this i installed the xubuntu desktop on ubuntu and the problem remained. i did that to see if it were a problem with X or maybe a hardware problem.  i'm still unsure if the fault lies with hardware or software. time will tell!

I have the same pc but with a celeron and 768 mb ram It runs really smooth for me. Just to narrow your problem down I don't think it's the hardware

---

### Post by Huzudra on 2008-08-30
> **swoll1980 said:**
> I have the same pc but with a celeron and 768 mb ram It runs really smooth for me. Just to narrow your problem down I don't think it's the hardware

thanks, i actually got it to do the same thing in xubuntu after coming out of hibernate. i think its an issue related to that.  either way i ebayed myself a nvidia 6200 pci for it so i can run the prettier ubuntu with the eye candy on. nicer since i'll be loaning it out to a friend to use and to introduce linux to her.


hey, if you goto the 'ricer' isle at pepboys you can get a pack of 3 LED's for $8 with leads attached, they pop right into the front air vent holes of the case and make the 'smile' of the case glow nicely in a dim room. it looks pretty neat :)  i'm setting up one to be on whenever the system is powered, one to blink for HDD activity, and one to run with the power LED.:cool:

also, hello to a fellow dell-buntu-er.

---

### Post by Huzudra on 2008-09-01
another graphical anomaly, when things open sometimes i see a split second of horizontal black and white lines in the window, like tv static sort of. just for a brief moment, then the window is filled with its normal contents.  this is very repeatable.

maybe this boards chipset is in the shitter?

---

