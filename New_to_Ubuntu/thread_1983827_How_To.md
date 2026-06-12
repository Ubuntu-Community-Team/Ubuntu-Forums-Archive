---
title: "How To?"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by babdah on 2012-05-20
I installed the driver after for ati/amd fglrx that Ubuntu ask now i can not get my system to run normal. When I start it up it just gives me a black screen and does nothing else. I rebooted into recovery from live cd. I am assuming that the driver is the cause because before this i had a perfectly working system. Is there any way to install it from live CD?

---

### Post by Frogs Hair on 2012-05-20
You may be able to remove the driver from TTY or the recovery console if you know the complete name of the driver. I use Nvidia so I don't Know the ATI driver names. 

```
sudo apt-get remove driver name 
``` If you are able remove it then reboot and see if it starts normally.

---

### Post by babdah on 2012-05-20
My apologizes, I should of thought first.  Now how to mark this as solved

---

### Post by alphacrucis2 on 2012-05-20
> **babdah said:**
> My apologizes, I should of thought first.  Now how to mark this as solved

I would always enter the command:

```
sudo aticonfig --initial -f
```

After installing the Catalyst fglrx driver but before rebooting. Supposedly you are not supposed to need to do that these days but I would give it a try anyway.

---

### Post by raja.genupula on 2012-05-20
> **babdah said:**
> My apologizes, I should of thought first.  Now how to mark this as solved
From thread tools you can mark your thread as solved :)

---

