---
title: "VB Question (range of numbers)"
date: 2008-02-01
forum: Programming Talk
---

### Post by dhtseany on 2008-02-01
Hi, my friend is getting hung up on a lesson for school.

How do you define a range of numbers in VB?

Ex:
```

let text_box = "$5.00" if qty_box = **1-5**

```

I know in MySQL what I'm talking about is **(1,5)**

Any suggestions?

Thanks,

Sean

---

### Post by aks44 on 2008-02-01
Wouldn't that do the trick?

```
if (qty >= 1) and (qty <=5) then
    let ...
```

(syntax to be adjusted, it's been sooo much time since I didn't touch VB... but you get the idea)

---

