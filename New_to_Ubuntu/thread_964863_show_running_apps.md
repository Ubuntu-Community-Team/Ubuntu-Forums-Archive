---
title: "show running apps"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by poldie on 2008-10-31
Not really all running apps - I know there's a panel thing for that.  I mean when you have pidgin or compiz fusion running there's a little icon near the clock.  I've just installed 8.10 32 bit (because I had too many problems with 64 bit - ie no java in a browser).  But i'm not seeing icons for either of those two apps, so, for example, I click on the compiz fusion icon but i have nothing to right click on to get to the settings manager, reload manager etc.

---

### Post by nothingspecial on 2008-10-31
The command

```
top 
```

Will show you the apps that are using most of your cpu.

```
ps -aux
``` will show you all running processes.

---

### Post by stephanvaningen on 2008-10-31
You can also open System -> Administration -> System Monitor and select the tab 'Process list', it shows similar list to
 ```
ps -ef
```
but easier readable

---

### Post by poldie on 2008-10-31
> **stephanvaningen said:**
> You can also open System -> Administration -> System Monitor and select the tab 'Process list', it shows similar list to
 ```
ps -ef
```
but easier readable

I'm after the icons which are missing from the bottom right of the screen.  Like in Pidgin I used to see a little green circle which flashed when someone was talking to me, and with compiz-fusion it was a smaller version of the fusion icon I could right click on.

Solved:  Turns out I needed to add a panel called the 'notification area' to the taskbar.

---

### Post by hobo89 on 2008-12-08
> **poldie said:**
> Solved:  Turns out I needed to add a panel called the 'notification area' to the taskbar.

I managed to remove it from the panel earlier today without realising. Glad I found this thread, thanks!

---

### Post by Songwind on 2008-12-08
For future reference, if you like GUI tools, the **System->Administration->System Monitor** will show you all the running processes, as well as having some graphs to show you CPU and memory use.

---

