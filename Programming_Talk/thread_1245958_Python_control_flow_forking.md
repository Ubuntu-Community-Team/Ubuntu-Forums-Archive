---
title: "Python: control flow forking"
date: 2009-08-21
forum: Programming Talk
---

### Post by kumoshk on 2009-08-21
What exactly does it mean when control flow forks (in Python)?

Also, why is this bad in Python?

I know what it sounds like it means, but I'd like a more demonstrative answer so I can think in less abstract terms about it. In what cases can it fork (and how is the fork caused), and what are some workarounds for those cases?

---

### Post by CptPicard on 2009-08-21
Could you give some more context as to where you are coming across this problem? I honestly don't understand what you're talking about... :)

---

### Post by kumoshk on 2009-08-21
> **CptPicard said:**
> Could you give some more context as to where you are coming across this problem? I honestly don't understand what you're talking about... :)

Either do I.

The issue is with the isinstance() function. People say you shouldn't use it because it forks the flow control. I don't really know what they mean.

I want to know because I want to know if the alternate function I wrote for the purpose also causes a fork in the flow control (whatever that means).

Anyway, here's one of the many sites that talks about the issue:
[http://www.canonical.org/~kragen/isinstance/](http://www.canonical.org/~kragen/isinstance/)

If anyone could explain it (and why forking is bad), that would be great. Examples using code to demonstrate what it is would be best.

---

### Post by CptPicard on 2009-08-21
Aa, we're talking about the design issue of introducing some sort of alternate behaviour based on an explicit isinstance test. If I were you I would not mind that much about the "flow control forking" stuff -- the basic point is that it is just not very good style to use isinstance to discriminate types. It goes against the philosophy of duck typing.

You'd be much better off testing for specific symbols on the object with has_attr instead of the type of the object. That is, if you know that your type Dog has some "bark" method, you don't test for Dog, you test if your object can "bark" (suppose there are some other animals that can bark too..)

---

