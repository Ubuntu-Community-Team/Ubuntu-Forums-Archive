---
title: "header files and linking in c++"
date: 2008-03-26
forum: Programming Talk
---

### Post by StOoZ on 2008-03-26
I was just wondering, how does the compiler knows where to look for the function prototypes that are included in a particular header file?

---

### Post by nitro_n2o on 2008-03-26
do you mean the actual function implementation in the *.cc file?

---

### Post by LaRoza on 2008-03-26
> **StOoZ said:**
> I was just wondering, how does the compiler knows where to look for the function prototypes that are included in a particular header file?

If it is in <header> form, it looks in a particular directory (and the header may not actually be there, if it is standard).

If it is "header" form, it looks in the cwd, or the path given.

For g++, there are in:
```

/usr/include/c++

```

---

### Post by StOoZ on 2008-03-26
ok, I didnt explain my self correctly.
what I meant is, how the compiler knows in which file to look for the actual implementation of the functions that their prototypes are declared in a header file?

sorry for misleading. :KS

---

### Post by LaRoza on 2008-03-26
> **StOoZ said:**
> ok, I didnt explain my self correctly.
what I meant is, how the compiler knows in which file to look for the actual implementation of the functions that their prototypes are declared in a header file?

sorry for misleading. :KS

You link it when you compile, with the -l flag. The header just lets the compiler know how the function is used, you have to tell it to link.

(Standard library is different, except for math.h)

---

### Post by nitro_n2o on 2008-03-26
check out chapter 7 of this book [http://csapp.cs.cmu.edu/public/manuscript.html](http://csapp.cs.cmu.edu/public/manuscript.html) it is very helpful

---

