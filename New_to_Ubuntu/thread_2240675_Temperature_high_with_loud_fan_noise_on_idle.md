---
title: "Temperature high with loud fan noise on idle?"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by 94jamespark on 2014-08-21
I bought a Dell CS24-SC Server which holds two Intel L5420 Quad-Core Xeon 2.5 GHz.
Recently, I ran a temperature check using 'sensors' and gave me this result:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0°C  (high = +73.0°C, crit = +85.0°C)
Core 1:       +40.0°C  (high = +73.0°C, crit = +85.0°C)
Core 2:       +45.0°C  (high = +73.0°C, crit = +85.0°C)
Core 3:       +43.0°C  (high = +73.0°C, crit = +85.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +46.0°C  (high = +73.0°C, crit = +85.0°C)
Core 1:       +39.0°C  (high = +73.0°C, crit = +85.0°C)
Core 2:       +43.0°C  (high = +73.0°C, crit = +85.0°C)
Core 3:       +44.0°C  (high = +73.0°C, crit = +85.0°C)
```
When I place my hand near the server fans, I do not feel any hot air.
I am not sure if the system is detecting the correct temperature, but if so, is this suitable for my server on idle?
Also, the server is quiet loud, so I am looking to remove one fan.

---

### Post by nerdtron on 2014-08-21
Servers are usually loud and 44 Celcius is not high.

From your post high temp should be 70 Celcius and above.

---

### Post by Sanctimonious_Ape on 2014-08-22
> **94jamespark said:**
> 
Also, the server is quiet loud, so I am looking to remove one fan.

Before you go that route, you might want to read [this](http://www.techrepublic.com/article/quiet-noisy-computer-fans-with-a-drop-of-oil/).  I'm guessing the server is used, so it just might need some TLC in order to quiet it down.  We just had a [similar discussion](http://ubuntuforums.org/showthread.php?t=2239648) about this on laptops and I was able to drop my temp significantly just by thoroughly cleaning the fans and vents.  In a server case that's much easier and you've probably already done that.  What I didn't post in that thread was that I went back in to my laptop again later and added the lubricating oil to the fan - it runs much more quietly now and the temp has dropped even a few more degrees.

---

### Post by tgalati4 on 2014-08-23
Dell server's BIOS will spin up fans if it detects underspin in one fan.  So if a fan is supposed to be 3300 rpm but only reaches 2800 rpm, the BIOS will rev to 6500 to let you know that you have a sluggish fan.

Server's are generally loud regardless.

---

