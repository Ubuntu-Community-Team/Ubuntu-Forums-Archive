---
title: "Error inserting ramzswap"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MG&amp;TL on 2011-07-19
When booting Oneiric from 'testDrive' , I get the following error:

```
Error inserting ramzswap 
``` Loading screen then loads...and loads...and loads, and does not stop. I have left it for 4 hours and it doesn't load.

I know this is a bug, and therefore should be a launchpad, not forum post issue. (I have already reported this on launchpad)

BUT- I have tried this on several systems (laptop and pc), several operating systems (U-, Xu, and Lu- buntu) and it ALWAYS happens. What gives? :D

The only thing in common with systems is their linux-ness and they all share the same network.

---

### Post by dino99 on 2011-07-19
seems to be related with your ram sticks; if several are plugged, then test with one, then add an other.

---

### Post by MG&amp;TL on 2011-07-19
Ok... I'm using the test drive program. Can I simulate this in the program without physically taking out the sticks (and potentially fudging my pc?)

Thanks for help btw. Thought it was going to be a 'get off this forum message' :D

---

### Post by Quackers on 2011-07-19
I get a similar line during boot sometimes, but booting continues normally.

---

### Post by MG&amp;TL on 2011-07-19
Hmmm...I'l leave it a couple of weeks and try again, see whether it gets sorted out. Thanks guys.

---

### Post by dino99 on 2011-07-20
> **MG&TL said:**
> Ok... I'm using the test drive program. Can I simulate this in the program without physically taking out the sticks (and potentially fudging my pc?)

Thanks for help btw. Thought it was going to be a 'get off this forum message' :D

you have to unplug the stick(s) to test it, and maybe test on a different bank (note that often works by pair like 1-3, 2-4) depends on how many they are.

---

### Post by MeXaN1St on 2011-07-20
This error message is related to the kernel module that creates a compressed swap partition into RAM. This is often used in mobile devices with limited amounts of RAM, so it is pretty nothing to do about "normal" PC's.
Currently, this module seems broken in Oneiric, but mine loads quite well after displaying this error. 
More info: [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)
[https://wiki.edubuntu.org/Compcache](https://wiki.edubuntu.org/Compcache)

---

### Post by mc4man on 2011-07-20
there is this bug report, people there, (2), were using testdrive
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/800447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/800447)

---

### Post by MG&amp;TL on 2011-07-20
Several people now. I was the second poster. :D

Anyway, the pcs I tested it on were both ancient, similar spec to my signature, so that might be the problem. The laptops is new, but it's dual booting, it's  a VAIO, which seem to be occasionally problematic, and it's a laptop. With laptop RAM.

---

