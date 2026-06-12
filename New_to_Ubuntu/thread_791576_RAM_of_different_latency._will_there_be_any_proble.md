---
title: "RAM of different latency. will there be any problems?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by sharks on 2008-05-12
I have 2 rams of CL4 and CL5.will it affect the mobo?

---

### Post by kansasnoob on 2008-05-12
It can. A lot of it depends on the BIOS. For instance on one of my machines I have a Via PC2500E mobo and I was able to adjust BIOS settings to allow me to use one stick 533mhz DDR2 and another stick 667mhz DDR2, which obviously had different latency rates.

I think the BIOS settings included one specific setting of 2.5 to 5 or something like that. Anyway, it works fine there, but I've trying mixing RAM in other mobos and had major problems, such as slowing the FSB down to a crawl.

---

### Post by sharks on 2008-05-12
where in the bios should i adjust?

---

### Post by shifty_powers on 2008-05-12
> **kansasnoob said:**
> It can. A lot of it depends on the BIOS. For instance on one of my machines I have a Via PC2500E mobo and I was able to adjust BIOS settings to allow me to use one stick 533mhz DDR2 and another stick 667mhz DDR2, which obviously had different latency rates.

I think the BIOS settings included one specific setting of 2.5 to 5 or something like that. Anyway, it works fine there, but I've trying mixing RAM in other mobos and had major problems, such as slowing the FSB down to a crawl.

you're getting a bit confused there.

the general cas timings are distinct and separate from the speed of the fsb that the ram operates at.

basically, as long as they are both rated at the same speed, eg ddr2-533, then the difference in latency rates should not make any probs, and the motherboard will run them without problem.

in fact i have been running two sticks with different cas timings for years ;)

edit: you shouldn't have to touch the bios, don't worry ;)

---

### Post by sharks on 2008-05-12
i have a mobo with 533mhz fsb running 2 different ram of 533 and 667 mhz of different latency

---

### Post by BDNiner on 2008-05-12
And if they are running at different speeds then they should run at the speed of the slowest chip. so if you have 1 533MHz chip and one 667MHz chip then both chips should run at 533MHz.But i would not recommend this setup. You should run chips that have the same speed, difference in latency is not important.

---

### Post by shifty_powers on 2008-05-12
well, tbh, that still shouldn't be a problem. in any modern, (i.e. of the last 3/4 years), the 667mhz ram will just default to running at 533mhz ram.

---

### Post by superotakuman on 2009-12-31
Now what if the cas timing of one is 4,4,4,8 and the other is 2.5,4,4,8 will I have any problems? Just wanted to know, don't see how I would have problems, I just wanted some assurance.

---

