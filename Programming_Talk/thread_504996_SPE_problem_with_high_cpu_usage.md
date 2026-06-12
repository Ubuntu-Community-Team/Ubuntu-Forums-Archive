---
title: "SPE problem with high cpu usage"
date: 2007-07-19
forum: Programming Talk
---

### Post by BeardlessForeigner on 2007-07-19
I installed SPE from the repos and when I run it my CPU usage stays at about 20 or 30 % and my cpu temp climbs steadily. My CPU is only working when the SPE window is not minimized; if I minimize it my CPU drops back to 0%. I have been using vim mostly but would still like to try out SPE. Here is the output when I launch it:
```

SPE v0.8.2.a (c)2003-2005 www.stani.be

If spe fails to start:
 - type "python SPE.py --debug > debug.txt 2>&1" at the command prompt
   (or if you use tcsh: "python SPE.py --debug >& debug.txt")
 - send debug.txt with some info to spe.stani.be[at]gmail.com
 
Blender support disabled (run SPE inside Blender to enable).

Encrypted debugging disabled. 
  If you prefer encrypted debugging, install the "Python Cryptography Toolkit"
  from http://www.amk.ca/python/code/crypto

Launching application...

(python:13440): Gdk-CRITICAL **: gdk_draw_drawable: assertion `src != NULL' failed

```
Has anyone else has experienced this problem or possibly have a suggestion? I don't understand the Gdk-CRITICAL, and the only other error message is the wrong wxpython version, but in synaptic there are no other versions I can downgrade to.

---

### Post by leibowitz on 2007-07-20
So you installed it from the repos, and it doesn't start ?

Did you tried what is proposed.

> python SPE.py --debug > debug.txt 2>&1

The error may be something related to GTK and Python GDK bindings. So you may lack a package but I'm not sure. 

I suppose it's more like a SPE problem needing a newer python binding. What version of python did you try this with ?

---

### Post by pmasiar on 2007-07-20
You may want to ask on dedicated SPE forum: [http://developer.berlios.de/forum/forum.php?forum_id=12695](http://developer.berlios.de/forum/forum.php?forum_id=12695)

---

### Post by BeardlessForeigner on 2007-07-20
> **leibowitz said:**
> So you installed it from the repos, and it doesn't star
t ?
Did you tried what is proposed.
...


It starts up fine. But when I have the SPE window visible on my desktop it takes
 up 30% of my CPU just sitting there doing nothing, and my CPU usage drops to 0 
if I minimize or exit SPE. IThe debug report says the same messages when SPE sta
rts and then doesn't seem to report any errors. 

Edit: While writing this message, I tried turning off compiz fusion, and that ixed the problem. With beryl I also had the problem, so apparently SPE isn't playing well with compositing on my pc. I should have tried this but I haven't heard of this happening to ppl on this forums yet.

---

### Post by prokher on 2008-12-01
Same thing on 8.10 and SPE (set up from repository with aptitude).

Spe version 0.8.4.h
Python version 2.5.2
wxPython version 2.8.8.0

---

### Post by Sorivenul on 2008-12-01
> **prokher said:**
> Spe version 0.8.4.h
Python version 2.5.2
wxPython version 2.8.8.0

Same installed software, no issues here, even after half an hour with the window maximized.

---

### Post by prokher on 2008-12-02
Sorivenul, do you have compiz enabled?

---

### Post by Sorivenul on 2008-12-02
Just the basic desktop effects - results of "ps -A | grep compiz":
>  5575 ?        00:00:00 compiz
 5650 ?        00:00:13 compiz.real
 5779 ?        00:00:00 compiz-decorato

---

