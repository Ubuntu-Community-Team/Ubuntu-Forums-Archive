---
title: "[SOLVED] [bash] capitalize text"
date: 2008-09-12
forum: Programming Talk
---

### Post by tr333 on 2008-09-12
How can i capitalize text from within a bash script?

---

### Post by ghostdog74 on 2008-09-12
2 ways
1) you can use tr
```

echo $word | tr [a-z] [A-Z]

```
or
2) use toupper() function of awk
```

# echo $word | awk '{print toupper($0)}'
WORD

```

---

### Post by tr333 on 2008-09-13
Thanks!

---

