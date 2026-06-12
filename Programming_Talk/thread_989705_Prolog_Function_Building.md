---
title: "Prolog Function Building"
date: 2008-11-21
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-11-21
I have heard that Prolog can build dynamic functions like Lisp or Lambda Calculus. How is that done??



On another note, please rate Slackware on a scale of 0 to 10 for the following categories

Speed
Custom ability
Easy of Installation
Being Low Level
Ease of installing Packages
Worth trying on another computer

post results simply like below (nothing for no experience with it)

9
10
6
8
1
4

Thank You

---

### Post by Mr.Macdonald on 2008-11-22
Does anyone program Prolog?

---

### Post by pmasiar on 2008-11-22
I don't think there are too many Prolog experts aroud here (I know some Prolog but I am not expert). We have hard time to enlighten speed kiddies to consider Python! ;-) Lisp is more common "esoteric" language around here. I would recommend  inquiring on Prolog newsgroup instead.

---

### Post by Mr.Macdonald on 2008-11-22
Alright, but I will leave this open to who ever happens along.

and by the way
```
Esoteric Es`o*ter"ic ([e^]s`[-o]*t[e^]"[i^]k), a. [Gr.
 'eswteriko`s, fr. 'esw`teros inner, interior, comp. fr. 'e`sw
 in, within, fr. 'es, e'is, into, fr. 'en in. See In.]
 1. Designed for, and understood by, the specially initiated
 alone; not communicated, or not intelligible, to the
 general body of followers; private; interior; acroamatic;
 -- said of discussions of technical topics and of the
 private and more recondite instructions and doctrines of
 philosophers. Opposed to exoteric.
 [1913 Webster]
```

---

### Post by CptPicard on 2008-11-22
[http://www.cis.temple.edu/~pwang/203-AI/Lecture/Prolog-4.htm](http://www.cis.temple.edu/~pwang/203-AI/Lecture/Prolog-4.htm)

I am not sure if "dynamic predicates" is what you mean, but a bit of googling reveals this.

And no, I don't really know Prolog either, just had to take a bit of it at uni years ago.

---

### Post by Mr.Macdonald on 2008-11-22
Not really what I was looking for,

I want a method that when run, returns a function that was specifically built, in the first function, for the current situation. Like Sci-Fi Artificial Intelligence

---

### Post by pp. on 2008-11-22
A "function" in prolog is just one or more clauses. You can assert your new function and apply it as if it was part of the previously written program. You can also construct your function on the fly and pass it to other parts of the application to execute. There also is a number of predicates which take "functions" as arguments and apply those functions against some data.

---

