---
title: "which language?"
date: 2008-08-23
forum: Programming Talk
---

### Post by jrockpunk1 on 2008-08-23
OK so I know C and C++, and have dabbled in a lot of other languages for about a day, then stopped. I've had Ubuntu before, twice in fact. I just want your opinion on which language is "best" for linux programming. I mean languages which are good for doing stuff like creating programs to manage linux servers, create GUI's for the KDE environment, and things to do with linux in general.

I've heard that C, perl and Lisp could be good.

I know a lot of C, and have done a bit of perl, but don't know if they're what I'm looking for. I've also been looking at Lisp, but there doen't seem to be a great deal of tutorials, or people who use Lisp at all, for that matter.

Please reply and tell me which you think would suit me best (not just out of those that I've mentioned).


Thanks in advance.

---

### Post by cmay on 2008-08-23
try read the sticky.
there are lots of useful information there.

---

### Post by jimi_hendrix on 2008-08-23
pythons big in the open source world

---

### Post by nvteighen on 2008-08-23
First, read the Sticky, even if you're an experienced programmer.

Knowing C and C++, I'd jump to a dynamically typed language. Have you tried Python? People here will be able to explain better its benefits than I can, but it's a nice language that allows you to program straight to the problem without the usual time loss you suffer in C and C++ related to memory management or building whole data structure implementations for everything.

> 
I've also been looking at Lisp, but there doen't seem to be a great deal of tutorials, or people who use Lisp at all, for that matter.


"Lisp" is like "Linux distros". There no such thing called "Lisp", but a variety of languages that are called "Lisp dialects". There are two mainstream of these: Common Lisp and Scheme, both differ radically on philosophy but still are "Lisp"... mysteriously... :) 

Search for resources on those and you'll find some nice people doing nice things in Lisp.

Anyway, the Sticky has resources on both.

---

### Post by LaRoza on 2008-08-23
> **jrockpunk1 said:**
> OK so I know C and C++, and have dabbled in a lot of other languages for about a day, then stopped. I've had Ubuntu before, twice in fact. I just want your opinion on which language is "best" for linux programming. I mean languages which are good for doing stuff like creating programs to manage linux servers, create GUI's for the KDE environment, and things to do with linux in general.


For Linux programming, C is a must. For Ubuntu, Python is important to know.

KDE uses QT libraries for GUI's, and QT is available for Python.

You said you did a little Perl before, why not continue that?

> 
I know a lot of C, and have done a bit of perl, but don't know if they're what I'm looking for. I've also been looking at Lisp, but there doen't seem to be a great deal of tutorials, or people who use Lisp at all, for that matter.


There are many people who use Lisp, they just aren't code monkies ;)

See my language selector (see my home page, learn to program in my sig) and see what it tells you.

---

### Post by Reiger on 2008-08-23
If you want Lisp you may want to look at a slightly more modern language such as Haskell? If only because you ask about easy to find documentation regarding API's and such; which is exactly what Haskell has through Hoogle.

---

### Post by Kadrus on 2008-08-23
> or people who use Lisp at all, for that matter.
Last time i checked,around 300 lisp hackers were  hanging in lisp's IRC channel(thats not a bad number)..
read [practical common lisp]("http://www.gigamonkeys.com/book/"),and [ANSI Common Lisp]("http://www.paulgraham.com/acl.html").
Python is mostly used in Ubuntu.
read [Read Rapid GUI Programming with Python and QT]("http://www.amazon.com/Programming-Python-Prentice-Software-Development/dp/0132354187") to learn how to develop applications under KDE.

---

### Post by pmasiar on 2008-08-23
> **jrockpunk1 said:**
> which language is "best" for linux programming. I mean languages which are good for doing stuff like creating programs to manage linux servers, create GUI's for the KDE environment, and things to do with linux in general.


You need to think more what exactly you want.
 
Linux is (strictly speaking) the kernel, written in C (with sprinkled ASM), but unless you are expert on low-level systems programming there is hardly anything to do for you.

