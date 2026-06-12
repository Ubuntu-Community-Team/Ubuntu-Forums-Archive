---
title: "[SOLVED] Bash while loops with no commands"
date: 2008-07-30
forum: Programming Talk
---

### Post by lavinog on 2008-07-30
I am wondering if there is a way to get a bash while loop to loop without any commands between do and done, or is there some sort of dummy command that isn't evaluated.
The best I can come up with is to use true (see below example)

```

time $(count=50000;while [ $count -gt 0 ]; do let --count; done)
real	0m1.735s
user	0m1.692s
sys	0m0.040s

time $(count=50000;while [ $[ count-- ] -gt 0 ]; do continue; done)

real	0m1.768s
user	0m1.716s
sys	0m0.056s


time $(count=50000;while [ $[ count-- ] -gt 0 ]; do true; done)
real	0m1.667s
user	0m1.624s
sys	0m0.048s


```
I know that bash isn't meant for speed, and there are simpler ways to count. I will be using a similar command for getting positions in arrays

---

### Post by tamoneya on 2008-07-30
just put a "sleep" in there.

---

### Post by sisco311 on 2008-07-30
try:> time $(count=50000;while [ $[ count-- ] -gt 0 ]; do **:** ; done)

---

### Post by ghostdog74 on 2008-07-30
> **lavinog said:**
> 
I know that bash isn't meant for speed, and there are simpler ways to count. I will be using a similar command for getting positions in arrays
what exactly are you wanting to do ? describe more clearly.

---

### Post by lavinog on 2008-07-30
Thanks sisco311,
That was exactly what I was looking for.

---

