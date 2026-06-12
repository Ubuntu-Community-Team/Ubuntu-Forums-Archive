---
title: "Monitor not recognised."
date: 2008-10-29
forum: New to Ubuntu
---

### Post by lordbyron on 2008-10-29
Hi. I am running Hardy 8.04 I have intel integrated graphics and since doing the last batch of updates a few days ago. my flat screen LCD is not detected and the maximum screen resolution I am allowed is 1280 X 800. the screen itself says the best results are with 1680 X 1050 @ 60HZ which is what I had it on before. when I go into the screen resolution it says my monitor is unknown, but previously it knew it was a philips. please help. 
cheers
Byron

---

### Post by overdrank on 2008-10-29
> **lordbyron said:**
> Hi. I am running Hardy 8.04 I have intel integrated graphics and since doing the last batch of updates a few days ago. my flat screen LCD is not detected and the maximum screen resolution I am allowed is 1280 X 800. the screen itself says the best results are with 1680 X 1050 @ 60HZ which is what I had it on before. when I go into the screen resolution it says my monitor is unknown, but previously it knew it was a philips. please help. 
cheers
Byron

Hi and you may try and use the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and adjust you monitor there.

---

### Post by bubba_169 on 2008-10-29
Its situations like this that make you realise taking this tool out of Intrepid was NOT a good idea ](*,)

---

### Post by overdrank on 2008-10-29
> **bubba_169 said:**
> Its situations like this that make you realise taking this tool out of Intrepid was NOT a good idea ](*,)

Well I may agree but I have not had that much of a issue installing and using Intrepid without it. :)

---

### Post by philinux on 2008-10-29
> **lordbyron said:**
> Hi. I am running Hardy 8.04 I have intel integrated graphics and since doing the last batch of updates a few days ago. my flat screen LCD is not detected and the maximum screen resolution I am allowed is 1280 X 800. the screen itself says the best results are with 1680 X 1050 @ 60HZ which is what I had it on before. when I go into the screen resolution it says my monitor is unknown, but previously it knew it was a philips. please help. 
cheers
Byron

Check whats in System>Admin>Hardware drivers. Post back with what you got

---

### Post by lordbyron on 2008-10-29
Hi. I tried gksu displayconfig-gtk but the generic monitor doesn't work and the philips monitors don't have a 22 inch monitor on the list. I also checked the system>admin>hardware drivers and I don't have any in use on the system.is there anything else I can do?

---

