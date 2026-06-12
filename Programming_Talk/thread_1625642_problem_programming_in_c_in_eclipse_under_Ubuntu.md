---
title: "problem programming in c in eclipse under Ubuntu"
date: 2010-11-19
forum: Programming Talk
---

### Post by nir2000 on 2010-11-19
Hi everybody!
I have just started using Eclipse for programming in c, after using it for Java.
Unfortunately with no help. When I try to compile a simple program, after I installed the environment for c\c++ , I get the message "Launch failed. Binary not found" whenever I try to compile a simple program. 
Please if somebody knows the solution to this problem let me know.
Thank in advance
Nir

---

### Post by spjackson on 2010-11-19
> **nir2000 said:**
> I have just started using Eclipse for programming in c, after using it for Java.
Unfortunately with no help. When I try to compile a simple program, after I installed the environment for c\c++ , I get the message "Launch failed. Binary not found" whenever I try to compile a simple program. 

Here's an old thread that answers your question. Coincidentally it was resurrected yesterday. [http://ubuntuforums.org/showthread.php?t=983597](http://ubuntuforums.org/showthread.php?t=983597)

---

### Post by nir2000 on 2010-11-20
it did not help.
sorry

---

### Post by GregBrannon on 2010-11-20
Does the source compile and run from the command line or using another IDE like Geany?

---

### Post by Majorix on 2010-11-20
Maybe you should install the whole build-essential package. Try
```
sudo apt-get install build-essential
```

---

### Post by nir2000 on 2010-11-24
Sorry for the trouble, I should have simply chosen "Executable project" in the project opened up window. And that solved the problem.
Nir

---

