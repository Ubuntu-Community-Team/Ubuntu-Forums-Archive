---
title: "Compiz using almost 50% of CPU"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-10-04
Just noticed that compiz is using up a lot of resource - almost 50% CPU.

anybody else..

---

### Post by ventrical on 2011-10-04
Ok.. I disabled <cube-gears> in compiz and that did the trick .. but- still .. thats a lot of resource ..

---

### Post by madjr on 2011-10-04
unity for me overall feels laggier than in natty, but i dont have the cpu problem

---

### Post by effenberg0x0 on 2011-10-04
Yes, but in my case it was the  new version of flash-plugin amd64 (11.0.1.152) and plugin-container which were eating the cpu. Killing both brought compiz and the total cpu use to standard levels.

Regards,
Effenberg

[B]EDIT:
Running Flash on YouTube
Average CPU usage (No Flash Running)  |        Process       | Average CPU Usage Increase (10 minutes - Flash Running)
[/B]5%                                                           |      /usr/bin/X      | +2%
3%                                                           |        Firefox         | +4%
2%                                                           |        Compiz        | +28%
3%                                                           |  Plugin Container | +19%
**TOTAL=13%**                                                                          [B]TOTAL=53%

Hardware: [/B]AMD Phenom II X6@3.9GHz, 16GB Corsair RAM (1600 @ 8-8-8-24), Nvidia GTS450 1GB**, **ASUS M4A89GTD Pro/USB3

---

### Post by ventrical on 2011-10-04
> **effenberg0x0 said:**
> Yes, but in my case it was the  new version of flash-plugin amd64 (11.0.1.152) and plugin-container which were eating the cpu. Killing both brought compiz and the total cpu use to standard levels.

Regards,
Effenberg

[B]EDIT:
Running Flash on YouTube
Average CPU usage (No Flash Running)  |        Process       | Average CPU Usage Increase (10 minutes - Flash Running)
[/B]5%                                                           |      /usr/bin/X      | +2%
3%                                                           |        Firefox         | +4%
2%                                                           |        Compiz        | +28%
3%                                                           |  Plugin Container | +19%
**TOTAL=13%**                                                                          [B]TOTAL=53%

Hardware: [/B]AMD Phenom II X6@3.9GHz, 16GB Corsair RAM (1600 @ 8-8-8-24), Nvidia GTS450 1GB**, **ASUS M4A89GTD Pro/USB3

  Thats strange indeed. So it's random then.

  Luckily for me, during this beta test process , I happened to have quite a few extra fans in stock so I rigged up a few to keep my CPU extra cool <or otherwise well ventilated>  :) <nvidia card also>

 An old Navy Seal addage .. 'Two is one and one is none !'

:)

---

### Post by ubupirate on 2011-10-04
> **madjr said:**
> unity for me overall feels laggier than in natty, but i dont have the cpu problem

It's the opposite with me, Unity is extremely laggy in 11.04 and works smoothly in 11.10 on same hardware.

And this was with both setups having Sync to VBLANK disabled.

Also, no CPU usage issues at all.

---

