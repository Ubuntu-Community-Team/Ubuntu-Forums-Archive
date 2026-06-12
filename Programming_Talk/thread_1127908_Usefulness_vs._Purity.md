---
title: "Usefulness vs. Purity"
date: 2009-04-17
forum: Programming Talk
---

### Post by soltanis on 2009-04-17
Why does this seem to be a common (if not universal) trade off?

Haskell - the purported "pure" functional programming language, seems to be in my opinion highly useless. One of it's worst drawbacks is what makes it so theoretically great; functions cannot have side-effects.

Scheme - also a great functional language used to teach the basic concepts of programming, is more or less useless in the real world.

Contrast these languages with

Perl - a language that was more or less made up as it went along, has no formal specification, and yet is used pretty commonly on Unix systems.

Common Lisp - originally a functional language that broke with the paradigm (oh yes, functions do have side-effects, and yes, we are going to evaluate the expressions left-to-right IN ORDER, I'm talking to you Haskell).

C - ubiquitous despite many theoretical weaknesses, such as no bounds checking, completely unsafe pointers, and no built-in mechanisms for thread-safety.

I notice a pattern here. Academically designed languages tend to fall to the wayside and become useless despite what on paper looks like a wide range of benefits. Languages that were made up as the creators went along with a specific purpose in mind seem to rapidly gain usage and hence, become useful.

---

### Post by samjh on 2009-04-17
What do you mean by "academically designed"?  Designed by academics?  For academic purposes?

I think you'll find that some "academically designed" languages like Lisp, Pascal, and Python are/were either successful or have enjoyed a lot of success.

Equally, some languages that were "made up as the creators went along with a specific purpose" weren't so successful.  Examples include PL/1, Forth, and Jovial.  All three have been relegated to very limited niche roles.

---

### Post by Yacoby on 2009-04-17
> **soltanis said:**
> Why does this seem to be a common (if not universal) trade off?

Haskell - the purported "pure" functional programming language, seems to be in my opinion highly useless. One of it's worst drawbacks is what makes it so theoretically great; functions cannot have side-effects.

Scheme - also a great functional language used to teach the basic concepts of programming, is more or less useless in the real world.
Have you considered this is because people who have be taught using imperative or OO languages struggle to get their head around functional languages. (I know I do). Sure, they don't work for every problem, but neither does any other language. (And you have to love the lazyness)

Yahoo!s online shop building service was originally written using lisp (back before it was aquired by Yahoo!), and the developers attributed their success to having a more powerful language. There was a writeup somewhere. 

On the plus side, they are very easy to write multi core programs with, and make more scene to some people. From a mathematical standpoint, Haskell makes a lot of sence.

Wasn't Haskell designed as a teaching languge in part?

> Perl - a language that was more or less made up as it went along, has no formal specification, and yet is used pretty commonly on Unix systems.
I love perl for its clear syntax and readability...

Which is why I use Python.

> 
C - ubiquitous despite many theoretical weaknesses, such as no bounds checking, completely unsafe pointers, and no built-in mechanisms for thread-safety.
It is designed for speed. Basically a asm macro language. If I was told to develop a application that wasn't speed critical, I wouldn't use C. Sure, I love C/C++, but they aren't good at getting things done when you compare them to more modern languages.


I would have thought that things like Haskell become more widespread, as we don't seem much closer to a good oo parallel language, and unless we make another jump in technology, chip makers are going to put more cores in a cpu, rather than increase the power of the CPU.


> Surely the best programming language or environment for a task is the one that lets you get the job done quickly and easily.Agreed

---

### Post by lisati on 2009-04-17
Surely the best programming language or environment for a task is the one that lets you get the job done quickly and easily. 

To be honest, I think some of the theoretical stuff we could get into here would probably be largely unintelligible to many people (including myself)

---

### Post by CptPicard on 2009-04-17
> **soltanis said:**
> Why does this seem to be a common (if not universal) trade off?

I would say that "purity" in particular tends to be a property of a language that goes out of its way to crystallize some particular concept, but the downside is that then you have to use that one concept to build everything. When all you have is a hammer, everything starts looking like a head.

Haskell is a great example... I *still* don't quite understand how monads work for representing state, and I've tried a lot.

Practical languages are on the other hand ones that allow you to take multiple approaches and bend to your will as problem dictates.

> 
Scheme - also a great functional language used to teach the basic concepts of programming, is more or less useless in the real world.

Well actually, Scheme makes for a nice scripting language. I'll probably use Guile when I get the chance.

> 
Common Lisp - originally a functional language that broke with the paradigm (oh yes, functions do have side-effects, and yes, we are going to evaluate the expressions left-to-right IN ORDER, I'm talking to you Haskell).

Actually, remember that Lisp originally was very academic. It was notation used on scientific papers to represent programs. Then a grad student had the crazy idea of implementing eval on a computer. But yes, the practicality of CL comes from being very, very multiparadigm... it's probably the most cross-paradigm language anywhere, and a good argument can be made that any language trying to approach the level of expressiveness *has to be a lisp* because you can't do the macros, for example, without the S-expression syntax...

And laziness is nice, for example Clojure -- the JVM-lisp -- is completely lazy...

---

### Post by eye208 on 2009-04-17
> **Yacoby said:**
> Have you considered this is because people who have be taught using imperative or OO languages struggle to get their head around functional languages.
The main difference between functional and other languages is in the assignment of blame:

If you struggle with a functional language, it's because you are dumb.

If you struggle with C++, it's because the language is dumb.

---

### Post by s.fox on 2009-04-17
I believe that the most appropriate language to use is the one that will allow you to complete the task at hand with relative ease and in good time.

---

### Post by nvteighen on 2009-04-17
> **soltanis said:**
> 
Scheme - also a great functional language used to teach the basic concepts of programming, is more or less useless in the real world.


Big mistake: Scheme is not pure functional, although it's usually used that way. It's multiparadigm just like Common Lisp.

The issue with Scheme is actually its anarchy: we've got standards nobody cares for (R5RS... now R6RS...), incompatible implementations, lack of bindings and no serious sense of community.

> 
I notice a pattern here. Academically designed languages tend to fall to the wayside and become useless despite what on paper looks like a wide range of benefits. Languages that were made up as the creators went along with a specific purpose in mind seem to rapidly gain usage and hence, become useful.

Ok, depends on your task. When programming, you model some reality and you have to choose which paradigm and which language suits better to do it. For example, if your task consists in functions where state is avoidable, Scheme or Haskell may be a worth try that may solve the problem much better than C...

You may be too much influenced by thinking that programming is about developing applications. Sometimes you program to solve a theorical program... In such cases, those "pure useless" languages prove to be much superior...

---

### Post by albertjr on 2009-04-17
> **eye208 said:**
> The main difference between functional and other languages is in the assignment of blame:

If you struggle with a functional language, it's because you are dumb.

If you struggle with C++, it's because the language is dumb.

No, c++ is not a dump language
It's a very nc language cause
it is the basis of java prog language..
That's what I think..

_______________________________________
[Career Tips and Guide](http://www.ichatcareers.com/)
[ Facebook Account](http://www.facebook.com/AlbertDominguez/)

---

### Post by rplantz on 2009-04-17
Discussions like this make me recall a discussion I had with a friend in 1974. My group was trying to decide between a PDP-11 and a Nova 3, which was going to be programmed in assembly language. Since my friend used both machines, I asked his advice.

He pointed out advantages and disadvantages of both machines. He said that in the end, they performed very similarly.

Then he said that he preferred programming the Nova because (*here is the key point*) that was the one he programmed the most, so he was **more familiar with it**. One of the few times I've heard a truly honest answer. Instead, most of us spend a lot of energy rationalizing our (irrational) opinions. And most of us are pretty good at it.

---

### Post by Reiger on 2009-04-17
Haskell has been partly designed with `provable correctness' in mind: this means that if you are to implement an algorithm in Haskell it is much easier to *prove* that is correct because the basic building blocks do what they do and nothing else. Again: the ability to let functions have side effects is a nightmare when you want to prove things ...

Actually: a more or less `accepted' programming adagium is that `globals are evil'. Why? Well because in languages where you can `assign' values (rather than declaring a symbol) you can in one fell swoop render unit testing, proving algorithms and debugging hellish excersises by assigning values to variables either called the same as the globals or the globals temselves. With functional languages you never have that problem because your function does not modify outer or inner functions; whole classes of problems just go away once you drop the concept of `having side effects'.

---

