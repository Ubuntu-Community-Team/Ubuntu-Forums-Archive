---
title: "C++ Weird string::npos behavior"
date: 2009-11-25
forum: Programming Talk
---

### Post by patryk77 on 2009-11-25
Hey,

I am having a weird bug when trying to use 

```
if (curPos != string::npos)
```

It never evaluates to true when using the string find functions. The following works:

```
if (curPos != (unsigned int) -1)
```

If I cout << curPos, I get 4294967295 (which I expect as it should be (unsigned int) -1).

If I cout << string::npos, I get 18446744073709551615

Is that simply because I am on a 64-bit platform, and size_t is 64-bits?

Is using (unsigned int) -1 in my comparisons the correct way of dealing with this?

Thanks.

---

### Post by dwhitney67 on 2009-11-25
curPos should not be declared as an unsigned int; it should be declared as a size_t.

---

### Post by MadCow108 on 2009-11-26
unsigned int is only guaranteed to be at least 32 bit wide. So it can be also 32 bit on 64 bit systems.
This means size_t and unsigned int do not have to be equivalent.
thus always use the correct types.

---

