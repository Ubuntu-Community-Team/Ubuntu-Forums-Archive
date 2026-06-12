---
title: "Grep and recursive on multiple files (no results)"
date: 2018-10-09
forum: Programming Talk
---

### Post by oygle on 2018-10-09
When I use **kfind** recursively looking for "remember" on all .TXT files , I get many results (expected). But when I use grep, no results ??

```

grep -i -r 'remember'  *.txt

```

I have also tried -R but still no results. Obviously something dumb I'm doing

---

### Post by mc4man on 2018-10-09
I guess instead of using *.txt use the option
```
 --include="*.txt"
```

---

### Post by oygle on 2018-10-09
> **mc4man said:**
> I guess instead of using *.txt use the option
```
 --include="*.txt"
```

Thanks muchly, that worked fine ..

```
grep -i -R 'remember' --include="*.txt"
```

---

