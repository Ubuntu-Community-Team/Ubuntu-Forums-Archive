---
title: "Slow boot problem"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by freelancer85 on 2008-09-24
When starting Ubuntu booting takes about 2-3 min. It's quite slow. There are no USB devices connected. Screen is black. Does anyone knows what's the problem?

---

### Post by NovaAesa on 2008-09-24
It might be a good idea to post your computer specs so that we know how fast it should be starting up. Also, when you say the screen is black, is it like this for the whole boot process? Do you see anything like a loading bar or a grub menu?

---

### Post by yragrelluf on 2008-09-24
check your startup programs, and in the system bios, check the boot device order. Also, get gtk orphan from synaptic, maybe there is bd libs slowing you down, this will fix them.

---

### Post by freelancer85 on 2008-09-24
> **NovaAesa said:**
> It might be a good idea to post your computer specs so that we know how fast it should be starting up. Also, when you say the screen is black, is it like this for the whole boot process? Do you see anything like a loading bar or a grub menu?

Asus A9Rp Series, Processor Celeron M 1.87 Ghz, 384 RAM, 128 ATI, 60 GB HDD...

Yes it's for the whole process, i do not see any of that...

---

### Post by yragrelluf on 2008-09-24
is it a dual boot system?

---

### Post by freelancer85 on 2008-09-24
> **yragrelluf said:**
> is it a dual boot system?

No it's not dual boot system. One system and one partition.

---

### Post by Tatty on 2008-09-24
Does your monitor go into stand-by mode during boot?

My desktop's monitor used to do that with Gutsy (i think, might have been linuxMCE actually) for some reason.

---

### Post by freelancer85 on 2008-09-24
> **Tatty said:**
> Does your monitor go into stand-by mode during boot?

My desktop's monitor used to do that with Gutsy (i think, might have been linuxMCE actually) for some reason.


I don't know actually. I can hear HDD is working but there's nothing I can se on monitor...

---

### Post by Tatty on 2008-09-24
> **freelancer85 said:**
> I don't know actually. I can hear HDD is working but there's nothing I can se on monitor...

Usually monitors have an led light colour change to indicate wether it is on or in standby mode - does the led light on your monitor change when you finally see something appear during boot?

---

### Post by freelancer85 on 2008-09-24
> **Tatty said:**
> Usually monitors have an led light colour change to indicate wether it is on or in standby mode - does the led light on your monitor change when you finally see something appear during boot?

It's notebook and it doesn't have any light indicator. But screen is black as #000000 :)

---

### Post by freelancer85 on 2008-09-24
I forgot to say that the picture shows up on login.

---

### Post by freelancer85 on 2008-09-24
I'VE FOUND SOLUTION TO MY PROBLEM!

YOU CAN FIND COMPLETE GUIDE HERE:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

THANK YOU EVERYONE!

---

### Post by gjoellee on 2008-09-24
if you are using Hardy Heron this may help a little: [http://www.kshoster.net/?c=tipsandtricks&x=optimizehardy](http://www.kshoster.net/?c=tipsandtricks&x=optimizehardy)

---

