---
title: "How to increase allocated virtual ram"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by cheddarva on 2011-09-30
Hi, I'm kinda a noob still, but I'm trying to speed up my older computer.

I'm currently running Ubuntu 10.04 (64 bit) and I want to increase the ammount of virtual ram (or at least toy with it) to see if I can get my machine to run faster.

I'm assuming it uses virtual ram similar to windows (which I'm fairly familiar with). I know in windows how to do it, and know that it can greatly effect performance of the overall system (from experience)...

I just can't figure out how/where to edit the value ubuntu is set to use as virtual ram...

help please :)

---

### Post by wildmanne39 on 2011-09-30
Hi, welcome to the forum! Ubuntu uses swap space on the hard drive which should have been created when you installed ubuntu, also you can create I swap file which I have never done that and is not needed if you setup swap on your hard drive.
Thank you

---

### Post by kmsalex on 2011-09-30
If you open system monitor next to your ram it should say your swap usage. chances are its already something like 5gb highly dough you need anymore.

---

### Post by dFlyer on 2011-09-30
If you created a swap file when you installed your system, it's either equal to or twice the ram you have installed. You shouldn't need much more. I've got 4 gig of ram and have never used my swap. I mainly use the computer for photo processing and not large db's. If you want to speed up your computer add more ram, not swap space.

---

### Post by cheddarva on 2011-09-30
(slaps forehead) Thanks so much, that makes sense :) I'm running with 4.5 gb for swap... that's gotta be plenty

---

### Post by wildmanne39 on 2011-09-30
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by bodhi.zazen on 2011-09-30
swap does not increase the speed of your computer, it is at least 100 x slower then ram.

What is the output of ```
free -m
```

Linux uses ram fairly different then windows

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

---

### Post by cheddarva on 2011-10-01
total       used       free     shared    buffers     cached
Mem:          2512       1454       1058          0        180        384
-/+ buffers/cache:        889       1623
Swap:         4282          0       4282

---

### Post by wildmanne39 on 2011-10-01
Hi, your information looks good you do not need to do anything to your swap file,you have plenty of free memory, and the links provided has good information on swapiness and memory.

As stated you do not want to use the swap as long as you have ram available because it will be much slower.
Thank you

---

### Post by cheddarva on 2011-10-01
right right... thanks again :)

---

