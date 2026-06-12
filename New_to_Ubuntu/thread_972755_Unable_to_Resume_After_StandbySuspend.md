---
title: "Unable to Resume After Standby/Suspend"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by abrussak on 2008-11-06
(I posted this in General Help, but got no response at all....I thought I might post here as well to see if anyone else has a clue.)

Hello folks,

I have the following laptop Everex SA2053T.

8.04 runs perfectly fine and I'm capable of doing system standbys. However in 8.10, if I do a suspend, the standby occurs correctly and the power button blinks at me, but once I attempt to resume, nothing on my screen appears, as if it's turned off. The only means for me to get out of this is to hold down the power button. Ctrl+Alt+Backspace does nothing. For about a second, my battery light will blink between green(charged) and orange(charging).

Any help would be greatly appreciated...

PS: I tried out a xubuntu livecd and still had the same issue, so it isn't gnome-specific.

---

### Post by sayems on 2008-11-06
I have the same problem, when I suspend my computer it goes normally to suspend but when I resume from suspend there is just a black screen and nothing happens. My friend had the same problem and it works for him to press ctrl+alt f8 and then alt+f7. I've tried that many times but nothing works. I have tried everything to make it work, nothing seems to be working. No matter what method I try, I always get black screen after login.

I have got few links for you to trouble shot, they might work out for you.
[http://blog.vaxius.net/?p=19]("http://blog.vaxius.net/?p=19")
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

---

### Post by talsemgeest on 2008-11-06
If you can, try to install a different graphics driver, see if that makes any difference. Standby is connected to the graphics driver you use, so the different driver in 8.10 is most likely the problem.

---

### Post by abrussak on 2008-11-06
The first link won't apply to me because my laptop has an integrated Intel graphics card.

And with the second link, I installed that package, however s2ram is not a known command, and when I tried s2disk, I still got the same result.

> **talsemgeest said:**
> If you can, try to install a different graphics driver, see if that makes any difference. Standby is connected to the graphics driver you use, so the different driver in 8.10 is most likely the problem.

How is this accomplished in 8.10? I know in 8.04 I had the app called "Screens and Graphics"...I can't seem to find an equivalent one in 8.10.

---

### Post by abrussak on 2008-11-06
bump?

---

### Post by talsemgeest on 2008-11-06
If you have intel graphics, search intel in synaptic package manager, or do the same for nvidia or ATI.

---

### Post by philinux on 2008-11-06
Now this is weird. I've never been able to put my desktop to sleep until Intrepid. It works great now even sound works.

Is this a laptop issue now?

---

### Post by abrussak on 2008-11-06
The one i found that matches: xserver-xorg-video-intel is already installed.

---

### Post by mohdiarra on 2008-11-07
I have a gateway laptop with ATI and suspend/resume was working fine with ubuntu 8.04, but ever since I installed 8.10 my laptop doesn't resume from suspend, I get the black screen with the fan spinning...
Please help...

---

### Post by abrussak on 2008-11-10
Anyone have any other ideas?

---

### Post by notnic on 2008-11-28
I am having the same problems as above. Sometimes if the fans are off after a suspend, I can hit a key on the keyboard to get them spinning, but still no screen.

---

