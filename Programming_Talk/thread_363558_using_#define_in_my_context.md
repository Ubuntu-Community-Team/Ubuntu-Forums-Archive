---
title: "using #define in my context?"
date: 2007-02-17
forum: Programming Talk
---

### Post by ansi on 2007-02-17
Hello,

 I wrote some own functions (C) which operates with strings, they looks like Std. functions:
```

    _bool  mystr_ncpy(myStr* dst, char* src, size_t src_len)
   {
          ..... 
   }
```

And I want define the same function's which gives only src && dst as arguments. What version is better:
```
 #define   mystr_cpy(dst, src)     mystr_cpy(dst, src, strlen(src))
```

or this:
```
   _bool mystr_cpy(myStr* dst, char* src)
   {
     return mystr_ncpy(dst, src, strlen(src));
   }
```


Of course, I understand that the version with #define will be processed with pre-processor on compilation study, but second version will spend processor's time on creating new stack (I think). 1st version looks more elegant, but it will be hard-understandable in headers for other developers.

It is in more part a design question I think.

Thanks.

---

### Post by runningwithscissors on 2007-02-17
It doesn't matter either way. Trying to shave nanoseconds off is more trouble than it's worth.

Having said that, the first one is a lot more clearer, in my opinion.

---

### Post by lnostdal on 2007-02-17
don't ever use macros if you don't have to ..  if you are concerned with the overhead of one extra call add a declaration `inline'

```

inline _bool mystr_cpy(myStr* dst, char* src)
   {
     return mystr_ncpy(dst, src, strlen(src));
   }

```

..when you compile this with some optimization-options turned on the extra call will be gone or "inlined" with the code of the caller

---

### Post by ansi on 2007-02-17
> **lnostdal said:**
> don't ever use macros if you don't have to ..  if you are concerned with the overhead of one extra call add a declaration `inline'.


O! Nice. I've just forgot about inline'd functions. But they have exactly one disadvantage: they are not defined by C89 :), but C99 is more nice than C89 I think :).

Thanks to all. The question was solved.

---

### Post by lnostdal on 2007-02-17
i wonder what the next Cxx will be called .. i mean after C99 we'll have the old y2k problem again :)

---

