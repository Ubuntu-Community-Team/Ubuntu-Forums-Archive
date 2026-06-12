---
title: "getchar putchar problem"
date: 2009-07-15
forum: Programming Talk
---

### Post by freeburn on 2009-07-15
gcc can not recognise getchar, but stdio is included. in compilation it does not report any problem but during debugging getchar is not called at all. in my netbeans ide it gives a redmarking saying that unresolved identifier problem. and it does not nevigate to the header file. what should i do?

---

### Post by lisati on 2009-07-15
Do you have build-essential installed?
```
sudo apt-get install build-essential
```

---

