---
title: "Python weird behavior with arrays"
date: 2010-11-05
forum: Programming Talk
---

### Post by nbo10 on 2010-11-05
I have noticed a weired behvior with a piece of code invovling arrays

```

t1 = 0.001
t2 = 0.1 
t3 = 0.5
t4 = 0.001
t5 = 0.25
t = [t1,t2,t3,t4,t5]
W = [1,2,7,8,3,5]

t = t * W[0]

len(t)

```
returns 0 for the length of t. But if I have t = t / W[0] the length returns 5. What is going on here?

---

### Post by DanielWaterworth on 2010-11-05
I ran the code and got 5 in python 2.6.5 and python 3.1.2.

---

### Post by TheWeakSleep on 2010-11-05
I got five as well.

---

### Post by raydeen on 2010-11-05
5 here as well. Python 2.5.1 running on a Mac.

---

