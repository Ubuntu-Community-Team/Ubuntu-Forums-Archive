---
title: "desktop effects cannot be enabled"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-03
Hello,

I have just set up Ubuntu 8.04 with Wubi and when I try to setup desktop effects it tells me desktop effects cannot be enabled.

I have an old GEFORCE2 card and can change to higher resolutions with no problem. I have set up the proprietary driver for nvidia and things I have tried so far seem to work except the desktop effects thingy. Your help appreciated.

---

### Post by nerdman978 on 2008-05-03
if you have the drivers installed, then the problem lies in the age of your graphics card. The desktop effects feature is usually only to be employed on newer hardware.

---

### Post by wordmaster on 2008-05-03
The card is about 2-3 years old. Too ancient?

---

### Post by lazyart on 2008-05-03
A GeForce2 is much older than two years.  At least the architecture is.

---

### Post by Helios38 on 2008-05-03
yes. the effectiveness of compiz depends on the shape of your gfx card (or chip)



rather old gfx cannot run compiz well or at all. i suggest with that hardware you stick to metacity.

---

### Post by wordmaster on 2008-05-04
Thank all of you.

---

### Post by TheMemphisExperience on 2008-05-04
Using Linux Ubuntu 7.10 and 8.04, I was able to run Compiz-Fusion on a Dell Optiplex 260 using the integrated graphics card. The zoom and water effects would not work, but most everything else did. Desktop effects could not be enabled on my laptop under 7.10, but in 8.04, they work just fine. Again, this is using the integrated Intel card.

Dell Optiplex
Pentium 4 2.0GHz
512 Kb ram
IDE HDD 15GB
(S?)ATA HDD 40GB

Acer Aspire 5920
Intel Centrino Duo 1.5x2
2 GB RAM
SATA HDD 200GB

---

### Post by ucal on 2008-05-04
Would an ATI 1270 Integrated card work?

---

### Post by TheMemphisExperience on 2008-05-04
> **ucal said:**
> Would an ATI 1270 Integrated card work?

That, I wouldn't know since I've got no experience with them. You could try to enable the effects using the ATI card and pray they work. Using my integrated Intels, all I had to do was install Compiz-Fusion or choose my flavor of graphical effects from a list menu to enable advanced effects.

Although this was not true for my laptop's card until Ubuntu 8.04.

---

### Post by ucal on 2008-05-04
Thanks.  I'll try it.  I figure if the thing can barely run Oblivion, then it should be able to run desktop effects nice enough.

---

### Post by dennismk on 2008-05-27
> **ucal said:**
> Would an ATI 1270 Integrated card work?

Yes, it works. But you need to enable ATI proprietary driver (somewhere in System, Administration, ...)

---

