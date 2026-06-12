---
title: "Oz Programming Help"
date: 2010-08-22
forum: Programming Talk
---

### Post by napz on 2010-08-22
Hey, does anyone have an idea how can I do a loop through a list using Oz programming language ?

Thanks in advance.

---

### Post by pling on 2010-08-22
> **napz said:**
> Hey, does anyone have an idea how can I do a loop through a list using Oz programming language ?

Thanks in advance.

Oz is a functional language so you're probably better writing a function that does something to the first element of the list and then calls itself on a list consisting of the remaining elements. This works well because you can pass this function another function that will actually do stuff to the elements, so you can write (psuedo code):

listSqs = listApplyFn(list, sqFn)

If you're learning a new language for fun/broadening your mind, then Oz wouldn't be a choice that I'd recommend unless you already know a functional language. You'd be better off with Scala (which you can use like a "normal" language or a functional) or Erlang or Haskell. All are (imo) better designs and have much better books and more active communities.

---