Linux distribution, like Ubuntu, is vast universe of thousands packages written in dozen languages, with souple dozen API library families, no human can know them all. So you need to decide in which little corner you want to "put your stake", learn what is used there, and contribute. And there are many many programs as interesting, but not included in any distro.

Many people contribute to what they use at work, or as hobby (you need a lot of time to learn enough become proficient). So unless you give us more info, all suggestions what to do would be on personal preferences of the poster, not relevant to you.

Now, separate (more generic, so easier) issue is, which languages should competent programmer know.

Every programmer should know C, and possibly C++, check. Also, at least one dynamically typed language. There are 4 popular: Perl, Python, Ruby and PHP. Perl is most popular, but also rather quirky and most obsolete. PHP was designed specifically for web pages, and it's design is very quirky and not guiding programmer to good practices. 

From remaining two (which are 99% similar), I have slight preference to Python, because is little older, community is little bigger, little more books, libraries, and is little farther from Perl's quirks. But if someone around you can help you with Ruby and not Python, go for Ruby, as they are 99% same. If you need info/ebooks/training task for Python, see wiki in my sig.

But these are still pretty standard languages. After that, you may consider learning more languages, and more different: any dialect of Lisp; Prolog; Forth; Haskel - there are plenty. You may also consider learning Java or C#, if you think it will give you chance for better job - but more interesting (if rarer) are in those more "agile" languages - you will understand when you learn one.

So, there are no silver bullet - language is a tool to solve specific class of problems. C is good match for task where speed is of utmost importance - you will be surprised for how many task speed of development is **much** more important than speed of running code. And in the end, you glue system from partial solutions in different languages, as needed.

---

### Post by CptPicard on 2008-08-23
> **Reiger said:**
> If you want Lisp you may want to look at a slightly more modern language such as Haskell?

Well, seriously now, Lisp isn't "archaic", and Lisp has its strong points which are quite separate from Haskell's :) 

