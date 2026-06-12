---
title: "Ctrl+Alt+F7 - Very Slow screen redraw (Nvidia 280.13 proprietary)"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-05
Hello, I am seeing something new with today's updates. I can switch from Unity Desktop to any VT very fast. Switching between VTs is also instant. Switching from any VT back to Unity (Ctrl+Alt+F7) gets me a black screen with the mouse for about 20 seconds. After this time the desktop appears and everything is fine again. There's nothing specific in my logs. 

I am running Nvidia 280.13 64 bit proprietary. Hardware is more than enough for a normal performance. Everything else seems to work OK, no other error detected.


I would appreciate any ideas. Not sure how to debug this with no errors or warnings.

Regards,
Effenberg

---

### Post by WorLord on 2011-10-06
Same here.  Not a dealbreaker, but wow.

---

### Post by effenberg0x0 on 2011-10-06
It seems to be a lot faster when using Ubuntu 2D (5 seconds, more or less, to redraw the desktop). So it probably could be related to Compiz. There have been Compiz+Nvidia+VT Switching bugs in the past, but it seems they have been worked out by 2008/2009. 

What is really weird is that can't find a single system output message that gives me a lead to what is going on. No xorg error, no compiz error, kernel, etc. Nothing.

Initially I thought it could relate to the fact that I have a console framebuffer, but so far I could not prove it.

I will test it with some different proprietary drivers versions and also with the open source driver, in order to produce a more relevant bug report. Right now it's to vague. 

In case anyone that is facing the same behavior reaches this thread, it would be interesting to compare platforms.

I am running NVidia GTS 450 (Single card) with driver version 285.05.09, Compiz 0.9.6, Xorg version 1.10.4, Mesa 7.11-0ubuntu3, everything on AMD64.

Regards,
Effenberg

---

### Post by mr.miles on 2011-10-10
I am having problems that might be related. I posted these launchpad bugs: 
	868889	screen does not refresh until mouse click or movement over responsive area		unity
 	871600	windows don't refresh, sometimes tearing happens		xorg 
 	871614	windows don't update reliably until menu bar is clicked   xorg

I've had the same problems with nvidia current restricted and current-updates restricted driver, as well as the nvidia 173 driver. The only way I can make a window reload reliably is for me to drag it around. then there is some tearing.

(this is with amd64 oneiric and Nvidia GeForce 430 GT  on a Dell Optiplex 960)

---

