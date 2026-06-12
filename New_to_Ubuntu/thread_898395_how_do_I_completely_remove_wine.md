---
title: "how do I completely remove wine?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Gone fishing on 2008-08-23
How do I completely remove wine? I installed wine and messed it up trying to get MS Access to work. I've removed wine, using complete removal in synaptic and deleting the .wine directory in my home folder,  but if I reinstall wine its still messed up with a broken office install. So how do I completely remove wine and start again?

Also has anyone had reactos running well in Virtual Box?

---

### Post by sharks on 2008-08-23
i think the downloaded package is still in ur system.type:
sudo apt-get clean

and then try reinstalling it.

---

### Post by lukjad on 2008-08-23
Also try:
```
sudo apt-get autoclean
```

---

### Post by talibanned on 2008-08-23
Hey on a related but slightly different topic, I need to remove iTunes but apparantly this can only be done by removing Wine entirely.  Should I just remove wine through synaptic manager or is there a particular set of Terminal instructions for this?

---

### Post by philinux on 2008-08-23
Use 

sudo apt-get purge yourapp

See man apt-get

---

### Post by Gone fishing on 2008-08-23
Well it worked :) reinstalled and this time and office worked, but it can't have purged everything as when wine installed the menu already had all the office 2000 icons as if I'd already installed it?

---

### Post by Gone fishing on 2008-08-23
I suppose the next question is has anyone got Access working properly?

---

