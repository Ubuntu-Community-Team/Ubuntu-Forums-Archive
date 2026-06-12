---
title: "help with awk"
date: 2010-11-25
forum: Programming Talk
---

### Post by Drenriza on 2010-11-25
if i do this command
```
ls -lah | awk '{ print $3 $4 $5 }'
```
and get this output
> cristiancristian4,0K
how would i be able to paste spaces into the text so it would stand like
> cristian cristian 4,0K
instead

Thanks on advance.

---

### Post by Arndt on 2010-11-25
> **Drenriza said:**
> if i do this command
```
ls -lah | awk '{ print $3 $4 $5 }'
```
and get this output

how would i be able to paste spaces into the text so it would stand like

instead

Thanks on advance.

If you want spaces, output spaces:

```
ls -lah | awk '{ print $3 " " $4 " " $5 }'
```

---

### Post by DaithiF on 2010-11-25
```
ls -lah | awk '{ printf "%s %s %s\n", $3,$4,$5; }'
```

---

### Post by Drenriza on 2010-11-25
> **Arndt said:**
> If you want spaces, output spaces:

```
ls -lah | awk '{ print $3 " " $4 " " $5 }'
```

Worked as intended :p

Thanks.

---

