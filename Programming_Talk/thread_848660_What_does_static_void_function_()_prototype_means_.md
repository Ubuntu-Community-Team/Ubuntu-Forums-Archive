---
title: "What does static void function () prototype means in C."
date: 2008-07-03
forum: Programming Talk
---

### Post by dmitrijledkov on 2008-07-03
I've been learning C and started to learn GTK. In the examples function prototypes all begin with static void.

Void means that function doesn't return anything, but what does static keyword means?

Is it part of C? When and where should I use it?

Thank you in advance.

---

### Post by WW on 2008-07-03
> **dmitrijledkov said:**
> I've been learning C and started to learn GTK. In the examples function prototypes all begin with static void.

Void means that function doesn't return anything, but what does static keyword means?
The function is only visible in the file in which it is defined.

> **dmitrijledkov said:**
> 
Is it part of C?

Yes.

> **dmitrijledkov said:**
> 
When and where should I use it?

When you don't want (or need) the function to be called from functions that are defined in other files.

More info: [http://gd.tuwien.ac.at/languages/c/cref-mleslie/SYNTAX/static.htm](http://gd.tuwien.ac.at/languages/c/cref-mleslie/SYNTAX/static.htm)

---

