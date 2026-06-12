---
title: "Time on my hands"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by eagle128 on 2012-02-07
Hi again, its along time since i`ve been here, you know how it is busy busy no time and then just after Christmas a had a heart attack so im off work for a while.

 So i thought i`d try linux again. i loaded Ubuntu 10.04 lts  on to my pc (2 hard drives one runs win 7)

I`m having a problem with my processor temp its an AMD ATHLON 7750 KUMA and the core temps rise alarmingly  (by 10 to 15 degrees) when using ubuntu any one got any advice
Cheers eagle128

---

### Post by farrinux on 2012-02-07
would this be a laptop pc or a box?

---

### Post by eagle128 on 2012-02-07
Its my desktop.

 The temp is around 14/20 with win7 it rises to 25/30 degress with ubuntu i use a program called `phenom msr tweaker` to lower the temp on win7 is there a similar linux prog

---

### Post by eagle128 on 2012-02-07
Problem solved i installed ubuntu again the temps dropped

---

### Post by quadproc on 2012-02-07
> **eagle128 said:**
> Problem solved i installed ubuntu again the temps dropped
There was at least one kernel version that had a bug in task scheduling (I believe) where the CPU would spin in a loop and eat lots of power while supposedly being idle.  That version may have been 10.04 so I would suggest checking which version of the Linux OS you have, and searching the web to see if you can find out if that is the version with that problem.  The uname -a command will tell you which version of the OS is in use.

You might want to run the System Monitor for a while to see how busy your CPU(s) is during idle time.

quadproc

---

