---
title: "Nvidia graphics card driver problem"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Wenchkin on 2008-06-06
Ok, first the hardware concerned:
XFX Nvidia GeForce FX 5700 LE graphics card (don't laugh!)

I'm using Kubuntu Hardy Heron, kernel 12 (I can't get any subsequent kernels to boot as yet :()  I'm not sure if the graphics card driver has anything to do with this, as all the other hardware seems to be functioning perfectly.

I followed the instructions to autodetect the best driver with EnvyNG.  It's installed the FX generic driver and for basic work it's been acceptable. However, I'm suspicious that I have an issue with either the driver or card, most obvious when I'm loading games in Kubuntu.  I see the egg timer on the tab at the bottom of my screen, then the tab vanishes and nothing else happens.  No error message pops up.  Very simple games seem to work fine, which also suggested to me that the graphics card was the problem loading the more "flashy" ones. 

Should I try to install a different driver in Envy or would it be easier to remove Envy altogether and manually install the driver from Nvidia?  What's the safest way to remove Envy and the driver it installed if I want to do this?  

Incidentally, in the event that the card is just not going to work well under Kubuntu, is there a list of good Nvidia cards which do? 

Thanks,

Wenchy

---

### Post by Hospadar on 2008-06-06
I think that card should work fine with ubuntu, I used to rock almost the same card and can't recall any issues.  Do you know if you are getting any 3d acceleration at all? I would try a couple things and then report back here.  Get a terminal open and:
type in "glxgears" report what happens, post any suspicious terminal output
start a game from the terminal and post any suspicious terminal output.  I think you will have a much harder time manually installing the driver, although you might try using envy to remove the driver, and then use ubuntu's restricted driver manager to install and configure your driver.

---

### Post by Wenchkin on 2008-06-06
Oki,

Output from glxgears command:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


I'm not sure if I did this right, but tried running a game by entering "/usr/games/tomatoes"

And got this:

Error appeared:
 - Unable to set the OpenGL video mode 800 x 600 (32 bit)!
Couldn't find matching GLX visual

I'm not sure how much help that is ;)

Wemchy

---

### Post by PinkFloyd102489 on 2008-06-06
Im running a 5200FX, you can laugh at me. :-P


I dont know if this will help, but I have to have Compiz running in order to play an OpenGL game. Try that?

---

### Post by alienexplorers on 2008-06-06
In envy for that card select manual install and select the 96.xx.xx driver.  I have a fx5200 and that is what worked for me.  I have full use of compiz and can play games with good fps.

---

### Post by PinkFloyd102489 on 2008-06-06
Im using the new 173 driver on my 5200FX. It works well.

---

### Post by alienexplorers on 2008-06-06
Would not work for me.  Would not let me start compiz and the system kept starting at 800x600resolution.

---

### Post by Wenchkin on 2008-06-07
I've gone into EnvyNG and told it to remove the old driver and then manually installed the proper one.  System rebooted fine and no white screen of death etc.

I've installed compiz, however it refuses to load (egg timer shows at the bottom of the screen on the "tab" but then both vanish).  

I loaded up Cadega config to see what it said.  It detected the graphics card...sorta.  During the testing it came up telling me there was an opengl problem and 3d problem, other tests went fine.  I could see the cogs but they weren't quite turning... bit like myself LOL.

Opening Adept Manager, I checked for opengl packages and none seem to be installed.. ruh roh :D  So before I (further) break the system, is there a correct way to get opengl functioning properly?

On the plus side, while horribly slow, I can get one of the "bad" games to at least load up and start.  So it's getting there!

Wenchy

---

