---
title: "javascript switch question?"
date: 2007-06-15
forum: Programming Talk
---

### Post by RawMustard on 2007-06-15
HI all.

Can some kind heart explain this line of javascript code to me please.
```
FOO = (foo==1) ? 1 : 0;
```

Am I right in thinking FOO will = 1 if foo = 0 and FOO will = 0 if foo = 1??

---

### Post by jespdj on 2007-06-15
> **RawMustard said:**
> Am I right in thinking FOO will = 1 if foo = 0 and FOO will = 0 if foo = 1??

No, the other way around. This will make FOO = 1 if foo = 1, and FOO = 0 if foo = 0. This is the same as:

if (foo == 1)
  FOO = 1
else
  FOO = 0

---

### Post by RawMustard on 2007-06-15
Ah ha!

Thankyou kindly :)

---

### Post by slavik on 2007-06-15
and people say perl is unreadable :P

---