Haskell may be newer, but it is also substantially different -- pure-functionality really makes stuff harder in general (for example, I still can't really model stuff in terms of Monads so I can't really say I'm able to 100% use the language). The big huge Point of Lisp is the homoiconic structure that allows for the macro system, not necessarily the fact that you can (and often do) code in functional style in it.

---

### Post by Kadrus on 2008-08-23
> If you want Lisp you may want to look at a slightly more modern language such as Haskell?
Lisp !=Haskell.
They are both different languages,Haskell is a purely functional,modular programming language.
Lisp is a multi-paradigm programming language that has ***functional*** aspects.
You should not recommend Haskell as it's alternative.

---

### Post by jrockpunk1 on 2008-08-24
Sorry I've only just got back to you all. Thanks for all your help. And I'll answer a few questions. Basically, for someone who said there are lots of languages needed to learn to do everything, I just want to be able to do as much as possible with linux. I've heard that linux is the best OS for security, networking and business etc etc. Some things I might want to program would be: A firewall, An IRC bot, a game etc. Just stuff to test my skills. And I've already tried haskell (in my list of one-dayers :P) and hated it, purely for the resources it uses and the... strangeness of it? Anyway thanks for your help, and I'm going to have a go with python and go back to perl, and also brush up on my C. And I meant common Lisp for those who asked :D

Thanks for helping everyone, I can't believe I got that many comments overnight

---

### Post by Reiger on 2008-08-24
> **Kadrus said:**
> Lisp !=Haskell.
They are both different languages,Haskell is a purely functional,modular programming language.
Lisp is a multi-paradigm programming language that has ***functional*** aspects.
You should not recommend Haskell as it's alternative.

Of course Lisp!=Haskell; but quite a few of the ideas in/of Lisp are present in Haskell also. Given that Haskell has a slightly more convenient (IMHO of course) syntax; and a lot of safety/convenience features, you may be able to do more with Lisp sooner if you've seen basic Haskell first.

Just don't get addicted to Lazy Evaluation. :D

---

### Post by Reiger on 2008-08-24
> **jrockpunk1 said:**
> purely for the resources it uses and the... strangeness of it? 

Resources? Depends on what you do with it -- which is to say: if you do really imperative stuff in Haskell you have to be fairly advanced to do it efficiently; but on the other hand if you try some of the hardcore functional stuff in an imperative language you better e really good at those too.

Strangeness? It's a language which is built around functions, so if you have never seen at least some of the concepts of Relations or Predicate Logic you may think it's somewhat awkward. That'll go away if you try to code in it for longer than just 1 day.

---

### Post by nvteighen on 2008-08-24
> **Reiger said:**
> Of course Lisp!=Haskell; but quite a few of the ideas in/of Lisp are present in Haskell also. Given that Haskell has a slightly more convenient (IMHO of course) syntax; and a lot of safety/convenience features, you may be able to do more with Lisp sooner if you've seen basic Haskell first.

Well, Lisp's syntax may be ackward because of the parentheses, but with a good editor that keeps track of them you get rid of that problem.

The nice thing in Lisp is that Data = Code. So, the syntax is absolutely minimal: (procedure data) and nothing else... (I'm excluding syntactic sugars like the '(1 2 3) which actually stands for (quote 1 2 3)) of course, your data can also be a procedure with several arguments which some turn to be a list, etc... So you end up having a all-purpose syntax for just everything.

> **Reiger said:**
> 
Strangeness? It's a language which is built around functions, so if you have never seen at least some of the concepts of Relations or Predicate Logic you may think it's somewhat awkward. That'll go away if you try to code in it for longer than just 1 day.

All languages will look strange if you only know C-like languages... :) (which is the OP's case)

I'd suggest you to also look at Python's basic functional programming abilities (reduce(), filter(), map() and list comprehensions). It might be a good start to see what that paradigm is about.

---

### Post by jrockpunk1 on 2008-08-24
thanks again everyone, and yeah it seemed strage to me, but I've had another look at it, and it seems not quite as strange. This is the page that threw me off:
[http://www.haskell.org/~pairwise/intro/section1.html#part1](http://www.haskell.org/~pairwise/intro/section1.html#part1)
So, time for a vote people. Which do you think I should learn out of: Python, Perl, Common Lisp, or haskell?

---

### Post by CptPicard on 2008-08-24
Python, by all means. You get some feel for functional "aspects" when you get more advanced with it.

---

### Post by LaRoza on 2008-08-24
> **jrockpunk1 said:**
> 
So, time for a vote people. Which do you think I should learn out of: Python, Perl, Common Lisp, or haskell?

I think you should get a tattoo instead.

See? That is what you get when you have information, yet ask random people for suggestions ;)

Learn whatever you want. You have some information on all.

---

### Post by Reiger on 2008-08-24
> **jrockpunk1 said:**
> thanks again everyone, and yeah it seemed strage to me, but I've had another look at it, and it seems not quite as strange. This is the page that threw me off:
[http://www.haskell.org/~pairwise/intro/section1.html#part1](http://www.haskell.org/~pairwise/intro/section1.html#part1)
So, time for a vote people. Which do you think I should learn out of: Python, Perl, Common Lisp, or haskell?

Depends. Want it easy: go with imperative languages such as Python or Perl. Want something completely different (as you already saw for yourself); either one of the other two.

Why does that page throw you off? Assume you were to code the following Haskell fragment in C:
```

module Prime where

primes (x:xs) = x : ( primes (filter (`isRelativePrimeTo` x) xs) )
primes  x	  = x

isRelativePrimeTo = \x y -> x `mod` y /= 0

```

Step by step:
```

Function primes
Case 1 : a list of one element x on front, and tail xs
  Return x on front of the list z;
    Where z = the result of applying *primes* to the list which you get by taking all elements e for which the following yields **True**:    isRelativePrime e x
Case 2 : a list of just one element x
  Return x.

Function isRelativePrime
Case: two values x and y
Return whether the result of x mod y is inequal to 0.

```

How would accomplish that?

---

### Post by jrockpunk1 on 2008-08-24
****, I dno, with a lot of reading and re-learning shiz that I should have remembered :P thanks for the help everyone. I'm going to try haskell first, and python :D

---

### Post by nickgaydos on 2008-08-24
> **jimi_hendrix said:**
> pythons big in the open source world
Agree :)

---

