---
title: "help with limewire"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by den carter on 2008-05-21
i was trying to install limewire and when i clicked on install ikeeep getting a box popping up that says only one software management tool is allowed to run at the same time.....but nothing else is running as far as i know,ive restarted my computer and tried it again and it did the same thing what can i do about this, thanks

---

### Post by SunnyRabbiera on 2008-05-21
Hmm, well you can check if apt is running in the background by opining up the system monitor located under system> administration listed as system monitor.

I had a issue like this once myself, lets see how this works.

---

### Post by Bodsda on 2008-05-21
This can sometimes happen if apt has hung at some point.

Close any Terminal, Update manager, Add/Remove, Synaptic windows that may be open,the load a terminal and type

```
 killall apt 
``` this will stop any apt process running in the background, if this command just gives you another prompt then it has worked and you should be able to use apt again.

---

### Post by kamitsukai on 2008-05-21
Why do people insist on using limewire? why dont you give the limewire based frostwire app a go? its as fast as the paid version of limewire :)

---

