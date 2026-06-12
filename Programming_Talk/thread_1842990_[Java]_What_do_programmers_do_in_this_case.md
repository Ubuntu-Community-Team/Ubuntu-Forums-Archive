---
title: "[Java] What do programmers do in this case?"
date: 2011-09-12
forum: Programming Talk
---

### Post by t1497f35 on 2011-09-12
[SIZE=2]Hi,
Since Java only has signed numbers (byte, short, int) what do programmers do when say they have to create a Java binding to a C API and there's a function that works with "unsigned char" values?

Do they
1) use "short" and waste memory?
2) use "byte" and hope the function will never produce any values above 128?
3) if some other solution - which one?[/SIZE]

---

### Post by Bachstelze on 2011-09-12
Not a Java programmer but unless I need to store millions of values, I would just use an int. If you are really low on memory, check the conversion rules, maybe using a byte could work. But whatever you  do, never assume anything about the return value.

---

### Post by Senesence on 2011-09-12
I would agree with Bachstelze.

Although, if you really need to save up memory:

A byte is still a byte, so if you could just copy the raw bits from unsigned char to java byte, you could store everything in java bytes, but just transforming them to ints when needed:

```

my_int = j_byte
if negative(my_int):
    my_int = abs(my_int) + 128

```

I think that would work.

PS: I'm not a java programmer.

---

