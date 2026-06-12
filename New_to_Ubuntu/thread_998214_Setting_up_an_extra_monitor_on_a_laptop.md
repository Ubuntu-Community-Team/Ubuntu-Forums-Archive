---
title: "Setting up an extra monitor on a laptop"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by DSL5 on 2008-11-30
Ok, so I just got an extra monitor and i want to set it up to work with linux.

I went to Screen Resolution and placed the monitors accordingly (the extra one is on the right), but for some reason, it keeps making the extra monitor the primary one. Is there any way to change the primary monitor??

My video card is:

Intel Corporation Mobile 915Gm/GMS/910GML Express Graphics Controller )rev 03)

---

### Post by Diabolis on 2008-12-01
You could try i810switch.
```
sudo apt-get install i810switch
```
then
```
i810switch lcd on
```
or
```
i810switch crt on
```
[http://www16.plala.or.jp/mano-a-mano/i810switch.html](http://www16.plala.or.jp/mano-a-mano/i810switch.html)

---

### Post by DSL5 on 2008-12-01
```
i810switch crt on
``` turned on my second monitor, but it was fuzzy and shakey. I have the second monitor working without it, i just want to make the left screen primary instead of the right screen.

---

