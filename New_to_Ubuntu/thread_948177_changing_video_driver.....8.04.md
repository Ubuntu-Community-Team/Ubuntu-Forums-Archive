---
title: "changing video driver.....8.04"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-10-15
I have 8.04 installed on my friends computer and want to upgrade the video driver. 7.1 has System>Administration>Screens and Graphics......then you can change the screen and drivers.

I can't find this in 8.04 and I don't know how to get this thing changed!!

---

### Post by Tatty on 2008-10-15
What graphics card do you have?

Generally this is done with either the Hardware Drivers manager in System->Administration, or with EnvyNG which is in the repos.

The Screens and Graphics manager is more designed for getting the correct display settings for your card, rather than for installing new drivers.  However it is still available in Hardy, just not as an icon:

```
displayconfig-gtk
```

I imagine you would have to preface that with gksu, but I am not in hardy atm to check.  Try it without and see if it complains.

---

### Post by chaddiesel on 2008-10-15
Thanks for the help. I'll try that tonight and post any problems that I might have.

I'm running a really old graphics card in there. ATI Radeon AGP DVI is the only information I can get about it. It might now work any better with a driver but I'll give a shot in the dark. :D

---

