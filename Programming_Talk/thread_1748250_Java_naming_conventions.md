---
title: "Java naming conventions"
date: 2011-05-03
forum: Programming Talk
---

### Post by orrymr on 2011-05-03
Hey guys, I was wondering what it means if a variable name in java begins with an underscore. For example:
```

private MenuItem _closeItem;

```
Does it hold any significance?

---

### Post by rg4w on 2011-05-03
I can't speak for that author, but I often use underscores to visually reinforce things that are only used within a given module, class, or script.  I've seen other code that uses them like that too, so it may be what's going on with that snippet.

---

### Post by simeon87 on 2011-05-03
> **rg4w said:**
> I can't speak for that author, but I often use underscores to visually reinforce things that are only used within a given module, class, or script.  I've seen other code that uses them like that too, so it may be what's going on with that snippet.

This is also the convention in Python. I haven't seen this convention used in Java but it makes sense that it serves the same purpose. There's no inherent meaning to starting a variable in Java with an underscore otherwise.

---

### Post by cgroza on 2011-05-03
camelCaseIsTheJavaConvention.

---

