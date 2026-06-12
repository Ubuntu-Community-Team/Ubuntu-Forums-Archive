---
title: "Jave question"
date: 2007-03-11
forum: Programming Talk
---

### Post by Mba7eth on 2007-03-11
Hi all , 
Can i run some applets with the same speed on different computers ? 
Or in other words how can i let my applet measure the hosted computer speed and act accourding to the computer speed .

---

### Post by lnostdal on 2007-03-11
here's a tip: do not act according to computer speed "directly" .. act instead according to elapsed time sinse last "checkpoint"

---

### Post by laxmanb on 2007-03-11
yeah... create threads... do a Thread.wait() for different periods of time depending on last checkpoint...

---

### Post by Mba7eth on 2007-03-12
can some one provide me with an example please :) 
just to make thing more clearer I'm running some animations in the applets and i do have a thread  . But i'm using sleep instead of wait ( does it make any different ? ) . one my new computer between each sleep it execute around 300 value from the file input, whereas on the old computer it execute only around 75 value only. Thanx all for your help .

---

### Post by Mba7eth on 2007-03-12
[COLOR="Red"]Spelling Corrections : [/COLOR]
can some one provide me with an example please  
just to make thing more clearer I'm running some animations in the applets and i do have a thread . But i'm using sleep instead of wait ( does it make any difference ? ) . on my new computer between each sleep it execute around 300 value from the file input, whereas on the old computer it execute only around 75 value only. Thanx all for your help .

---

### Post by pmasiar on 2007-03-12
[sleep](http://java.sun.com/docs/books/tutorial/essential/concurrency/sleep.html) suspend execution for a specified period (with example). Top hit when searching for [http://www.google.com/search?q=java+sleep](http://www.google.com/search?q=java+sleep) - google is your friend

---

### Post by Mba7eth on 2007-03-12
pmasiar I really appreciate ur help :) 
I just wanted an example on the last check point issue .... and if it is better to use wait instead of sleep

---

### Post by mbeierl on 2007-03-20
The Swing class Timer is usually used to perform updates to animations.  Please do not forget that the update of the animation itself requires cpu power, so you might get slower rates on a slower computer.  The timer class itself can coalesce events (merge two into one) to compensate for this effect on slower computers.

See:  [http://java.sun.com/j2se/1.5.0/docs/api/javax/swing/Timer.html](http://java.sun.com/j2se/1.5.0/docs/api/javax/swing/Timer.html)

---

### Post by thelinuxguy on 2007-03-20
> **Mba7eth said:**
> [COLOR="Red"]Spelling Corrections : [/COLOR]
just to make thing more clearer I'm running some animations in the applets and i do have a thread . But i'm using sleep instead of wait ( does it make any difference ? ) . on my new computer between each sleep it execute around 300 value from the file input, whereas on the old computer it execute only around 75 value only. Thanx all for your help .

You have referred to some input processing from a file. But if you are talking about the animation speed being different on different machines, then you should be looking at refresh rates and syncing your screen updates with the refresh rate. Using sleep or wait for controlling animation speed is not a very good idea.

I do not have a code sample at the moment but this forum may have what you are looking for: [http://forum.java.sun.com/thread.jspa?threadID=515912&messageID=2458405](http://forum.java.sun.com/thread.jspa?threadID=515912&messageID=2458405)

---

