---
title: "Need a free C++ profiler"
date: 2009-04-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-04-28
That would definitely help optimizing stuff.

---

### Post by Yacoby on 2009-04-28
valgrind might be worth a look. It did OK when I used it.

---

### Post by SledgeHammer_999 on 2009-04-28
use gprof

---

### Post by Sockerdrickan on 2009-04-28
yes gprof seconded

---

### Post by TheOrangePeanut on 2009-04-28
I was also going to recommend gprof

---

### Post by Zugzwang on 2009-04-29
First:
```

valgrind --tool=callgrind ./your_program

```
then:
```

kcachegrind callgrind.out.[PID]

```
For finding out the PID, use "ls". Very helpful.

---

### Post by smudi on 2009-04-29
valgrind definitely

---

