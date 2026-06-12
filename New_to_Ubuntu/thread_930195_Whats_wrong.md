---
title: "Whats wrong?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by AdrenalineJunkie on 2008-09-25
I have installed 8.08 onto my iMac Indigo using the alternate install CD. 

I have made sure that this time the CD was verified before use as this was a problem in a previous install.

welcome to Yaboot....etc

Then the screen goes white, then black and then nothing happens.

What should I do?

---

### Post by neurostu on 2008-09-25
Mac hardware is pretty fickle, especially machines with the older IBM processors. Try posting in the Mac specific section of the forums, you'll be more likely to get informed responses there.

---

### Post by nowshining on 2008-09-25
> **AdrenalineJunkie said:**
> I have installed 8.08 onto my iMac Indigo using the alternate install CD. 

I have made sure that this time the CD was verified before use as this was a problem in a previous install.

welcome to Yaboot....etc

Then the screen goes white, then black and then nothing happens.

What should I do?

do u mean 8.04 or 8.10?? if 8.10 - it's still not deemed stable - the latest stable is hardy ver. 8.04 - ibex 8.10 should be ready and deemed stable at around mid month this october...

---

### Post by jemate18 on 2008-09-25
8.08? I think there is no such....

---

### Post by AdrenalineJunkie on 2008-09-26
Sorry, 8.04.

I have reinstalled it, and now I get this;



Loading, Please Wait...
bogl_init failed: EXPLODE

screen init failed
kinit: name_to_dev_t(/dev/hda4) = hda4(3,4)
kinit: trying to resume from /dev/hda4
kinit: No resume Image, doing normal boot...

Ubuntu 8.04.1 iMac-Indigo ttyl



and then just a prompt to log in.

---

### Post by Sycron on 2008-09-26
it's a terminal login or a graphical login ?

---

### Post by AdrenalineJunkie on 2008-09-26
its giving me a terminal login

---

### Post by billgoldberg on 2008-09-26
> **AdrenalineJunkie said:**
> its giving me a terminal login

try typing 

```
startx
```

and see what it says

---

### Post by Sycron on 2008-09-26
or ```
sudo gdm
```

---

