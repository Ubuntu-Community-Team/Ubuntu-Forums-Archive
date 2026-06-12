---
title: "problem with operators in nasm"
date: 2011-04-27
forum: Programming Talk
---

### Post by socratic_irony on 2011-04-27
I have the following piece assembly code:
```

mov ebx,eax % 10
mov eax,eax / 10

```

It gives the following errors on assembling:
```

error: division operator may only be applied to scalar values
error: division operator may only be applied to scalar values

```

I'm new to assembly and just writing my first few assembly programs. What may be the cause of the errors?

---

### Post by BkkBonanza on 2011-04-27
As the error msg suggest you can only use a division/mod operator for "scalars" - which means constants that are computed at assembly time. Those operators are not machine instructions. If you want to do actual division in assembly code then you have to use the suitable op codes. Refer to assembly code reference guides for your cpu.

---

### Post by socratic_irony on 2011-04-28
Thanks. :D

---

