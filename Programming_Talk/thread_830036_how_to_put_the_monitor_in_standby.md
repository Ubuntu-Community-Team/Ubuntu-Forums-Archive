---
title: "how to put the monitor in standby?"
date: 2008-06-15
forum: Programming Talk
---

### Post by Clive McCarthy on 2008-06-15
I want to turn the display monitor off, from within a C program. Clearly the OS can sends control signals via the graphics card to put the monitor in standby mode via Display Power Management Signaling (DPMS). I guess there is a system call to do this? Is there a console command to do this?

Standby: Back-light off. Not hibernate where the state of the machine is saved to disk. I want my program to just power down the monitor to save power and, most importantly, extend the monitor's life. An LCD display is good for three years running 24/7 but I want my application to run just from 7:00am to 11:00pm every day. If can save 8 hours in 24 that increases the life by 18 months.

When 7:00am comes around I want my program to wake the monitor up. Eight hours sleep is all any monitor really needs.

It looks like "xset dpms force standby" and "xset dpms force on" may do the trick if called via a C system(""); function.

---

### Post by stroyan on 2008-06-15
The system() approach will work.
You can also look at exactly what the xset command is doing.
 apt-get source x11-xserver-utils
 view x11-xserver-utils-7.3+2/xset/xset.c
Look at all the code in the "#ifdef DPMSExtension" conditionals.

---

### Post by Clive McCarthy on 2008-06-15
Very cool. You can't do that in XP!

---

### Post by Clive McCarthy on 2008-06-18
Your advice here has been very helpful. :popcorn:
My next system issue is to figure out how to invoke fullscreen mode from within my program?

I found advice about manually doing what I want by using:
system>preferences>keyboard short cuts>window management>toggle fullscreen mode
Which does exactly what I need.

I need to unleash my OpenGL/glut program from the fenestration's mullions. A system call to the window manager is probably what I need...

:)

---

