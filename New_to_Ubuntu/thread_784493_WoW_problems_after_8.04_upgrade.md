---
title: "WoW problems after 8.04 upgrade"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by sir_napsalot on 2008-05-06
I'm currently running hardy heron using the latest version of wine and World of Warcraft will load......but with a rendering error. everytime i load the game it ends up looking crappy. attached a screenshot to show the end result. my video card is the ATI Radeon X1600 running proprietary drivers. can anyone help me resolve this problem?

---

### Post by mapes12 on 2008-05-06
Did everything work before upgrading from 7.10??

---

### Post by sir_napsalot on 2008-05-07
everything worked except the sound before i upgraded to hardy

---

### Post by mapes12 on 2008-05-07
I had screen resolution problems after upgrading to 8.04 so I reinstalled 7.10 which works fine. No doubt there will be an update fix at some point when I will try again.

For sound open a terminal window then ```
alsamixer
``` to see if it can be configured from there.

---

### Post by hyper_ch on 2008-05-07
8.04 can run WoW fine :) do you use the Wine HQ repos?

I just followed that here [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) (alternate 1 install method) and works... even aoss works great.

---

### Post by sir_napsalot on 2008-05-07
Well I've looked at the trouble shooting section of the WoW help from the community. I've adjusted the Config.wtf file with ```
SET gxApi "OpenGL"
``` but the game refused to load, I'd get a black screen and nothing else. I've done the registry tweak as well but that hasn't helped me either, as far as I can tell. Is there anything that I'm missing because I've tried the tricks listed here:
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)
but to no avail. Know of anything I need to do? I did run ```
alsamixer
``` but that didn't help, just allows me to adjust the volume. If you need any more info to help just let me know.

Update - Ran the game just a minute ago and the sound now works but the graphics are still hard on the eyes

---

### Post by sir_napsalot on 2008-05-11
well after working tirelessly on this little project i decided to just re-install 7.10. ran into the SAME hitch i did last time (how i fixed it is beyond me) but can anyone tell me the command needed to just completely get rid of the all fglrx driver work i've done? i used this how/to:
```
https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0
```
all the way down to command line 4 when installing the binary drivers (which in my opinion are garbage to tempt me back to windows) for 7.10.

Update -- curious as to wether or not im losing my mind. just ran ```
fglrxinfo
``` which hasn't worked and all of a sudden it works fine. the command spits this out ```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
``` which i know isn't good. is there some sort of "self-healing" function to linux i don't know about? because this is the second time its happened.

---

