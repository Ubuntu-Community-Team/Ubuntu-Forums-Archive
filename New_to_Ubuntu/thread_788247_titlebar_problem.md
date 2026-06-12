---
title: "titlebar problem"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Abu Noor-Eddin on 2008-05-09
Hi all, 

I am upgraded Ubuntu 7.10 from 7.04 on my hp 530 notebook. After finishing, I noticed that all windows titlebar disappeared. 

I am feeling that it is a graphic card problem. Any one can help me? 

Thanks in advance.

---

### Post by hotchkikr on 2008-05-09
yep it probably is, check those drivers first. Then try turning off the effects in the "appearance" menu. that should make them come back

---

### Post by Abu Noor-Eddin on 2008-05-09
> **hotchkikr said:**
> yep it probably is, check those drivers first. Then try turning off the effects in the "appearance" menu. that should make them come back

Please tell me how to check drivers as I am new to linux/ubuntu

---

### Post by SunnyRabbiera on 2008-05-09
something might have got messed up with compositing, have you tried to turn the effects off?

---

### Post by hotchkikr on 2008-05-09
if you don't know about the drivers it's fine, you didn't install them

if you can, could you look in your specs and tell us what your graphics card/chip is and we might be able to see what it is.

---

### Post by Abu Noor-Eddin on 2008-05-09
> **SunnyRabbiera said:**
> something might have got messed up with compositing, have you tried to turn the effects off?

3D desktop disappeared from preference menu !!

---

### Post by SunnyRabbiera on 2008-05-09
> **Abu Noor-Eddin said:**
> 3D desktop disappeared from preference menu !!

alright, have you tried the appearance application?
it might be there to turn off effects.

---

### Post by Abu Noor-Eddin on 2008-05-09
> **hotchkikr said:**
> if you don't know about the drivers it's fine, you didn't install them

if you can, could you look in your specs and tell us what your graphics card/chip is and we might be able to see what it is.

I installed 915resolution to adjust my resolution once before. My graphic card is Intel chipset family

---

### Post by hotchkikr on 2008-05-09
it should be in the "appearence" menu in preferences

ok try this -> 
```
metacity --replace
```
in your terminal

---

### Post by Abu Noor-Eddin on 2008-05-09
> **SunnyRabbiera said:**
> alright, have you tried the appearance application?
it might be there to turn off effects.

It works when I turned them off. Thank you.

---

