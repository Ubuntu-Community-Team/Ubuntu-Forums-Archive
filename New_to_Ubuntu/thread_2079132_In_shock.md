---
title: "In shock"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by geomcd1949 on 2012-11-01
I started using Ubuntu about six months ago. It took a while, but I finally got my setup to work: dual monitors with an AMD three-core processor and a cheap graphics card. Then I get the great idea to build a really nice computer. So I get an Intel 3770, with four cores and hyper-threading, and a nice Radeon graphics card. I put 32GB of memory in it, just for the hell of it. 

Then, tragedy: I installed Ubuntu 12.04. With the graphics card installed, it wouldn't detect two monitors. There is an overlay in the bottom right of the screen saying the hardware is incompatible. The sound won't play. I thought about upgrading to 12.10, but halfway through the process a popup tells me that the performance of my system will be degraded if I continue. 

So I take out the graphics card, and hope that the integrated graphics of the CPU will be OK. It's the HD 4000. No joy. Same problems (although I do get sound with this). A similar notice when I try to upgrade, saying the system will be degraded. I try it anyway, and all I get is a full-screen terminal. 

I Google the problems. Seems they're everywhere. I'm wondering what's going on? Have I missed something? Doesn't Ubuntu support 2012 hardware? Have I fallen into a trap that waits for all rookies?

Please help. I really don't want to go back to Windows.

~George

---

### Post by LERecords on 2012-11-01
I feel your frustration.. I have settled on sticking with 11.04 until they hammer more bugs out of 12.10.. Ubuntu is an amazing os, but has its share or problems like everything else.. I would suggest lookin at 11.04 or 11.10 for the time being. Should work fine for your setup.

---

### Post by geomcd1949 on 2012-11-01
Thanks. Was hoping I made some easily correctable mistake, but I guess not. 

How do I "downgrade" to 11.04?

---

### Post by mastablasta on 2012-11-01
you didn't :

1. say what graphics card exactly do you have
2. if you have a newer card you need proprietary drivers. and if you have very new card 12.10 is what you are looking for.

intel 4000 series should work well.

---

### Post by blackbird34 on 2012-11-01
> **LERecords said:**
> I feel your frustration.. I have settled on  sticking with 11.04 until they hammer more bugs out of 12.10.. Ubuntu is  an amazing os, but has its share or problems like everything else.. I  would suggest lookin at 11.04 or 11.10 for the time being. Should work  fine for your setup.
I'd say use 12.04 not 11.04: the latter's out of support, whereas 12.04 gets hardware updates in point releases (12.04.1).
Have you tried a **clean install **of Ubuntu 12.10 from scratch?

---

### Post by geomcd1949 on 2012-11-01
Sorry. Intel Core i7 3770; ASRock z77 Extreme4; HIS iCooler H775F1GD Radeon HD7750; 32GB Corsair Vengeance (4x8GB) DDR3 1600.

I'll try a fresh install of 12.10.

Really appreciate the advice.

~George

---

### Post by geomcd1949 on 2012-11-01
Did a fresh install of Ubuntu 12.10. Almost everything now works: Dual monitors are recognized; I can set their respective resolutions; there is no overlay saying there is incompatible hardware.

The only thing not working properly now is the sound. My HD monitor has built in speakers. It will play HD video but there is no sound. Rhythmbox and VLC indicate when a CD is playing, but no sound is heard. When I connect plug-in speakers to the green hole from the motherboard, sound plays when either Analog Outout (Built-in Audio) or Headphones (Built-in Audio) is selected, but no sound is heard when Digital Output (S/PDIF) is selected.

Am not sure this is an OS problem, and suspect it might have something to do with hardware configuration. Am just not sure, and would appreciate suggestions and advice.

Thanks LERecords, mastablasta and blackbird34 for solving the original problem! Very much appreciated!

~George

---

### Post by Cheesemill on 2012-11-01
Go to Settings > Sound > Hardware and choose a different output from the drop down list. For example on my machine I have 3 different HDMI outputs listed but only one of them results in sound going through the HDMI cable.

---

### Post by geomcd1949 on 2012-11-01
I go to ALL SETTINGS >SOUND. For "Output" I have three choices: Digital Output (S/PDIF); Headphones; and Analog Output. 

Headphones and Analog Output play sound through speakers attached to the green hole from the motherboard. 

Digital Output (S/PDIF) doesn't give sound. [I know the sound is working and turned on in the monitor because I tested it on another computer.]

Am I looking in the place you mean for me to be?

~George

---

### Post by Mark Phelps on 2012-11-01
The "green hole" is the analog audio OUT jack on your motherboard.

When you select SPDIF, you must have speakers connected to the SPDIF jack on your motherboard.

---

### Post by geomcd1949 on 2012-11-01
Sorry, Mark, I'm missing your point.

---

