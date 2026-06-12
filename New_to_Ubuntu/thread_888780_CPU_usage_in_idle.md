---
title: "CPU usage in idle"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Chris11 on 2008-08-13
My Sys monitor sows always CPU usage around 40% at idle with no desktop effects and no application running, no mesanger in the background etc.... in the porcess list ther is also no precess that needs the CPU more then a few %... Is that normal? 

I remember using Gutsy it was about 8%. 

Here a screen shot of the monitor. Th spike is when I hit the Print Screen key...

---

### Post by Thingymebob on 2008-08-13
Don't know my Turion 64x2 sits at about 15%Cpu1 & 20%CPU2 with full desktop effects.

---

### Post by Tom--d on 2008-08-13
post a screen shot of top
go in terminal and type top and press enter. post the outcome

---

### Post by Tom--d on 2008-08-13
My cpu's stay around 0 or 1% when idle

---

### Post by cariboo on 2008-08-13
There is a bug in the system monitor that shows higher cpu usage that there actually is. Use htop to show actual cpu usage. Htop is avaliable in the repositories and you can use Ad/Remove Programs, Synaptic Package Manager, and of course the command line to install it.

Jim

---

### Post by Chris11 on 2008-08-13
ok here is a screen shot of htop... 

the CPU idles now between 0.7 and 2%.. as you said it must be the bug in the grafic system monitor that gives out a wrong result.. 

thanks to you both for clarifying the situation

Chris

---

### Post by Tom--d on 2008-08-13
> **Chris11 said:**
> ok here is a screen shot of htop... 

the CPU idles now between 0.7 and 2%.. as you said it must be the bug in the grafic system monitor that gives out a wrong result.. 

thanks to you both for clarifying the situation

Chris

No problem :)
Yeah, I never use the System monitor to monitor my CPU, Conky does that :P).
its good for memory usage and other things tho :)

---

### Post by Sinkingships7 on 2008-08-13
There's no bug that I know of. The problem seems to be that the system monitor actually takes processing power to draw the graphs. Using top will get you a more accurate result, because the system monitor won't already be sucking up a quarter of your CPU.

---

