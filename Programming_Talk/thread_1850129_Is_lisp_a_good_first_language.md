---
title: "Is lisp a good first language?"
date: 2011-09-25
forum: Programming Talk
---

### Post by insanity99 on 2011-09-25
I want to get into programming. I don't have any experience other than ActionScript. I know concepts like variables, functions and data types, but that's all.

I don't have many goals. I'm learning for fun, although sometimes I want to make my own roguelike.

If Lisp is a good choice to learn as a first language, Can you suggest some beginner-level books?

Thanks.

---

### Post by cgroza on 2011-09-25
I don't know if it's a good language for learning, but I know that it is not a common one.
I started with Python and never regretted it.

---

### Post by Bachstelze on 2011-09-25
Yes. [http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/)

Python is also good, but I believe starting Lisp will make you a better programmer in the long run. Of course it depends on your goals, and since you say you don't really have any...

---

### Post by Smart Viking on 2011-09-25
From what I've heard, lisp is great as a starting language.

I only know a little lisp though, I started out with Python.

---

### Post by slavik on 2011-09-26
LISP is good as a starting language.

---

### Post by JDShu on 2011-09-26
I think Lisp would be an amazing first language. The SICP link in Bachstelze's post is a classic. Go through the lecture videos and (free) book if only for the bragging rights :D

---

### Post by ve4cib on 2011-09-26
Lisp is definitely fun, and one of those languages I think anyone serious about being a programmer should learn at some point.

The biggest advantage to learning Lisp first is that it is very simple in terms of syntax.  Everything is a list, and everything is reliably evaluated in a consistent, recursive fashion.  Its simplicity makes it very easy to learn, but it's powerful enough to do pretty much any kind of programming you want.  And if you ever want to get into AI research Lisp is commonly used in those kinds of areas.

The biggest disadvantages of learning Lisp first are that it is rarely used outside of academia (and Emacs), so you will definitely need to learn other languages later.  Secondly, Lisp is a functional language, but most professional programmers work in imperative languages (like Java, C, C++, Fortran, most Python programming, etc...).  At a fundamental level, Lisp forces you to *think* differently than you do with most other languages, so you may find it difficult to adjust to thinking in an imperative way once you become proficient with Lisp.

Is it a good first choice?  Maybe.  Personally I think any language *can* be a good first choice and the quality of the choice relies more on the student and the instructor than on the language itself.  It is a choice, and would not likely be the one I would choose to teach first.  But if you want to learn it first then by all means go ahead.  You will not lose anything by learning it, and you may potentially gain a great deal.

---

### Post by JDShu on 2011-09-26
> **ve4cib said:**
> 
The biggest disadvantages of learning Lisp first are that it is rarely used outside of academia (and Emacs), so you will definitely need to learn other languages later.  Secondly, Lisp is a functional language, but most professional programmers work in imperative languages (like Java, C, C++, Fortran, most Python programming, etc...).  At a fundamental level, Lisp forces you to *think* differently than you do with most other languages, so you may find it difficult to adjust to thinking in an imperative way once you become proficient with Lisp.


I'm being a bit pedantic, but Lisp is not a functional language. You can use imperative (and even OOP) if you want.

---

### Post by ve4cib on 2011-09-26
> **JDShu said:**
> I'm being a bit pedantic, but Lisp is not a functional language. You can use imperative (and even OOP) if you want.

If I may counter your pedanticism, LISP is a functional language, with some non-functional elements (or "pollution" if you're a purist).  But at its core it is functional, not imperative or OO.

---

### Post by CptPicard on 2011-09-26
I'm a big proponent of Lisp; it's remarkably minimal but also remarkably abstract and expressive. Very easy to get started with, and the cool point is that you can, in a sense, express everything *in most other languages* with "minimal effort" -- this means Lisp exposes you to a lot of ideas very quickly. When you move to more specific languages, you'll recognize the particulars from the general idea you got from Lisp.

Lisp is in a sense a general language interpreter already... it's very easy to build interpreters for other languages on top of it. That's why an argument can be made that it is, a sense, the optimal first language to learn.

---

### Post by insanity99 on 2011-09-26
Thanks guys, I started reading a book called Land of Lisp, it uses common lisp and all the exercises are making games.

I'm not sure if its a good book or not, got good reviews. and I figured it would help prepare me to make a rogue like.]

I am using the compiler CLISP right now. I keep messing but because I forget to to '(' at the start of each line :D

---

### Post by cgroza on 2011-09-26
> **insanity99 said:**
> Thanks guys, I started reading a book called Land of Lisp, it uses common lisp and all the exercises are making games.

I'm not sure if its a good book or not, got good reviews. and I figured it would help prepare me to make a rogue like.]

I am using the compiler CLISP right now. I keep messing but because I forget to to '(' at the start of each line :D
Now if you started Lisp, there is no better editor for it than Emacs.

---

### Post by nvteighen on 2011-09-26
Lisp (Scheme) was used on the mythical SICP MIT course as a first language for years. (Then it was replaced by Python. Not sure what were the reasons... but it's not like MIT does things randomly)

So yeah, Lisp is perfect for this. It makes things very transparent because it almost lacks any syntax and because it gives you the ability to use the Lisp interpreter as your own language's. You may not get the importance of that last feature at the beginning, but you will in the future.

> **ve4cib said:**
> If I may counter your pedanticism, LISP is a functional language, with some non-functional elements (or "pollution" if you're a purist).  But at its core it is functional, not imperative or OO.

Scheme and Common Lisp have set! and setf (respectively) as core concepts of the language. Specially CL's setf, which is very important when doing some stuff with CLOS...

Lisp is not about pure FP; it's not Haskell. Actually, sometimes pure things may sound great, but are impractical. Lisp is actually more about metaprogramming than FP, even when it obviously gains a lot from the latter.

---

### Post by GenBattle on 2011-09-26
I would recommend Python instead as a first language, especially for games. LISP will give you a better grounding in computer science and programming, true, but there are many more game programming resources for Python; Panda3D, Pyglet, PyGame, Cocos2D, etc.

---

### Post by BeRoot ReBoot on 2011-09-26
Definitely seconding the recommendation for Python as a first language. I've tried learning lisp, and I understand it, but to me the language is absolutely unreadable, and I don't like writing code that requires an equal or greater size of comments to be understood. I understand the arguments in favour of purely functional languages, and just by looking at the bullet points, lisp looks like the perfect language. I say try it out, but don't be scared if you don't get it, and don't be afraid to try an "easier" language like python.

---

