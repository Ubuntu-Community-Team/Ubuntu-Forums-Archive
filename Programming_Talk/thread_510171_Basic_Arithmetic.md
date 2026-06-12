---
title: "Basic Arithmetic?"
date: 2007-07-26
forum: Programming Talk
---

### Post by MianoSM on 2007-07-26
I'm unable to come up with a script that works at all for this....

What I want to do is have a simple grep go through a file (000000*.log) each day, and search for the word "new", and add up the sum of all of those "new" words.

I tried to do it in bash, but have yet to come up with anything successfully. : (

---

### Post by jyba on 2007-07-26
Can't you just use 'wc -l' or am I misunderstanding the problem?
```
grep "new" 000000*.log | wc -l
```

---

### Post by MianoSM on 2007-07-26
That is exactly what I needed thank you very much. : )

---

### Post by Mr. C. on 2007-07-27
```
grep -c new 000000*.log
```

MrC

---

