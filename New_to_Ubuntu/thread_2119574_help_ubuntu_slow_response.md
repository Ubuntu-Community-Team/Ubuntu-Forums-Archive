---
title: "help: ubuntu slow response"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by kennethkhoo on 2013-02-24
Hey guys, 

I'm a total newb in linux. I've installed ubuntu 12.04 x32 in my pc today and fully updated it. I've noticed slow response in the UI, mainly when I "Alt-Tab" around, and scrolling through webpage in firefox (compared to windows 8 previously). I suspect ubuntu for not utilizing my graphic card, but I can't tell.. It would be great if anyone can help me in diagnosing & fix this?

Spec:
pentium D 3.0Ghz
4GB DDR2 800 MHz
GeForce GT 218 (GF 210)
Um.. standard 500GB hdd, bluetooth, wifi adapter blah blah...


Additional information:
The CPU seems to be steady at 10% without anything running, then while scrooling/alt tabbing it goes up to 60%..

---

### Post by howefield on 2013-02-24
> **kennethkhoo said:**
> ... I suspect ubuntu for not utilizing my graphic card, but I can't tell..

Try installing the proprietary drivers, open the Dash and search for Additional Drivers, and install from there.

---

### Post by TheFu on 2013-02-24
> **kennethkhoo said:**
> Hey guys, 

I'm a total newb in linux. I've installed ubuntu 12.04 x32 in my pc today and fully updated it. I've noticed slow response in the UI, mainly when I "Alt-Tab" around, and scrolling through webpage in firefox (compared to windows 8 previously). I suspect ubuntu for not utilizing my graphic card, but I can't tell.. It would be great if anyone can help me in diagnosing & fix this?

Spec:
pentium D 3.0Ghz
4GB DDR2 800 MHz
GeForce GT 218 (GF 210)
Um.. standard 500GB hdd, bluetooth, wifi adapter blah blah...


Additional information:
The CPU seems to be steady at 10% without anything running, then while scrooling/alt tabbing it goes up to 60%..

Unity (the main GUI) likes a beefy graphics card running proprietary drivers.  
* Did you install the proprietary drivers using the software center tool?  I do not run Unity myself, but I think it prompts people to install the proprietary GPU drivers now. Did you allow that?
* Unity is "heavier" than most other GUIs. The GUI is not Ubunty, if it just a GUI.  You can add or swap others in fairly easily under any Linux OS, including Ubuntu.  **XFCE** and **LXDE** are other GUI environments that many people prefer. Again, since I don't use Unity, I don't have the *Software Center* and can't tell you how to install either by point-n-click, but if you load Synaptic, the older package manager interface, you will be able to find programs with **XFCE** in the name that you want to load.  XFCE should run great on your hardware using any GPU driver.

Whatever you do, please do not visit the nvidia website and download a driver directly from there.   That method, while it can work, is the harder way under Ubuntu.

There are terminal ways to do all these things. That is how I would do each, but since you are so new, I didn't want to scare you.
If you google "how to install xfce ubuntu", you will find instructions.
If you google "how to install synaptic ubuntu", you will find instructions.
If you google "how to install nvidia drivers ubuntu", you will find instructions ... like these: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Do you see a pattern here?

I'd also point out that with Linux GPU drivers, the latest is not always the best. Highly recommend going with the "stable" version, only if there is a big issue should you try the latest.  I've been burned a few times doing this with terrible bugs.

Good luck.

---

