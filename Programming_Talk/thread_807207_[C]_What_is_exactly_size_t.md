---
title: "[C] What is exactly size_t?"
date: 2008-05-25
forum: Programming Talk
---

### Post by nvteighen on 2008-05-25
Hi!

Please, can someone explain me what is exactly size_t used for? I know it is a data type that can have various sizes depending on the platform and is the type what sizeof() returns and other functions like snprintf() need, but why just not a plain int (whose size also changes with the platform)?

Excuse me for my ignorance!

---

### Post by Lau_of_DK on 2008-05-25
> **nvteighen said:**
> Hi!

Please, can someone explain me what is exactly size_t used for? I know it is a data type that can have various sizes depending on the platform and is the type what sizeof() returns and other functions like snprintf() need, but why just not a plain int (whose size also changes with the platform)?

Excuse me for my ignorance!

Its this:

[quote=google]
`size_t' is a type suitable for representing the amount
of memory a data object requires, expressed in units of `char'.
It is an integer type (C cannot keep track of fractions of a
`char'), and it is unsigned (negative sizes make no sense).
It is the type of the result of the `sizeof' operator. It is
the type you pass to malloc() and friends to say how much
memory you want. It is the type returned by strlen() to say
how many "significant" characters are in a string.
[/quote]


Read the rest: [Here]("http://bytes.com/forum/thread220206.html")

---

### Post by Lster on 2008-05-25
This may also be helpful:

[http://www.cplusplus.com/reference/clibrary/cstring/size_t.html](http://www.cplusplus.com/reference/clibrary/cstring/size_t.html)

---

### Post by nvteighen on 2008-05-25
Thanks for the links!

But isn't it a bit dangerous? I mean, if accidentally a negative value is stored into a unsigned type, what we get is a large number (the maximum length - the absolute value of the stored number, I think)... So, in a malloc() call that can be really harmful, isn't it?

I have had some bad experience with math.h's log10 returning negatives into a size_t variable that was latter used by malloc().

---

### Post by Npl on 2008-05-25
> **nvteighen said:**
> Thanks for the links!

But isn't it a bit dangerous? I mean, if accidentally a negative value is stored into a unsigned type, what we get is a large number (the maximum length - the absolute value of the stored number, I think)... So, in a malloc() call that can be really harmful, isn't it?

I have had some bad experience with math.h's log10 returning negatives into a size_t variable that was latter used by malloc().Uhh... thats a problem for all singned->unsigned conversions. It`s your problem though... what do you expect to happen if you call malloc with a negative integer?
If you tell the computer to do bullsheet he might comply :)

---

### Post by slavik on 2008-05-25
> **Npl said:**
> Uhh... thats a problem for all singned->unsigned conversions. It`s your problem though... what do you expect to happen if you call malloc with a negative integer?
If you tell the computer to do bullsheet he might comply :)
that's why I set my Linux systems to vm.overcommit_memory to 2 with ration being 50. :)

---

### Post by nvteighen on 2008-05-26
> **Npl said:**
> ... what do you expect to happen if you call malloc with a negative integer?


Wait: if you call malloc with negative integers, don't you get a sandwich?? :p

So, being serious: in summary, signed -> unsigned conversion doesn't take the absolute value and one must be careful to watch what is being stored at a size_t variable (or whatever any other unsigned type). Am I right now?

---

