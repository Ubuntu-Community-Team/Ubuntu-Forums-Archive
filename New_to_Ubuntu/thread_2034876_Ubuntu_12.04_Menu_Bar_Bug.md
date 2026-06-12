---
title: "Ubuntu 12.04 Menu Bar Bug"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by beastk17 on 2012-07-29
I'm really not certain how to refer to this question or really what to call it, so forgive me if it is already answered and i was unable to locate it.

I've been using ubuntu for the past few months and its been running smoothly, but recently this bizarre problem has occurred.
in the first screenshot is the menu when it looks normal, but now in the mail, user session, and sound menus the color has changed to white. its a small thing, but its irritating.

this started right after i was trying to install google earth through a plethora of methods in terminal and synaptic. i gave up on that, but then this started happening.

I have a lenovo Z570 running ubuntu 12.04

---

### Post by NikTh on 2012-07-29
Hi , 

it seems to me like a compiz settings problem . 

Did you change something lately ? 

Do you want to reset all your settings ? maybe this helps to solve it  (maybe not). 
_**You will lose ALL your settings**_ (even wallpaper) if you run below command 
```
rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
```
but maybe this solve your problem. 

Thanks

---

### Post by Krytarik on 2012-07-29
This is a bug of the default 'light-themes' (Ambiance and Radiance) that apparently affects both Precise 12.04 and the currently under development Quantal 12.10, though to a rather limited extent, it seems:

[http://ubuntuforums.org/showthread.php?t=2026646](http://ubuntuforums.org/showthread.php?t=2026646)

Regards.

---

### Post by beastk17 on 2012-07-29
Thanks for the info, i guess i'll make do with changing the theme every session.

Btw the remove settings commands didn't fix the problem but thanks for the advice.

---

