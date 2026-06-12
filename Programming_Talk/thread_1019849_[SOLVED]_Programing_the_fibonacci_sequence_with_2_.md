---
title: "[SOLVED] Programing the fibonacci sequence with 2 variables"
date: 2008-12-23
forum: Programming Talk
---

### Post by R031E5 on 2008-12-23
Hi! I'm having a really hard time figuring out if there's some programming language in which I can write the fibonacci sequence with only two variables.

The normal syntax is (as everybody knows):
```
    z = x + y
    x = y
    y = z
```

But I'm just curious
I hope someone can help me with that

Cheers!

---

### Post by Gilabuugs on 2008-12-23
something like?
[http://code.activestate.com/recipes/66316/](http://code.activestate.com/recipes/66316/)

---

### Post by monkeyking on 2008-12-23
or just do it analytically with one variabel

[IMG]http://upload.wikimedia.org/math/e/a/2/ea28b263d7f01d652ebc064d0ee0e26b.png[/IMG]

---

### Post by PandaGoat on 2008-12-23
I do not think you can do what you are asking since that is not how a sequence is even defined.  If you want the nth number you *must* build up to it using recursion or iteration. There is no language that implements any of these methods with simple assignments.  Although, this sequence is closely tied to the golden ratio, and the nth number can be approximated, as the above poster pointed out. 

The closest thing I can think of for a language where you can do what you want is Haskell where variables are not evaluated until they are needed, although I am sure there are other language.

---

### Post by monkeyking on 2008-12-23
> **PandaGoat said:**
> ... If you want the nth numbers you*must* build up to it using recursion or iteration...

... and the nth number can be approximated, as the above poster pointed out. 


Without making a mathdiscussion out of it.
I don't think you are right.

You don't have to build up anything.
If you want to calculate the sum of all values from 0 to n.
You don't actually have to add every single one.
you can simply calculate it by n(n+1)/2.

The formula is not an approximation, it's equally valid.
It broadens the domain for the fib function from the positive integers to the reals. Just as the gamma function has the real axis as domain but contains the factorial function as an injection on the natural numbers.

enjoy the christmas.

---

### Post by slavik on 2008-12-24
using recursion, you need only 2 variables ...

x=1, y=1
odd iterations ...
x+=y;
print x
even iterations ...
y+=x;
print y

---

