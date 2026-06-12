---
title: "Using bash to print the third word in a line"
date: 2011-03-19
forum: Programming Talk
---

### Post by fasoulas on 2011-03-19
Is there a way to print out the 3rd word of a line found in a file?

Can i do this with grep??

---

### Post by sisco311 on 2011-03-19
awk is probably a better choice:
```
awk '/PATTERN/{print $3}' file
```

---

### Post by fasoulas on 2011-03-19
> **sisco311 said:**
> awk is probably a better choice:
```
awk '/PATTERN/{print $3}' file
```

ok thanks a lot
i did ```
awk '{print $3}' file
``` and it worked

---

