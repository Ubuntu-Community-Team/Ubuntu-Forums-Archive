---
title: "Factor Program Causes 'Floating Point Exception'"
date: 2007-05-23
forum: Programming Talk
---

### Post by Lster on 2007-05-23
Hi

I have a problem with a small program. It's supposed to display all the factors of a number entered. This is the code:

```

...

```

I compile and run with:

```

...

```

There aren't any compile-time errors, but when I run I get:

> > 123
Floating point exception (core dumped)


I just can't see anything wrong with my code...

Thanks,
Lster

---

### Post by GeneralZod on 2007-05-23
```
if ( x % i == 0 )
```

What happens when i == 0?

---

### Post by Lster on 2007-05-23
Whoops... You are right - I should start at 1!

Thanks,
Lster

---

