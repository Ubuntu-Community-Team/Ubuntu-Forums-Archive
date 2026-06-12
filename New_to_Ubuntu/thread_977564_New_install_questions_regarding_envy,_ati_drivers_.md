---
title: "New install: questions regarding envy, ati drivers &amp; beep"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by jolly_grunt on 2008-11-10
Over the weekend, I did a clean install of Ubuntu 8.10 on my Dell e1505 notebook. I partitioned 4gb for swap, 10gb for root and the leftover 60+gb for /home. Does that sound about right?

After the initial install, I installed the 34 updates that were pending. Then I installed the available proprietary graphics card driver.

Should I have installed envy beforehand and allowed it to find the drivers for my card? 

Can I install envy now even though I've already installed the proprietary drivers?

I'm having flickering video problems and even the 3d flying toasters screensaver will ficker whenever I have desktop effects set to normal. It all appears to work perfectly with desktop effects set to off.

Also, I get a beep every time I shut down/restart Ubuntu. Is this normal?

I'm still in the fine tuning stage and pretty much enjoying it. I also love the flying toasters screensaver which reminds me of the old After Dark screen saver software for the old mac os. :D

---

### Post by Paqman on 2008-11-10
> **jolly_grunt said:**
> Over the weekend, I did a clean install of Ubuntu 8.10 on my Dell e1505 notebook. I partitioned 4gb for swap, 10gb for root and the leftover 60+gb for /home. Does that sound about right?

4GB swap sounds a little large. You'd only need one that big if you had 4GB RAM and wanted to hibernate. If you have more than 1GB of RAM you'll probably find you aren't using *any* swap in normal use. 

> 
Should I have installed envy beforehand and allowed it to find the drivers for my card? 


No, the default drivers are ok. Envy might include updated ones though.

> 
Can I install envy now even though I've already installed the proprietary drivers?


AFAIK, that's fine.

> 
Also, I get a beep every time I shut down/restart Ubuntu. Is this normal?


Er, dunno. Been a long time since i've used a default profile. Try System > Prefs > Sounds.

---

### Post by oldrocker99 on 2008-11-10
I use an nVisia card, but when I had trouble with the Ubuntu-provided drivers, I used Envy to remove the drivers, then install drivers itself. Worked fine.

---

