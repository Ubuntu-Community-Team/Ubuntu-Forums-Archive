---
title: "High CPU utilisation"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by apfx on 2012-09-11
Recently installed and updated latest Ubuntu 12.04.1 LTS 64 bit on a separate partition of my machine running W7.
I noticed immediately that it was not light on resources. Both cores are most of the time above 25%  even though I'm not running any programs. 

Has any one else experienced this ?

---

### Post by mips on 2012-09-11
You need to check which processes are eating cpu cycles

---

### Post by offgridguy on 2012-09-11
> **mips said:**
> You need to check which processes are eating cpu cycles

Is there an easy answer on how to do this?  Thank you.

---

### Post by offgridguy on 2012-09-11
> **apfx said:**
> Recently installed and updated latest Ubuntu 12.04.1 LTS 64 bit on a separate partition of my machine running W7.
I noticed immediately that it was not light on resources. Both cores are most of the time above 25%  even though I'm not running any programs. 

Has any one else experienced this ?

My setup is virtually identical to yours,  where do you find task manager on windows7?
All I could find was task scheduler,
I honestly don't know what the CPU usage is but I suspect it will be high also.

---

### Post by jemofthewest on 2012-09-11
Simply type ```
top
``` into a terminal and you'll get a list of all the processes, and I think the default is sorted by %CPU.  Then either use the kill option inside top, or remember the PID of the process and in another terminal type ```
kill PID
```  If you get permission errors, type ```
sudo !!
``` and enter your password.

Alternatively, another command to list all processes: ```
ps aux
```

For extra credit, read the man pages for top and learn what else you can do or just fiddle with the interface, there is a lot there.

For extra extra credit, install htop.  It has a bunch more options and is much more powerful with a similar interface.

---

### Post by alex2399 on 2012-09-11
That could be caused by the system monitor application itself. If the window is large and thus the graphs, it starts to eat CPU cycles.

---

### Post by mips on 2012-09-11
> **offgridguy said:**
> My setup is virtually identical to yours,  where do you find task manager on windows7?


CTRL-ALT-DELETE will bring you to a new shutdown window where you can also select to open the task manager.

---

### Post by offgridguy on 2012-09-11
jemofthewest;  Thank you for the help, according to this a total of all my cpu  usage,
comes to15.5%,  this is all  new to me, is this average? above? below?
thanks again

---

### Post by apfx on 2012-09-12
> **alex2399 said:**
> That could be caused by the system monitor application itself. If the window is large and thus the graphs, it starts to eat CPU cycles.

Yes, thats probably the culprit.

---

### Post by jemofthewest on 2012-09-13
That's pretty high.  I'd look through the processes and see what is causing that 15% eating up.  A good linux installation should only take 1-5% CPU when idle (no windows up or programs running).

---

