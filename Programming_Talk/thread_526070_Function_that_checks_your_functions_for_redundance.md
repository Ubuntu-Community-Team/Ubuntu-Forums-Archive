---
title: "Function that checks your functions for redundance?"
date: 2007-08-15
forum: Programming Talk
---

### Post by triptoe on 2007-08-15
I was just curious.. most languages have a standard library. Like python for instance... i can use a lot of built in functions.

my question is if there is actually a function that will detect in your program if any of the functions you have written are similar to ones already made and will inform you?

---

### Post by Wybiral on 2007-08-15
> **triptoe said:**
> I was just curious.. most languages have a standard library. Like python for instance... i can use a lot of built in functions.

my question is if there is actually a function that will detect in your program if any of the functions you have written are similar to ones already made and will inform you?

I don't think it's possible. Everyone will implement things slightly different so the code won't look the same, even if it produces the exact same result.

---

### Post by LaRoza on 2007-08-15
> **triptoe said:**
> I was just curious.. most languages have a standard library. Like python for instance... i can use a lot of built in functions.

my question is if there is actually a function that will detect in your program if any of the functions you have written are similar to ones already made and will inform you?

For python, check the [Python Library Reference]("http://docs.python.org/lib/"), actually, keep it at your side at all times! (You can download it from the site at: http://docs.python.org/download.html")

---

### Post by Tomosaur on 2007-08-15
The only real way to make sure you're not reinventing the wheel is to know what libraries / functions are already available. This means you need to spend a lot of time reading. Read up on the standard libraries for whichever programming language you're using, and when you want to code in a new feature, do a web search to see if there's something already in existence which does a similar job.

---

### Post by jaybee99 on 2007-08-15
You can get close to this effect in staticly typed languages without side effects such as haskell. You can use hoogle.com for instance to look for functions with the same type and, in a world without side effects, functions with the same type are usually strongly related - it may be that the library function with the same type as yours does the same thing.

---

### Post by pmasiar on 2007-08-15
> **Tomosaur said:**
> The only real way to make sure you're not reinventing the wheel is to know what libraries / functions are already available. This means you need to spend a lot of time reading. 

That's why I suggested recently that size of library reference is important deciding factor when selecting a language! :-) Python pocket reference has 150 pages of pocket format - java in a nutshell is 1200 pages of std format - 20 times as much reading! :-D

---

### Post by CptPicard on 2007-08-16
From a computer science perspective, this is actually impossible. There is no way to, in general case, give a function that checks two other functions for equivalence. The issue is related to the halting problem which in turn has its roots in the Entscheidungsproblem of formal logic. This was something that bothered mathematicials a lot on the early part of last century; then guys like Gödel, Turing and Church figured it out.

This is also why automated debugging is impossible in the general case.

---

