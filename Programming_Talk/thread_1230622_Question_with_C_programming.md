---
title: "Question with C programming"
date: 2009-08-03
forum: Programming Talk
---

### Post by weirdalec222 on 2009-08-03
I need to build a function that allows the user to input 2 strings, and then it checks to see if the second string is contained inside the first string..
 
any ideas? I'm having a lot of trouble!

---

### Post by djurny on 2009-08-03
are you allowed to use standard libc-like functions? substr will do the job for you..

---

### Post by weirdalec222 on 2009-08-03
i do not believe so, we are using the ANSI C library and the <string.h> header if that answers your question.
 
I think I'm supposed to use strcmp or strcpy, however I'm unsure.

---

### Post by djurny on 2009-08-03
> **weirdalec222 said:**
> i do not believe so, we are using the ANSI C library and the <string.h> header if that answers your question.
 
I think I'm supposed to use strcmp or strcpy, however I'm unsure.

[http://linux.die.net/man/3/strstr](http://linux.die.net/man/3/strstr)

made a typo; it was supposed to be strstr() instead of substr().. strstr() is defined in string.h so you're good to go..

---

### Post by asbuntu on 2009-08-03
Sounds like a homework problem to me.  I'm not sure this is the right forum for that.  Anyway, substr() is not "standard" libc.  Check out strstr().

---

