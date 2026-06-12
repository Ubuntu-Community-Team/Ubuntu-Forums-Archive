---
title: "goto in bash?"
date: 2010-12-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-12-22
I have some nested loops in a bash script like this:
```

for .....; do
    # loop 1
    for ......; do
        # loop 2
        if [ condition ]; then
            goto continue_loop_1;
        fi
        # do something if condition is not true
    done
    continue_loop_1
done

```
But there is no goto. Is there an alternative way to do it?

---

### Post by MadCow108 on 2010-12-22
just use break to get out of the current loop level.

break N for breaking out N levels

---

### Post by crazyfuturamanoob on 2010-12-22
Oh, didn't remember there was a such command. Thx :D

---

