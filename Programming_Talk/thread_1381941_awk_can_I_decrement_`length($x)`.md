---
title: "awk: can I decrement `length($x)`"
date: 2010-01-15
forum: Programming Talk
---

### Post by alphaniner on 2010-01-15
Is there anyway to modify the value of `length($x)` in the following:

```
awk '{print substr($9,1,length($9))}'
```

Specifically, I want to decrease it by one.  I know there's a myriad of other ways I could do what I want to do, I'm just hoping I can avoid doing them.

---

### Post by saulgoode on 2010-01-15
Why not just subtract one from value returned?

```
awk '{print substr($9, 1, length($9) - 1)}'
```

---

### Post by lisati on 2010-01-15
> **saulgoode said:**
> Why not just subtract one from value returned?

```
awk '{print substr($9, 1, length($9) - 1)}'
```

Beat me to it!

Saving the result(s) a function/procedure returns and working on the saved copy is sometimes easier than trying to modify the function/procedure yourself.

---

### Post by alphaniner on 2010-01-15
> **saulgoode said:**
> Why not just subtract one from value returned?

```
awk '{print substr($9, 1, length($9) - 1)}'
```

<*grumble*> I *swear* I tried that and it didn't work.  Thank you.

---

