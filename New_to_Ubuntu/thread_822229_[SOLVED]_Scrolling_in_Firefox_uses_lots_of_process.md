---
title: "[SOLVED] Scrolling in Firefox uses lots of processing power"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Beatbreaker on 2008-06-08
I'm using Firefox and I've noticed that when i scroll on some pages (like the length of the "Post New Thread" page on these forums), I get a less than instant reaction from the program.

I also then checked my CPU usage and it shoots up to around 60% just when i'm scrolling. If i'm on a long page it goes even higher. What's happening here? Is it a video driver problem? or is it Firefox 3's issue?

---

### Post by Bachstelze on 2008-06-08
> **Beatbreaker said:**
> Is it a video driver problem?

Most likely, yes. What kind of video card do you have, and do you have proper drivers installed for it?

---

### Post by Beatbreaker on 2008-06-08
I'm using an Nvidia card - not sure what type but it was extra when i bought my Dell Inspiton 1720. I've got compiz fusion working no problems - does that mean that the drivers are ok too?

---

### Post by forger on 2008-06-08
are you using ubuntu hardy heron 8.04?
head to menu system > administration > hardware drivers, make sure your graphics card driver is checked and enabled there

also, in firefox menu edit > preferences > advanced > general > uncheck "enable smooth scrolling"

---

### Post by Bachstelze on 2008-06-08
If Compiz works, yes, your drivers are OK. Do you still have that scrolling problem with Compiz disabled?

---

### Post by Beatbreaker on 2008-06-08
ok here's what i've found:

I've got what appears to be the proper NVIDIA driver "NVIDIA accelerated graphics driver (latest cards) - ticked, green light, in use.

No problems there, the only difference is that i remember that i once installed the Nvidia drivers and i had an Nvidia control panel in the system > preferences area. This time i don't have that, i don't think i should be worried though.

The other thing that i found is that turning off smooth scrolling fixes it a little - apperance wise it seems better and more responsive, in the Processor meter 
it still shoots up around the same area.

I turned off Compiz fusion and when i do scroll now instead of the CPU usage shooting to 70% it goes up around to 30%. But i can't do without Compiz Fusion so i want to know if there is a setting i might have on that is doing that to my scrolling?


actually i did a little more playing, i got Compiz back into gear and i think the usage percentage is lower now - I think it might have been the smooth scrolling option. Thanks forger & all others helping me out on this one

---

