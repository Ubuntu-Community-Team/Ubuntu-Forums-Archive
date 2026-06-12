---
title: "Lingot crashes when I try to change option settings"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by darkworld on 2008-06-22
Just installed hardy after a year with Fiesty - Lingot now crashes - I feel like a beginner all over again! 

start lingot from terminal - starts and runs ok - open options - change a setting and apply - Lingot vanishes.

Terminal reads:
> Unable to open audio device /dev/dsp: Device or resource busy


Anybody got a clue why this is happening - lingot works in Fiesty.

---

### Post by darkworld on 2008-06-22
device or resource busy? 

Well this shouldnt work then but it does! > cat /dev/urandom > /dev/dsp
 surely it should return the same error?

I cant find anything using /dev/dsp ??????

---

