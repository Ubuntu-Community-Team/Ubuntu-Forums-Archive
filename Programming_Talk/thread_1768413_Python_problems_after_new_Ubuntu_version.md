---
title: "Python problems after new Ubuntu version"
date: 2011-05-26
forum: Programming Talk
---

### Post by Zebbeni on 2011-05-26
After I installed the new version of Ubuntu a couple weeks ago, one of my Python programs suddenly started freaking out about float to integer conversions- at least when I try to run it from the ERIC IDE, Pyragua, and others. (I am still trying to get Eclipse to install correctly.) Yet my version of IDLE still runs the program fine.

Does anyone know what might have happened with the install?

---

### Post by NovaAesa on 2011-05-26
It sounds like you are running a different version of Python compared to what you were running before. You can find out your current python version by using the command
```
python --version
```
Do you know what version of python you were using previously?

---

### Post by Zebbeni on 2011-05-26
I'm running Python 2.7, and I don't think it's changed. I guess I'm wondering if there were some libraries that might have gotten messed up with the upgrade. 

I remember it telling me that some pieces of ERIC weren't supported anymore, but does that mean the whole program is just useless?

---

### Post by ziekfiguur on 2011-05-28
The default python version changed from 2.6 to 2.7 with ubuntu 11.04

---

### Post by lavinog on 2011-05-29
Can you post the code that is causing the problem?
It might be a simple fix to get it to be compatible for all versions.

---

