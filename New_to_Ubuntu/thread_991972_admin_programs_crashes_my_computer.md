---
title: "admin programs crashes my computer"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by taith on 2008-11-24
hey everyone...

whenever i try to get into the visual admin mode... for programs such as synaptic, my computer locks up... i can sometimes move the mouse... but all programs are inaccessible :-( only way to regain control i to do a hard-restart

i can still access these programs via terminal (thankfully) without locking up my computer

i am running ibex current...

i think this may have something to do with my nVidia xserver... as this only started after i set up my second monitor...

---

### Post by ohzopants on 2008-11-25
Does everything just sort of gray out? Or does it actually lock up?

Check your second monitor for the password dialog.  Maybe it's just popping up where you don't expect it to.

---

### Post by Thelasko on 2008-11-25
> **taith said:**
> i think this may have something to do with my nVidia xserver... as this only started after i set up my second monitor...

Yup, It's somewhere in you're graphics configuration.  I had the same thing happen to me when I played with the settings in Xorg.conf for my Intel card.  When you try to access an administrative application, the password dialogue box comes up.  While that password dialogue is up, the rest of the screen is supposed to turn grey.  If you have the wrong graphics settings, turning the screen grey can lock up the machine.

Sorry, I don't remember what I did.  I think it was back in Gusty when I had this problem.  I think it was a screen option.

P.S. Can you post your xorg.conf?

---

