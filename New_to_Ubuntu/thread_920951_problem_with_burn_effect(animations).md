---
title: "problem with burn effect(animations)"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-09-15
i have set the burn effect to show up i close a window everytime,which looks damn good.but,i have noticed that while i am running VLC  in the background,the audio gets disturbed for a fraction of a second,due to the burn effect on closing some window,which is noticeable.my computer has got 2 gigs of RAM,and has a nvidia graphics card with 256 MB VRAM,and is powered by core 2 duo processor(2GHz).how do i solve this?there aren't any problems using compiz and other eyecandy stuff.

---

### Post by stonecoldjha on 2008-09-16
can anyone get me fix this?thanks in advance.

---

### Post by LowSky on 2008-09-16
The biggest issue is Compiz in general, as far as I know. Compiz is trying to use your video processing at the same instance that another video source may wish to. If your watching movies the best thing to do is to turn off compiz effect and return to metacity..

there is a thing called fusion icon that can place a compiz icon inthe tray to turn off/on the effects, it in synaptic

---

### Post by stonecoldjha on 2008-09-16
so the two can't go together at the same time.does that hold even in case of a superior configuration.

---

### Post by silverglade00 on 2008-09-16
You might want to try turning down the burn effect. What I mean is to go into the CompizConfig Settings Manager to the Animations section and reduce the settings under Fire. Try number of fire particles (500 works great for me) and reduce the particle life some.

---

