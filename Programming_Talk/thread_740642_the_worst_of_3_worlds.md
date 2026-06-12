---
title: "the worst of 3 worlds"
date: 2008-03-31
forum: Programming Talk
---

### Post by slavik on 2008-03-31
I present to you, the unreadability of Perl, the huge amount of parenthesis of Lisp using the macro features of the CPP.

```
#define D2TD1(TYPE,PTR,ROW,COL) ((TYPE *)((size_t)(PTR)+((ROW)*(SIZE*SIZE*(size_t)sizeof(TYPE)))+((COL)*(size_t)sizeof(TYPE))))
```

The macro is valid, guess what it does. :)

edit: or there is an easier way to do this in C and I am missing it for some reason.

---

