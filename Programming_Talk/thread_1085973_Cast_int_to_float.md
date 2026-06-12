---
title: "Cast int to float"
date: 2009-03-03
forum: Programming Talk
---

### Post by roccivic on 2009-03-03
I need to cast an int to float in C and can't figure out how to.
The float variable is actually a gfloat (for use with GTK+) if that's relevant.

Many thanks,
Rouslan.

---

### Post by geirha on 2009-03-03
```

int i=5;
printf("%f\n",(float)i);

```

---

### Post by ibuclaw on 2009-03-03
Yes, what geirha said.

```

int i = 5;
gfloat j = (float)i;

```

Regards
Iain

---

### Post by roccivic on 2009-03-03
Thanks, that sorted it.

---

