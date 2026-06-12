---
title: "Maximium CPU"
date: 2009-04-20
forum: Programming Talk
---

### Post by Lekshmi on 2009-04-20
How to find the maximum number of CPU? Does the system is maintaining any data structure for that? Am writting one driver code,In that how can i get the maximum number of CPU? Which function or variable can help me for this purpose?

---

### Post by jolx on 2009-04-20
> **Lekshmi said:**
> How to find the maximum number of CPU? Does the system is maintaining any data structure for that? Am writting one driver code,In that how can i get the maximum number of CPU? Which function or variable can help me for this purpose?

Hi. I'm sorry but it's a bit hard to understand what you are asking.

---

### Post by cszikszoy on 2009-04-20
```
cat /proc/cpuinfo | grep "processor" -c
```

---

