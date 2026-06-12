---
title: "HDMI sound"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by mushroom08 on 2012-04-19
Hi im running ubuntu 10.10 i recently got a HDMI cable for my plasma tv i want to watch movies and youtube from my comp on it but i am not getting sound from my tv is there a fix for this my laptop speakers are not that great thx

---

### Post by 2F4U on 2012-04-19
If you enter

aplay -l

do you see your HDMI sound card?

---

### Post by kc1di on 2012-04-19
could you tell us what sound card your using?

---

### Post by mikaelcrocker on 2012-04-19
you can also `lspci` and see if an nvidia or amd sound device is present.  Also going into the command line with `alsamixer` to see things there too and fiddle with the settings may help as well

---

### Post by mushroom08 on 2012-04-19
Thx all it was muted ](*,)

---

