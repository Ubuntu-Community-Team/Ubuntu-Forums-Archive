---
title: "[SOLVED] Compiled language similar to Python"
date: 2009-01-05
forum: Programming Talk
---

### Post by JordyD on 2009-01-05
I'm, for the most part, new to programming, and the only language I know well is Python. I *do* know little bits and pieces of other languages (mostly c++), but I'd like to learn a faster, compiled language. So taking into account that I already know Python pretty well, are there any good compiled languages similar to Python?

Thanks,
Jordy

---

### Post by pmasiar on 2009-01-05
It depends on your definition of "similar". :-) Python is dynamically typed which is quite a problem for compilers

1) Python can be compiled: Psyco, ShedSkin, etc
2) Cython, rPython (part of PyPy) is Python like
3) C is "as simple as Python" (TM)

If you want to learn mainstream compiled language, go for C (and be prepared for some pain).

---

### Post by JordyD on 2009-01-05
> **pmasiar said:**
> It depends on your definition of "similar". :-) Python is dynamically typed which is quite a problem for compilers

1) Python can be compiled: Psyco, ShedSkin, etc
2) Cython, rPython (part of PyPy) is Python like
3) C is "as simple as Python" (TM)

If you want to learn mainstream compiled language, go for C (and be prepared for some pain).

By 'similar' I mean 'syntactically similar'. I don't know if they have something like that, but if they do, it would certainly eliminate some pain.

I also don't want to just compile Python because I would like to learn another language.

And what is the difference between C and C++? Is there a significant difference or is C++ just like an upgraded version?

Thanks for you help,
Jordy

---

### Post by Cracauer on 2009-01-05
Modula-3 is probably your best bet if you require a good implementation.

Of course you move to static type checking but I think the "feel" of the language is closest, at least if you liked the OOP parts of Python.

---

### Post by JordyD on 2009-01-05
> **Cracauer said:**
> Modula-3 is probably your best bet if you require a good implementation.

Of course you move to static type checking but I think the "feel" of the language is closest, at least if you liked the OOP parts of Python.

Okay, I'll take a look at that. Thanks.

**EDIT:**

What's a good compiler?

---

### Post by nvteighen on 2009-01-05
There's none... at least syntactically similar in "surface structure" (thanks, Noam... :)), but in "deep structure" Python's and C's syntaxes are not that different, except for the whitespace issue... which it anyway is a good-C-code convention, so you actually better stick to it also in C :)

---

### Post by efexD on 2009-01-05
Similar in terms of compiled or interpreted?
Easy syntax or hard syntax?

---

### Post by JordyD on 2009-01-05
> **efeXor said:**
> Similar in terms of compiled or interpreted?
Easy syntax or hard syntax?

I want a compiled language with easy syntax.

If nothing is available, I'll probably go learn C++.

---

### Post by Greyed on 2009-01-05
Java?

OCaml?

D?

---

### Post by JordyD on 2009-01-05
> **Greyed said:**
> Java?

OCaml?

D?

I'll look into those, too. Thanks.

---

### Post by vambo on 2009-01-05
This might be worth a look. Still very experimental and far from mainstream, but interesting nonetheless.

[http://mathias-kettner.de/wirbel.html]("http://mathias-kettner.de/wirbel.html")

---

### Post by shadylookin on 2009-01-05
java is jit(just in time) compiled and pretty fast

c++ is compiled, fast, mainstream, and you apparently know some of it. So you might want to stick to c++

---

### Post by efexD on 2009-01-05
I would say either C++ or Java.
Because once you learn the syntax of one, others become very clear. It just takes time.

---

### Post by Reiger on 2009-01-05
If you want a true compiled Python-like language then this is it:

> **vambo said:**
> This might be worth a look. Still very experimental and far from mainstream, but interesting nonetheless.

[http://mathias-kettner.de/wirbel.html]("http://mathias-kettner.de/wirbel.html")

It's even 'advertised' as such.

---

### Post by JordyD on 2009-01-05
> **vambo said:**
> This might be worth a look. Still very experimental and far from mainstream, but interesting nonetheless.

[http://mathias-kettner.de/wirbel.html]("http://mathias-kettner.de/wirbel.html")

This looks very interesting. I do wish that those buttons at the top were in English, though. Besides "Linux" and "Projekte" I can't guess what they mean.

I'll try out Wirbel. I'll probably learn C++ at some point anyways, along with Wirbel.

Thanks everyone for your help.
Jordy

---

### Post by Cracauer on 2009-01-05
> **JordyD said:**
> Okay, I'll take a look at that. Thanks.

**EDIT:**

What's a good compiler?

Modula-3 compiler:

[http://www.cvsup.org/ezm3/](http://www.cvsup.org/ezm3/)

---

### Post by Kilon on 2009-01-05
I can't say that JAVA or C++ is similar to Python syntax. 

The one that reminds me of python most is Pascal actually. 

You can try FreePascal , it is cross platform and like pythons works hand in hand with C\C++. 


[http://www.freepascal.org/](http://www.freepascal.org/)

The advantages of freePascal is that is fully compatible with Delphi libraries which is a commercial IDE (WINDOWS/LINUX) and language product. Lazarus which is the IDE clone of Delphi , is very good and free as well (open source). You will find loads of documentation and how to's. It is a very easy to use language with a very active community. Pascal is one of the oldest languages.

---

### Post by Cracauer on 2009-01-05
Pascal and OO variants such as Modula-3 are clearly the most similar.

Whether they are the best choice is a different matter...

---

### Post by wmcbrine on 2009-01-05
> **Cracauer said:**
> Pascal and OO variants such as Modula-3 are clearly the most similar.Only superficially, because of the "plain English" appearance they share. But IMHO Python really has more in common with C, borrowing e.g. many of C's operators. Although Python's logical operators -- "and"/"or"/"not" -- do match Pascal rather than C. Also, Python has nested functions, like Pascal. Hmm...

---

### Post by Cracauer on 2009-01-06
No way.

Operator likeness, maybe.

But programming C well is all about preallocated buffers and byzantine APIs, and with C++ it gets 8.3 times worse. These two have nothing in common with the spirit of Python programming.

Smalltalk might be a real contender, but I wouldn't say there's a true OpenSource compiler out there, at least not a very practical one.

---

### Post by wmcbrine on 2009-01-06
> **Cracauer said:**
> But programming C well is all about preallocated buffers and byzantine APIs, and with C++ it gets 8.3 times worse. These two have nothing in common with the spirit of Python programming.But neither does Pascal, IMHO.

When I moved from Pascal to C as my main language, it felt tremendously freeing -- I could now do things that I'd had to use inline assembly to do before, because Pascal was so restrictive. Moving from C to Python, I get the same kind of feeling, even though it's a move in the "other direction" (lower level language to higher level). I do miss a few things from C, but not, e.g., explicitly specified types or block delimiters -- things which are part of both Pascal and C. But Pascal also lacks even the implicit type conversions of C.

So on my very informal "pain in the ***" scale, Pascal > C > Python. :D

C++ is a whole other issue. I wouldn't lump it in with C, which is a small, elegant language, albeit not without its flaws.

---

### Post by jimi_hendrix on 2009-01-06
well...OP can always learn ASM...

---

### Post by Cracauer on 2009-01-07
> **wmcbrine said:**
> But neither does Pascal, IMHO.


That's why I said Modula-3, not Pascal :)

---

