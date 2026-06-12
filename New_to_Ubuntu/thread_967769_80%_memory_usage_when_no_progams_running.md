---
title: "80% memory usage when no progams running"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by elliah on 2008-11-02
im running xunbuntu 8.10 on an IBM thinkpad X30 with 256mb ram. when i open system monitor i see that memory usage hovers at around 80% even though i'm not running any programs. when i check processes, a brief sum up of all the processes' memory doesn't even come close to 180mb(80%). what is eating up my ram?

---

### Post by diablo75 on 2008-11-02
Um.... Ubuntu itself?  You can't expect Ubuntu to not use up some RAM.

---

### Post by gjoellee on 2008-11-02
Will you do not have a lot of ram, it is just as much RAM Xubuntu is using, if you want lower RAM usage you should try out Fluxbuntu

---

### Post by Sef on 2008-11-02
GNU/Linux keeps the ram in memory, and releases it when it needs to be used.  

This is what mine looks like

>              total       used       free     shared    buffers     cached
Mem:          2007       1006       1001          0         39        369
-/+ buffers/cache:        597       1410
Swap:          964          0        964


Type in free -m in your terminal and let us see what yours is.

---

### Post by diablo75 on 2008-11-02
Right, as Sef points out, a portion of memory is actually being used by the OS and applications, while another portion is being used as cache, which actually makes your system run a little faster (depending on your usage habits).

---

### Post by elliah on 2008-11-03
total       used       free     shared    buffers     cached
Mem:     240        236          3          0          0         38
-/+ buffers/cache:  197         42
Swap:    705          8        697

that's what i got when i typed free -m

---

### Post by earthpigg on 2008-11-03
> GNU/Linux keeps the ram in memory, and releases it when it needs to be used. 

how come people always say that.... but i generally see my ubuntu install take up ~350 megs to start with, then more and more gets used as i have more and more open/going on?

is it a flat number, not a %, that is used?

---

### Post by snowpine on 2008-11-03
> **earthpigg said:**
> how come people always say that.... but i generally see my ubuntu install take up ~350 megs to start with, then more and more gets used as i have more and more open/going on?

is it a flat number, not a %, that is used?

It varies from computer to computer; if you have lots of ram, Ubuntu will use it. :)

---

### Post by khelben1979 on 2008-11-03
> **snowpine said:**
> It varies from computer to computer; if you have lots of ram, Ubuntu will use it. :)

Exactly. 

A linux system doesn't use the RAM in the same way as MS Windows does as I have understood it (correct me if I'm wrong).

---

### Post by earthpigg on 2008-11-03
> **snowpine said:**
> It varies from computer to computer; if you have lots of ram, Ubuntu will use it. :)

i have 4 gigs, and both on my 8.04 install and on my fresh 8.10 install the gnome gui system monitor always has the vast majority of it listed as available.

after a week or so it'll be up to 2-3 gigs used (firefox history, pidgin history, memmory leaks from games, etc) and i ctrl+alt+backspace to restart x and its back down to nearly nothing used.

(i got 37 days uptime doing that a few months back lol)

---

