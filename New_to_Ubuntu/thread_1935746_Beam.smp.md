---
title: "Beam.smp"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by Crossbow on 2012-03-04
Beam.smp: What is it, why is it eating all my CPU, and how do I stop it? 

I'm running 10.04.

---

### Post by Crossbow on 2012-03-04
Okay, I think, I THINK, that I fixed this. 

Browsing the forums I found that beam.smp has something to do with Ubuntu One. I don't use that and no one seams to know what beam.smp is, so I uninstalled everything that said Ubuntu One, except for "vote for you r favorite packages" because it gave me a warning. 

The CPU usage is averaging a lot lower now, but I don't actually know what I've done. Am I going to be OK?

ETA: Nope, didn't fix it. The CPU was down for a while but now it's staying way up all the time.

---

### Post by Crossbow on 2012-03-05
Annnnnd the CPU usage is still hovering between 50% and 100% even though this forum is the only thing I have open.

---

### Post by winh8r on 2012-03-05
Open a terminal and enter 


```
top
```


this will show realtime data on processes running so at least you can see what is hogging the CPU.

---

### Post by Crossbow on 2012-03-06
Well, beam is gone so I guess at least I fixed that. At the moment, 62% of my CPU is being used by launcher.exe and 35% by wineserver. I assume this is because I tried to launch the free download of World of Warcraft. I should probably have known better. I wouldn't run but I can't close it, will have to reboot. 

Another 10% is Xorg. I don't know what that is. I do know that adds up to more than 100%...

---

