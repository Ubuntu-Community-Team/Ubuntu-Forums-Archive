---
title: "defaulting input"
date: 2011-05-08
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-08
When I a = input("how many") how can I default it to 1 if the user enters a word instead of a number?

---

### Post by Tony Flury on 2011-05-09
which language ?

If it was python I would use isdigit 

```

a = input("How Many")
if NOT a.isdigit():
    a = 1

```
isdigit checks that every character is a number

Note - the above wont work with decimal points.

---

### Post by ki4jgt on 2011-05-09
exactly what I needed thanks.

---

