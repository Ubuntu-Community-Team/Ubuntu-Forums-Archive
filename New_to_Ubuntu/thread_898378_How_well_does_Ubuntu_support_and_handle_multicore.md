---
title: "How well does Ubuntu support and handle multicore?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by skymera on 2008-08-23
Hi

Since this day and age a lot of people run new machines with dual core and even quad core processors, but how well does Ubuntu handle them and could it use them more effectively?

I know Windows XP handles them pretty poorly, merely offloading data from the first core to the second to fourth. While Vista is said to support it better, by giving each core a job to do rather than just 1 core which spreads it out.

So how well does Ubuntu support multicore?

---

### Post by fedex1993 on 2008-08-23
From what i know ubuntu use dual core very well. When i fold @ home sometimes it puts all the load on one core instead of both if you have multipule i think ubuntu would scream on it and run really well. I am waiting to get my hands on a 3 to 4 core processor.

---

### Post by JP1990 on 2008-08-23
Intel core 2 quad q6600 runs amazingly fast on Ubuntu and amazingly slow on windows xp home edition inc sp3

---

### Post by bpowell2005 on 2008-08-23
My previous laptop had a dual-core intel chip, and Ubuntu Hardy handled it just find out of the box. Generally, the cores indicated similar loading, but some times I'd see one core maxed out, and the other idling...I'm not sure why that was.

---

### Post by jerome1232 on 2008-08-23
> **bpowell2005 said:**
> My previous laptop had a dual-core intel chip, and Ubuntu Hardy handled it just find out of the box. Generally, the cores indicated similar loading, but some times I'd see one core maxed out, and the other idling...I'm not sure why that was.

You were probably using some program that is single threaded and cpu intensive.

---

### Post by durand on 2008-08-23
Ubuntu handles them very nicely...like most linux distributions. It's all about using multi threaded applications that will actually use multiple cores.

---

### Post by SunnyRabbiera on 2008-08-23
Yeh mutlticore is no issue for Ubuntu or linux in general, in fact most say that linux in general handles multicore PC's better then windows and mac... I believe it.

---

### Post by skymera on 2008-08-24
Is there a way to know if programs are multithreaded before you install them?

Does synaptic say anywhere that the program is or not?

I'd like to install as many multithreaded things as possible to get the most out of Ubuntu.

---

### Post by RSingh on 2008-08-24
from my experience it handles MUCH BETTER.

Running HD on Windows XP side, there is a lot of lag as I have i945 graphic chip and much work is done by cpu.

On ubuntu till this date, there has been no lag on any HD video (720p & 1080p).

---

### Post by durand on 2008-08-24
It's not that easy to know if an application does use multiple threads. You will just need to google. However, many programs are now being designed with multithreadedness in mind so I don't think there will be much reason to know.

I know that the quake 4 engine is multithreaded if you use the right binary. The quake 3 engine is but only if you compile it without sdl (sound). Opera is multithreaded, but ff isn't yet. BOINC projects generally run on a single thread to control how many cores are used by BOINC. 
I can't really think of any other cpu hungry applications at the moment.

---

### Post by katon on 2009-01-17
i have a problem sometimes with FLASH websites , it uses only one processor in 100 %  and the other not using .  I see in Vista is used more effectively. 
i have also de Q6600 quadcore. running intrepid ibex 32bit . 
maybe 64 is better for multicore?

---

