---
title: "regexp substute"
date: 2009-11-03
forum: Programming Talk
---

### Post by monkeyking on 2009-11-03
Hi

I got at file that looks something like

[PHP]
adsfasdf [1234132] fdasdf [343434] ...
[/PHP]

I basicly just want to remove everything between (and including) the matching brackets,

Such that

[PHP]
adsfasdf  fdasdf  ...
[/PHP]

I normally just do it like 's/FROM/TO/g', but this is somewhat more complicated, and my regexp is not excatly good.


thanks in advance

---

### Post by diesch on 2009-11-03
```
$ echo 'adsfasdf [1234132] fdasdf [343434] ...'|sed -r -es'/\[[^]]*\]//g'
adsfasdf  fdasdf  ...

```

---

### Post by monkeyking on 2009-11-03
Thanks it works,
so the logic behind this is

\[ Match left bracket

[^]]* Sinkhole until next right bracket

\] Match right bracket

Is this correct?

---

### Post by diesch on 2009-11-03
Yes, it's correct.

---

### Post by ghostdog74 on 2009-11-03
```

$ echo adsfasdf [1234132] fdasdf [343434] | awk -vRS="]" -vFS="[" '{print $1}' ORS=""
adsfasdf  fdasdf



```

---

