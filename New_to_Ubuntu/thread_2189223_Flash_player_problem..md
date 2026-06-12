---
title: "Flash player problem."
date: 2013-11-21
forum: New to Ubuntu
---

### Post by Toni_Vines on 2013-11-21
Hello, I've mentioned this before but got nowhere so left it. I'm of a mind to try and fix this now if I can. I am running Ubuntu 12.04 0n a Dell Opti-plex GX-260 machine. I have 1.5 gig memory, Intel® Pentium(R) 4 CPU 2.80GHz processor. 
Now the strange thing is that YouTube videos are playing fine with Flash Player in Google Chrome but if I try to view YouTube in Firefox The picture seems to be negative and is squashed up in the left hand half of the frame. The sound is fine. 
Does anyone have any ideas, suggestions? As I can watch YouTube etc OK in Chrome this is not a desperate situation, more something I would like to answer out of interest. 
Thanking you all,
Toni.

---

### Post by simbauad on 2013-11-21
Well The flash player in firefox and chrome are different. Chrome uses it's own version of flash player known as pepper flash. Firefox uses the default flash player installed by ubuntu. Adobe has stopped flash player development for linux. However, chrome regularly updates it flash player for linux, making it the only means for using up-to-date flash-versions. However, it shouldn't be that the flash player be glitchy on firefox. Could you tell how you installed flash in ubuntu?

---

### Post by Toni_Vines on 2013-11-21
Thanks for your reply simbauad, I haven't installed Flash. I'm just running it as it came in Firefox on the original install. I'm a total newbie to all this so I may have missed something very obvious here. Sorry if I have.

---

### Post by simbauad on 2013-11-21
During installation, did you leave the default options during the first step? Could you open up the Ubuntu Software Center and paste this: flashplugin-installer. Is there a green tick over the adobe flash logo? If it's there flash is already installed. If no, then click on install. It will take some time.

---

### Post by Toni_Vines on 2013-11-21
Yes it's got the green tick on it.

---

### Post by simbauad on 2013-11-21
Ok. That could be a problem with the GPU drivers. Open up the dash > Softwares & Updates > Additional drivers > and tell us if you are using opensource or proprietary drivers. If you got the opensource drivers installed install the proprietary one. And then check on flash performance once again.
***[SIZE=3]_But before doing that:_[/SIZE] Right click on a video you are watching > flash player settings > display > untick/tick the hardware acceleration checkbox if it is ticked/unticked. Try restarting the browser after that and tell us if it has any changes.***

---

### Post by Toni_Vines on 2013-11-21
I've right clicked on the video and I can see the box with the check-box for video acceleration but it's all squashed up the the left hand side and won't let me un-check the box! 
As to Open up the dash and go to Softwares & Updates, I can't see this anywhere, sorry!

---

### Post by simbauad on 2013-11-21
Oops sorry. The solution was from Ubuntu 12.10 onwards. Didn't notice you were running 12.04. Dash > Additional Drivers

---

### Post by Toni_Vines on 2013-11-22
Hi simbauad, it says "There are no [COLOR=#000000]proprietary drivers in use on this system." [/COLOR]

---

### Post by simbauad on 2013-11-22
Your computer has intel driver?

---

### Post by Toni_Vines on 2013-11-22
I don't know. Where should I look to see?

---

### Post by simbauad on 2013-11-22
Copy/paste this in to the terminal:
```
lspci | grep VGA
```

---

### Post by Toni_Vines on 2013-11-22
This is what I get: 
toni@toni-OptiPlex-GX260:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
toni@toni-OptiPlex-GX260:~$

---

