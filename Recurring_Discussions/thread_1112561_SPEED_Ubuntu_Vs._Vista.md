---
title: "SPEED Ubuntu Vs. Vista ??"
date: 2009-03-31
forum: Recurring Discussions
---

### Post by bsta520 on 2009-03-31
i recently dual boot installed ubuntu along with vista...and after changing some things around .. visually... it seems like its not as fast as when i am on vista...i have the visual looks to the second check..and when i have two or three windows open things start to have delay time...in vista i can have 5 windows open no problem ... high ram usage programs too... including photoshop, firefox, word, and anything else..

is this normal?  are there any settings i can play with or change around?  thanks!

---

### Post by cariboo on 2009-03-31
No that isn't normal, open an Applications-->Accessories-->Terminal and type:

```
top
```

and check which server/application is using the most cpu cycles.

Jim

---

### Post by 3Miro on 2009-03-31
Have you installed proper video drivers for Ubuntu. If you have NVIDIA or ATI you need the proprietary driver, otherwise everything would be slow.

---

### Post by bsta520 on 2009-04-01
> **3Miro said:**
> Have you installed proper video drivers for Ubuntu. If you have NVIDIA or ATI you need the proprietary driver, otherwise everything would be slow.

i think i might have in an update while i had wireless problems.. but is there a way to check for that??


also to anyone reading...when my ubuntu loading screen is up i have to hold a key .. any  key...for it to load...if i dont nothing will load and the bar will just sit there... same goes for when i shutdown...   how do i fix this?  and please dont  tell me to reinstall...i just got done with a weeks work of fixing the wireless..

---

### Post by philinux on 2009-04-01
Have a look in System>admin>Hardware Drivers, see if any are offered to be installed.

Whats the spec of the machine and what version ubuntu you running.

---

### Post by bsta520 on 2009-04-02
Amd turion 64x2 mobile tl-60 2.00 ghz  3gb ram

---

### Post by SamNSane on 2009-04-03
The relative speeds of these operating systems is going to vary by general hardware capability and by the way the operating systems' driver databases cope with the hardware present in the systems. Frankly, Vista's memory management, UI speed optimization and disk access optimization schemes are pretty hard to beat. Vista loaded onto any reasonably powerful platform has, in my experience, been faster than recent Ubuntu versions on the same hardware. Faster to boot. Faster to launch applications. Faster to respond to UI input.

I don't use Ubuntu because it's lightning fast. It isn't. I use it because it's closer to being what I want overall from an operating system. It's much more customizable in just about every sense of that word. For instance, you have to "break" Vista to get the kinds of logon screen configuration options available for the asking in Ubuntu.

And Ubuntu's package management system is a dream. To keep a Windows system with a bunch of third party applications completely up-to-date, you have to jump through some hoops.

It makes sense to optimize your installation of Ubuntu so that it is responsive. But this isn't a drag race.

By the way, much of that "feeling" of being faster was deliberately built into Vista. Microsoft spent tons of money to get the perception of speed. Some of it is real, and some of it is illusion. I think it's a heck of an operating system, but I don't run it or any of its Windows brethren on any of my personal systems. There's nothing like having real access to control of the system's functionality. And, in Windows, you only get what Microsoft wants you to have. That can be good, or it can be bad. I like Ubuntu.

Just another opinion by someone who like to sniff the flowers along the way.

;)

---

### Post by bsta520 on 2009-04-03
good answer thanks for that perspective...now does anyone know why i have to press and hold a key for the ubuntu loading bar to move? if i dont press anything it will stop loading?  why?

---

### Post by pg-13(prostitute) on 2009-04-03
pretty sure you get better performance in linux, since SGI is using redhat now which is causing 90% of hollywood to boot linux for film/visual effects.

soon there will be a better selection of gfx software out for linux, which im sure you will have to license.

---

### Post by michaelzap on 2009-04-03
> **bsta520 said:**
> good answer thanks for that perspective...now does anyone know why i have to press and hold a key for the ubuntu loading bar to move? if i dont press anything it will stop loading?  why?

Could it be that your keyboard is malfunctioning?

---

### Post by bodhi.zazen on 2009-04-03
Moved to recurring discussions for what should be obvious reasons.

If you would like assistance please start a thread with a title less likely to attract trolling such as "help speed up ubuntu" rather then evoking a ubuntu vs windows thread.

---

