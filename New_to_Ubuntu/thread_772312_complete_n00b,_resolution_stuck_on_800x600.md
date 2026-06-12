---
title: "complete n00b, resolution stuck on 800x600"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by con spirito on 2008-04-28
hey guys, i just installed ubuntu 8.04 through Wubi.
what can i do to change my resolution to 1024x768? i have a via sg3 unichrome pro graphics chip on a fujitsu amilo L7300 laptop. from the installation it said its going to run on low graphics and i couldn't configure it. tried to search the forums but got even more confused. i am VERY VERY VERY new to this, so please help.

---

### Post by tzulberti on 2008-04-29
Go to System -> Preferences -> Screen Resolution.

---

### Post by brigadoon on 2008-04-29
> **con spirito said:**
> hey guys, i just installed ubuntu 8.04 through Wubi.
what can i do to change my resolution to 1024x768? i have a via sg3 unichrome pro graphics chip on a fujitsu amilo L7300 laptop. from the installation it said its going to run on low graphics and i couldn't configure it. tried to search the forums but got even more confused. i am VERY VERY VERY new to this, so please help.

We feel your pain. We were all new at one point. I am assuming you are using a driver compatible with Ubuntu 8.04. Drivers I used on previous versions of Ubuntu did not work for my laptop. This means trial and error to find the right one in some cases.

I have a NVIDIA GeForce4 420 Go card on a Toshiba Satellite laptop. I had similar problems. Trying to fix one lead me to a few others. Don't give up hope though. I was able to resolve my hardware conflicts with Ubuntu 8.04. My fix can be found at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

I faced the same symptom you described with a different piece of hardware. With my laptop the NVIDIA driver was not configured to see the higher resolution display. Drivers are written by people and people make mistakes or can't think of everything. I think if you try using a custom edid.bin file described in my thread you may be able to get to the higher resolution. It may be worth a try. However, to get it to work your driver control program needs to be able to export a edid.bin or similar file. Your hardware provider may have called it something different but the theory behind the solution may be what ails your system.

Good luck.

---

### Post by tliotis on 2008-04-29
thanks for the support

---

### Post by pedro_orange on 2008-04-29
EDIT: I need to learn to read

---

