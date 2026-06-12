---
title: "Improving memory on GNOME 2.32"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Foobarz on 2012-03-28
So,on my GNOME 2 machine I found that the biggest memory hog was gnome panel and the various applets on it?

Is there some way to reduce memory usage in GNOME 2? (Suggestions about XFCE and LXDE are great, but for me that is worst case scenario, especially LXDE since it's kind of primitive to date)

---

### Post by bodhi.zazen on 2012-03-29
How much RAM do you have and what problem are you having ?

What version of Ubuntu are you running ?

What makes you think the panel is using too much ram or that reducing the amount of ram it is using is important ?

---

### Post by mastablasta on 2012-03-29
why is XFCE worst case scenario? it's basically a light gnome :-)
 
you can remove the virtual desktops if you are not using them. also background image...
 
but you won't be able to have anything functional below 130-140 MB at idle. load up some programmes and you are toast.
 
a better way would be to use XFCE and tweak that one. you can go as low as 70-80 Mb at idle.
 
Then from the nicer options there are also E17 and Razor QT (both kind of experimental).

---

### Post by kazztan0325 on 2012-03-30
Hi Foobarz,

What about trying to use **'zRam'**?

**Sergey "Shnatsel" Davidoff >> zRam stuff on Launchpad**
[https://launchpad.net/~shnatsel/+archive/zram]("https://launchpad.net/~shnatsel/+archive/zram")

---

### Post by Foobarz on 2012-03-30
Ok, I have 512 Mb Ram, I checked system monitor and it had originally showed gnome-panel and metacity to be consuming a lot of memory, but now its fine after I turned off metacity compositing. 

But hey, any suggestions to reduce RAM usage (excluding using lighter programs)?

---

### Post by kazztan0325 on 2012-03-31
> **kazztan0325 said:**
> What about trying to use **'zRam'**?

**Sergey "Shnatsel" Davidoff >> zRam stuff on Launchpad**
[https://launchpad.net/~shnatsel/+archive/zram]("https://launchpad.net/~shnatsel/+archive/zram")

I would like to suggest you would try 'zRam'.

There is a explanation of 'zRam' here:
[http://en.wikipedia.org/wiki/ZRam]("http://en.wikipedia.org/wiki/ZRam")

I think it would increase performance on your machine.

---

