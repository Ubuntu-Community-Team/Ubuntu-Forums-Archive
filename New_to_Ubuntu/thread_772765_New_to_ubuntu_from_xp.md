---
title: "New to ubuntu from xp"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mangalo on 2008-04-28
Hi,
I just installed ubuntu 8.04 on my ibm T42 laptop through wubi.  I have a couple of question i want to ask:
1. Why does my cpu constantly load at 20%+ in system monitor even though I don't run any program? Is there a way to fix this?
2. I installed Envy and run it to update the ati 9600 mobile graphic driver but how do I check to see it's working correctly.

I tried to play a youtube music video but that taking up all my cpu resource and slow it down.  what can I do?

Appreciated for all your help.

---

### Post by f37u5g0d on 2008-04-28
What kind of specs is your computer?  Sometimes just watching the graphs in the system monitor can suck up alot of CPU especially if the refresh rate is high and you have an older/slower computer.  More importantly check the processes tab to see what is actually using your CPU.  I find that more of the names make sense in ubuntu on the process menu then they did in xp.  As for envy.  I have no idea lol.

---

### Post by forrestcupp on 2008-04-28
Open a terminal and type
```
 glxinfo | grep direct
```
If it says yes, then your Envy installed drivers are working.  You should be able to type
```
glxgears
```And it should open a window with gears that spin smoothly.

---

