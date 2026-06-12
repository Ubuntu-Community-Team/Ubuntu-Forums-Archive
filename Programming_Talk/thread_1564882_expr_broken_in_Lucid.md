---
title: "expr broken in Lucid?"
date: 2010-08-31
forum: Programming Talk
---

### Post by Fatman_UK on 2010-08-31
Hi all,

Is expr broken?

```
$ expr 2 * 3
expr: syntax error
$ expr 2*3
2*3
$ expr "2 * 3"
2 * 3
$ expr (2 * 3)
bash: syntax error near unexpected token `2'
$ expr \(2 * 3\)
expr: syntax error
$ expr "\(2 * 3\)"
\(2 * 3\)
$ expr \(2 * 3)
bash: syntax error near unexpected token `)'
```

The manpage suggests you can feed a multiplication to expr. Did I miss something?

ps: I already found a workaround for this, which is to use "echo "2 * 3" | bc" instead. I'm just worried that expr is broken.

---

### Post by schauerlich on 2010-08-31
```
schauerlich@inara:~$ expr 3 \* 5
15
```

* is auto-expanded by bash, you have to escape it.

---

### Post by amauk on 2010-08-31
You can also do
```
expr 3 '*' 5
```

from expr man page
> Beware that many operators need to be escaped  or  quoted  for  shells.

---

### Post by ghostdog74 on 2010-08-31
when you need to use decimals/floats in your calculation, call  bc or awk. Otherwise, for simple integer maths you can use bash itself (note ksh supports floats) ,

```

echo $((5*3))

```

---

### Post by Fatman_UK on 2010-08-31
Tried everything except that. Thanks! :D

---

