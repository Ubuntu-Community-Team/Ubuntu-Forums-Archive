---
title: "Two questions: GCC"
date: 2009-02-16
forum: Programming Talk
---

### Post by Krupski on 2009-02-16
Hi all!

This is probably simple stuff... but I can't seem to find it (yes I googled the heck out of it).

OK, Ques #1: In Linux and using GCC, how do I determine which library has the function I need?

Ques #2: I need to do base 10 exponent (that is, 10^0=1, 10^1=10, 10^2=100, etc...) how do I do it in GCC?

In Win LCC-32 there is a function "pow10()" which takes 1 parameter (the exponent). For example, "pow10(3) == 1000".

Anything like this in GCC, or do I have to write my own?

Thanks!

-- Roger

---

### Post by bruce89 on 2009-02-16
First off, GCC is a C compiler. glibc is the GNU C Standard Library, which is what you meant by GCC.

> **Krupski said:**
> OK, Ques #1: In Linux and using GCC, how do I determine which library has the function I need?

You need to know what library a function is in before you can use it.

> **Krupski said:**
> Ques #2: I need to do base 10 exponent (that is, 10^0=1, 10^1=10, 10^2=100, etc...) how do I do it in GCC?

In Win LCC-32 there is a function "pow10()" which takes 1 parameter (the exponent). For example, "pow10(3) == 1000".

Anything like this in GCC, or do I have to write my own?

You're getting confused between GCC and glibc, see above.

Anyway, glibc has the function pow10 (the documentation says that exp10 is preferred), which takes a double and returns a double. Include <math.h>, and add "-lm" to the GCC command.

---

### Post by Krupski on 2009-02-16
> **bruce89 said:**
> Anyway, glibc has the function pow10 (the documentation says that exp10 is preferred), which takes a double and returns a double. Include <math.h>, and add "-lm" to the GCC command.

I have done both (include math.h and use the -lm switch) and here's what I get:

```

convert.c: In function ‘main’:
convert.c:73: warning: implicit declaration of function ‘pow10’
convert.c:73: warning: incompatible implicit declaration of built-in function ‘pow10’

```

I get the same exact error with "exp10" - no difference.

Concerning my first question, if I *didn't* know that "pow10()" needed "math.h", how would I go about finding which "include" to use?

I saw the answer on here somewhere before... but I don't remember what it was and I can't find it. :(

---

### Post by Can+~ on 2009-02-16
```
pow(10, 3);
```

[http://www.cplusplus.com/reference/clibrary/cmath/](http://www.cplusplus.com/reference/clibrary/cmath/)
(Yeah, it's a c++ reference, but the C library is intact!)

---

### Post by Krupski on 2009-02-16
> **Can+~ said:**
> ```
pow(10, 3);
```

[http://www.cplusplus.com/reference/clibrary/cmath/](http://www.cplusplus.com/reference/clibrary/cmath/)
(Yeah, it's a c++ reference, but the C library is intact!)

Well now that works! Thank you so much.

-- Roger

(edit to add): Thanks for the link to the reference too! It'll be a great help.

---

### Post by the_unforgiven on 2009-02-17
> **Krupski said:**
> 
Concerning my first question, if I *didn't* know that "pow10()" needed "math.h", how would I go about finding which "include" to use?

I saw the answer on here somewhere before... but I don't remember what it was and I can't find it. :(
You generally use manual pages to see how to use the function - what headers to include and what libraries to link to.
For example, all the glibc functions are documented in the 3rd section of manual pages. So, you could do:
```
man 3 pow
```
You need to have the 'manpages' package installed for that.

---

### Post by Krupski on 2009-02-17
> **the_unforgiven said:**
> You generally use manual pages to see how to use the function - what headers to include and what libraries to link to.
For example, all the glibc functions are documented in the 3rd section of manual pages. So, you could do:
```
man 3 pow
```
You need to have the 'manpages' package installed for that.

Thank you for the info. I'll have to install the manpages package... don't have it yet.

Thanks!

-- Roger

---

