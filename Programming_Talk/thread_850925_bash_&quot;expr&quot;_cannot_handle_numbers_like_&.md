---
title: "bash: &quot;expr&quot; cannot handle numbers like &quot;0.1&quot;?"
date: 2008-07-06
forum: Programming Talk
---

### Post by jo.angel on 2008-07-06
This has been teasing me for a while now, and I am not a very skilled scripter. 

For a script I need to multiply 2 numbers , which can be smaller than 1.

Example 1:
```
# expr 3 \* 1
# 3           # works fine!
```

Example 2:
```
# expr 3 \* 0.1
# expr: 0.1 is not an argument!     # doesnt work
```

So obviously expr cannot handle numbers , that are not "full"
So what is the alternative? As it is for a script it should possibly use a method functioning with all unix/linux systems

Many thanks in advance!

---

### Post by ghostdog74 on 2008-07-06
expr only does integers
```

# echo "scale=2;2*4.1" | bc
8.2

```

---

### Post by jo.angel on 2008-07-06
Works fine. I have tried with bc before, but didnt get this twist.
Thanks a lot and enjoy your sunday

Greatfully,

Jo Angel

---

