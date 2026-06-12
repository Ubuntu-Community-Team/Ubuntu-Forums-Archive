---
title: "2 monitors 2 X11 screens  fire fox will only run on one"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-05-21
yep i have 2 X11 screens and fire fox will only run on the one at a time
any body got a clue to why

and what is the best way to use 2 screens and compiz

---

### Post by Inxsible on 2008-05-21
depends on your graphics card. If you have nVidia, then you should use the restricted drivers and nvidia-settings to enable TwinView or clones.  As for your Firefox issue, it does seem strange. Does it give you any errors when you try to start it up the second time?

---

### Post by zeifertstc on 2008-05-21
> **Inxsible said:**
> depends on your graphics card. If you have nVidia, then you should use the restricted drivers and nvidia-settings to enable TwinView or clones.  As for your Firefox issue, it does seem strange. Does it give you any errors when you try to start it up the second time?

Back when I had dual monitors setup I encountered this exact situation. Apparently, Ubuntu will only allow you to run one instance of Firefox the error message that pops up is "An instance of Firefox is already running" as of yet, I have not found any way to get around this limitation.

Perhaps, if somebody were to find a way around this minor issue, I'd be willing to setup a dual monitor deal again. For now, I don't see any use for dual monitor, myself. But, yeah, it's not strange as it's been that way since Hoary Hedgehog.

---

### Post by Inxsible on 2008-05-21
Open up a terminal and try ```
killall firefox
```Then try starting two instance of Firefox.  I find it strange that you guys have that problem, since I have TwinView enabled and I run as many instances of firefox as I want.

---

### Post by angela57 on 2008-09-30
hello i have a kwetion about me resolution of me screen at this moment i have a resolution of 800+600 60

i have a monitorscreen of 22 inch how ken i chans this resolution to 1268+789 32 ore 16

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-27
I know my tread is really old but anyway i think i should clarify the problem. 

Right not using twinview because i would like to have 2 cubes one for each screen

So with 2 x screens you can have 2 cubes, but with 2 x screens you can only have firefox on one screen

---

