---
title: "Finding out why a package was installed (using aptitude)"
date: 2011-06-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2011-06-13
I use **aptitude** all the time, but just happened to read about this. Here's the example I chose:

```
paul@oneiric:~$ **aptitude why** lightdm-greeter-example-gtk
i   lightdm                     Recommends lightdm-greeter
i   lightdm-greeter-example-gtk Provides   lightdm-greeter
paul@oneiric:~$
```

They do say you learn something new every day...

---

### Post by useResa on 2011-06-14
Thanks! Also I did learn something new today. :D

---

### Post by ranch hand on 2011-06-15
Try "aptitude why-not <package>" sometime.

---

### Post by paul_in_london on 2011-06-15
> **ranch hand said:**
> Try "aptitude why-not <package>" sometime.

Thanks **ranch hand** - I should probably have mentioned that as well.

---

### Post by seeker5528 on 2011-06-16
> **ranch hand said:**
> Try "aptitude why-not <package>" sometime.

Guess now we need "aptitude why-wHY-WHYYYY!!! <package>" ;)

Later, Seeker

---

### Post by ranch hand on 2011-06-16
Or;
aptitude wtf <package>

---

### Post by silex89 on 2011-06-16
> **ranch hand said:**
> Or;
aptitude wtf <package>


Hahaha! :D

---

