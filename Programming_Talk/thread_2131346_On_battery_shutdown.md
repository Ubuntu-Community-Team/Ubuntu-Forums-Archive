---
title: "On battery shutdown"
date: 2013-04-01
forum: Programming Talk
---

### Post by conradin on 2013-04-01
Hi all, 
is there a script out there which can detect if my computer is on battery, and shut down accordingly?
This is for a Rasberry PI, where there is not an actual UPS attached, just a battery, and a hard wired power source. 
So I want the PI to power on when I start my car, then when i shut of the car, (power on the main line is now off)
so then I want the RPI to detect that is on auxiliary power, and shut-down accordingly. 
(I am actually using wheezy Debian for this)

---

### Post by trent.josephsen on 2013-04-01
Can you describe the power distribution structure of this project in more detail? Specifically, does the main power charge the battery, which powers the RPi, or does the RPi run off of main power initially and switch to battery when it detects the main level falling?

Is it even possible for the RPi to detect a voltage drop in the main supply? (If you only have two wires going from power supply to Pi/battery, the answer is probably "no", at least not without some clever circuitry. But maybe the RPi has some of that cleverness built in.)

---

