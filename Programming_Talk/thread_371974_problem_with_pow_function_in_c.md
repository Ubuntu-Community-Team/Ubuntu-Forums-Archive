---
title: "problem with pow function in c"
date: 2007-02-27
forum: Programming Talk
---

### Post by engineer on 2007-02-27
i have a problem with the pow function in c (standard math lib).

when calling for example with the following arguments

```

pow(-3.694710e1, -6.350497e-1)

```

nan is returned.

is there any function, which can do this?
i don't want to write it by myself...

---

### Post by yaaarrrgg on 2007-02-27
You have two negative numbers... is this correct?  From reference:

"If base is negative and exponent is not an integral value a domain error occurs, setting the global variable errno to the value EDOM."

Do you need complex numbers?

---

### Post by engineer on 2007-02-27
i already read it in man pages, but didn't realize, that my arguments are both negative.](*,) 
so i have to think about the arguments.

thanks!

---

### Post by lnostdal on 2007-02-27
if it turns out you need complex numbers see:

man 7 complex
man 3 cpow

(note that this is C99 as mentioned on these pages)

---

