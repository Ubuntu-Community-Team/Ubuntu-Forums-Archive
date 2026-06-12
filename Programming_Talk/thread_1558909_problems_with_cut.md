---
title: "problems with cut"
date: 2010-08-22
forum: Programming Talk
---

### Post by pytheas22 on 2010-08-22
I'm trying to do a simple thing with cut but am having trouble, probably because I'm missing something obvious.

The file *file* contains this line:
```

one two three
```

The command:
```

cut -d ' ' -f 1,2,3 file
```

returns:

```
one two three
```

as expected.  But the command:

cut -d ' ' -f 1,3,2 file

also returns:
```

one two three
```

I want *two* and *three* to be inverted, so that cut returns:
```

one three two
```

Could anyone point out where I'm going wrong.  I'm sure this is a simple, simple thing...

---

### Post by pytheas22 on 2010-08-22
So, that was dumb.  I guess cut doesn't reorder fields.  I need to use awk instead:

```
awk '{print $1,$3,$2}' file
one three two

```

---

