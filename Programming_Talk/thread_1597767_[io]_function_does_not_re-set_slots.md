---
title: "[io] function does not re-set slots"
date: 2010-10-15
forum: Programming Talk
---

### Post by mo.reina on 2010-10-15
i've written a fibonacci function in IO, and while it works the first time you run it, subsequent calls to the function don't work because the slots aren't reset.

```
Io> fib := method(n, call sender setSlot("h", list(0,1)),
... while(h size - 1 < n,
... h append(h at(-1) + h at(-2))
... ))
==> method(n, call, 
    while(h size - 1 < n, h append(h at(- 1) + h at(- 2)))
)
Io> fib(10)
==> list(0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55)
Io> fib(2)
==> nil
Io> fib(3)
==> nil
Io> h
==> list(0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55)

```

for some reason, after the first call, the setSlot command isn't being evaluated, i'm guessing it's going straight to the while argument... don't understand why though....

---

### Post by mo.reina on 2010-10-15
extra comma.... doh!

---

