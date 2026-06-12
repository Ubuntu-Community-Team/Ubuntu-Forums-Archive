---
title: "[SOLVED] Is 3 gigs of ram enough to run the 64-bit version of Hardy Heron"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by liquidphilosopher on 2008-07-22
I am buying a new laptop and wasn't sure if it met the requirements for the 64-bit version... Thank you!

- HP Pavilion dv6700t Special Edition CTO
- Genuine Windows Vista Home Premium with Service Pack 1 (32-bit)
- Intel(R) Core(TM) 2 Duo Processor T8300 (2.40GHz)
- 15.4" diagonal WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
- 3GB DDR2 System Memory (2 Dimm) 2GB DDR2 System Memory (2 Dimm)
- 256MB NVIDIA GeForce 8400M GS - For Core 2 Duo Processors
- HP Imprint Finish (Influx) + Microphone + Fingerprint Reader + Webcam
- Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
- 250GB 5400RPM SATA Hard Drive
- LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
- HP ExpressCard Digital/Analog TV Tuner
- 12 Cell Lithium Ion Battery

---

### Post by steveneddy on 2008-07-22
Yes - no problem.

---

### Post by Joeb454 on 2008-07-22
More than :)

RAM isn't a requirement to run a 64 bit OS - only a 64 bit CPU is required ;)

You could still run the 32 bit version if you wanted to of course :)

---

### Post by Vakman on 2008-07-22
Yes, easily. I run it with less.

---

### Post by scragar on 2008-07-22
I used to run it with 386MB, I still remember those old days. * gazes off into the distance *

Sorry, what was I saying?

---

### Post by liquidphilosopher on 2008-07-22
Wow! That was fast... Thank you all for your prompt reply, you have put my worries to rest. Thanx!

---

### Post by saratchandra on 2008-07-22
I used it on 256 mb, 768 mb and current on 2gb systems without problems.

---

### Post by stmiller on 2008-07-22
The only requirement is.... a 64bit cpu. :)

---

### Post by scragar on 2008-07-22
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

64MB min ram, but 380+ is recomended.

---

### Post by YaroMan86 on 2008-07-22
I used to run 64-bit Feisty/Gutsy on 512 MiB. 

Now I run Hardy on 1.5 GiB.

RAM is not something you need to worry about when it comed to word length.

---

### Post by pi.boy.travis on 2008-07-22
This is not my thread, but I have a really quick question.  Is there a command I can run to find out if I have a 32bit or 64bit processor?  

Thanks!

---

### Post by Flyingjester on 2008-07-22
oh yea, you're good to go buddy

---

### Post by tuxxy on 2008-07-22
> This is not my thread, but I have a really quick question. Is there a command I can run to find out if I have a 32bit or 64bit processor?

Thanks!

Applications > System Tools > Sysinfo

and yes 3 GIG is more than enough to run 64bit, mine boots up running 350MB :)

---

### Post by pi.boy.travis on 2008-07-22
Thanks!

---

### Post by Joeb454 on 2008-07-22
> **pi.boy.travis said:**
> This is not my thread, but I have a really quick question.  Is there a command I can run to find out if I have a 32bit or 64bit processor?  

Thanks!

From a terminal - ```
uname -m
``` It would return x86_64 if you're running 64 bit :)

---

### Post by YaroMan86 on 2008-07-22
Well, the question wasn't if he was running a 64-bit Ubuntu, but if his processor was 64-bit.

---

### Post by kdb424 on 2008-07-22
I have and still am running ubuntu on som somplete POS PC's and it runs great. Better than windws ever could. I tested.

---

### Post by YaroMan86 on 2008-07-22
> **kdb424 said:**
> I have and still am running ubuntu on som somplete POS PC's and it runs great. Better than windws ever could. I tested.

That's great! I'm glad for you and how Ubuntu is working out for you.

---

### Post by stmiller on 2008-07-23
Core 2 Duos, 'Athlon 64', AMD X2 are 64bit. 

Core Duo, Celeron, anything Pentium, etc are 32bit.

```

cat /proc/cpuinfo

```

---

