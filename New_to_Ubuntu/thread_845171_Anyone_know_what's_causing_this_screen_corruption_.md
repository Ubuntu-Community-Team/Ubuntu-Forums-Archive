---
title: "Anyone know what's causing this screen corruption when an app launches."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by philinux on 2008-06-30
I'm running compiz and the nvidia driver NVIDIA UNIX x86_64 Kernel Module  173.14.05

It doesn't happen all the time and I was lucky to grab a screen shot. It appears like this for about half a second or less.

---

### Post by Canis familiaris on 2008-06-30
It happens with me too whenever Compiz is enabled. I have an ATi card.

---

### Post by RomeReactor on 2008-06-30
I get that as well (GeForce 6200). I think it's just the buggy nVidia driver. It doesn't happen if Compiz is off.

EDIT:
> **Anurag_panda said:**
> It happens with me too whenever Compiz is enabled. I have an ATi card.

It might be Compiz after all...

---

### Post by philinux on 2008-06-30
Well that's not the cheery news I was looking for :shock:. I turned animations of to see if that was it too. 

Is this called tearing or is that something else.

---

### Post by RomeReactor on 2008-06-30
I think tearing is when the video card isn't able to keep up with the selected framerate; when you move a window, it looks like it's breaking up.

This problem may also have to do with framerate; I couldn't find a relevant Compiz bug in Launchpad.

I could only find just [one more thread]("http://ubuntuforums.org/showthread.php?t=716901") on this. For me, this problem only happens in Firefox. It *could* be a bug in Gecko...

---

### Post by philinux on 2008-06-30
It happens launching Thunderbird too although not as bad and open office. It's so random I bet it happens with a lot of apps.

I'd put my money on the graphics driver or compiz.

---

### Post by Canis familiaris on 2008-06-30
It happens launching Opera too.

---

### Post by philinux on 2008-06-30
Well I'm glad I'm not alone, I think I'll bug this at launchpad.

---

### Post by Canis familiaris on 2008-06-30
I am sure it is a Compiz bug.

---

### Post by sayakb on 2008-06-30
It used to happen in Gutsy on my laptop that has a GMA950 (Intel Onboard). It is a memory related issue. Are you running out of RAM? Try **preload** if it helps.

---

### Post by Canis familiaris on 2008-06-30
> **LinuxIsInnovation said:**
> It used to happen in Gutsy on my laptop that has a GMA950 (Intel Onboard). It is a memory related issue. Are you running out of RAM? Try **preload** if it helps.

I have 2GB RAM and use from 20-80%. Never has crossed that. So I guess I'm not tunning out of RAM.
BTW How do I try preload?

---

### Post by sayakb on 2008-06-30
Actually 80% is infact *running out of RAM *;)
What abt you philinux?

---

### Post by Canis familiaris on 2008-06-30
> **LinuxIsInnovation said:**
> Actually 80% is infact *running out of RAM *;)
What abt you philinux?

Well 80% happens only when I run XP in Virtualbox. Usually the usage hovers from 20-25% and still this problem occurs.
BTW Are you talking of Video Memory?

---

### Post by sayakb on 2008-06-30
No.. Intel Cards as I mentioned that I have on one of my laptops don't support direct rendering. So Video memory doesn't at all come into the picture here.. (or does it?)

---

### Post by philinux on 2008-06-30
At this point and it's been happening today, system monitor says.

418meg 20.9% of 2 gig, swap 84kb.

So I dont think it's memory related as it happens when I login and fire up FF as the only app running.

---

### Post by jerome1232 on 2008-06-30
Just thought I'd throw in I get this problem as well, Nvidia FX 5600LE using 173.14.9 x86_64 driver, have 1 GB of RAM but according to my System Monitor I never dive into the swap, haven't noticed if this only occurs during heavy processing etc...

---

### Post by phoenix_abhi on 2008-06-30
I may not be correct, Confirm ur all plugin working well. I beleive u are turned on some of the new pluins in CCSM which is colliding with the animations plugins

---

### Post by philinux on 2008-06-30
Which ones?

If you read my previous posts I turned off animations and it still happens. The screenshot on the first post is with animations off.

---

### Post by phoenix_abhi on 2008-07-01
Have u installed new plugins like stacks, freewins or anaglyph, photowheel, elements etc

---

### Post by philinux on 2008-07-02
No no new plugins at all, just the default.

---

### Post by phoenix_abhi on 2008-07-02
Sorry phil, then it is FX3, have u tried FX2 after uninstalling FX3

---

### Post by philinux on 2008-07-02
It happens with Thunderbird and open office.

---

### Post by phoenix_abhi on 2008-07-02
Very very rarely it happends in my Hardy 64, that 2 after installing new plugins earlier everything was fine. So the suggetions from my side are over, sorry bro

---

### Post by philinux on 2008-07-11
Thought I'd give this one last bump.

---

### Post by rekado on 2008-09-28
I also noticed this using the latest alpha of Intrepid Ibex. It also happens with every single drop down menu or the main menu in the panel.

I do not use Compiz.

---

### Post by rekado on 2008-10-06
Might be related to CPU frequency scaling. Seems like the CPU speed is adjusted a bit too slowly so that the glitch occurs.

---

