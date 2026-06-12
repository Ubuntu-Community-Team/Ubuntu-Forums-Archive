---
title: "Which LISP implementation are good for a beginner"
date: 2007-06-16
forum: Programming Talk
---

### Post by Masapena on 2007-06-16
At first I clarify what I mean with the word "implementation". Maybe I'm misusing the word, but I want to get something that can compile and interpret code.
 
I'm not a complete beginner in programming. I have tried C++, C and Python and I disliked more or less all of them. They felt too similar IMHO (note that I didn't said that **are** similar). C had too much clutter. C++ was very unfriendly to a beginner and object oriented programming was too difficult to understand for me when I was 12 years old. Python was nice to play around with its inteactivity, but I didn't take it seriously to actually learn anything. Also it kind of reminded me of those C-languages. But Lisp feels entirely different.

But my problem is, what implementation I should choose? There seems to be a lot of the them and their web sites don't tell anything that beginner *can* care about.

I would be intrested in implementations, which...

a)  are general purpose
b) Don't laugh, but I want to compile my code. I have only been able to play around with a "javascript creation" that only intrepted I really don't know what to call that one!
c) have some popularity, so that I can ask questions and actually get answers for them.

I have experience with programming really small, trivial programs and compiling them. So I really don't know, what is a good thing for debugging *more blah blah on things that I really don't know about*.

I also noticed that nobody has written well about learning to program. We have that one thread as a sticky, but isn't enough. I'm going to document my progress, and maybe publish my writings somewhere in the future, to encourage all the noobs in the world.

---

### Post by avik on 2007-06-16
I like CLisp.

```
sudo apt-get install clisp
```

It has an interactive mode, supports compilation, and is quite popular.

---

### Post by HackingYodel on 2007-06-16
Hi Masapena,

MzScheme in the form of [DrScheme]("http://www.plt-scheme.org/software/drscheme/") sounds like a perfect solution for you.

[MzScheme]("http://www.plt-scheme.org/software/mzscheme/"), the language it is based on, is very feature packed.  The ***Learning*** link on the DrScheme page is totally competent and top-of-the-line material.  You can install it form Synaptic or with **apt-get install **if you are using Ubuntu.

Here is its [Language Shootout]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=mzscheme&lang2=python") results versus Python.  Not too shabby, at all.

Give it a try, I think you'll like it.

---

### Post by Limpan on 2007-06-16
I have programmed a bit in Lisp (Allegro Common Lisp) and Scheme (DrScheme) and I must say that I think Scheme is the better/easier one. It's almost the same but some differences makes it simpler and more intuitive. That's my humble opinion, someone else might give you theirs. :D

---

### Post by DougB1958 on 2007-06-16
My advice: go with Scheme. It's a lean, simple, Lisp dialect, which makes it good for a learner. (Common) Lisp is probably more widely used, but it's bigger, and you can scale up to it from Scheme if you want to later.

---

### Post by BugenhagenXIII on 2007-06-16
I'm currently learning CLisp (via Slime and Emacs), following [this]("http://www.gigamonkeys.com/book/") tutorial, and I find it pretty easy to understand.

---

### Post by rickardg on 2007-06-17
> **Masapena said:**
> 

But my problem is, what implementation I should choose? There seems to be a lot of the them and their web sites don't tell anything that beginner *can* care about.


Well, the simple (and annoying) answer is  that it doesn't matter. All of the reasonably mature implementations will work nicely for learning the language. Try some of them, pick the one that feels best/has the most active mailing list/looks best/has the coolest name, stick with it for a few months and when you've learnt the language you know enough to care about the stuff on the web sites.

> a)  are general purpose

Common Lisp is a general purpose language, but even specialised dialects (like Emacs Lisp) would be acceptable for starting to learn the language, even if you'd have to adapt a bit when switching to a Common Lisp or Scheme.

> b) Don't laugh, but I want to compile my code. I have only been able to play around with a "javascript creation" that only intrepted I really don't know what to call that one!

Many Common Lisp implementations always compile your code, even the stuff you type into the interactive prompt. I'm not sure about Scheme, but I'm sure some of them do.

> I have experience with programming really small, trivial programs and compiling them. So I really don't know, what is a good thing for debugging...

All Lisp implementations I know of have debuggers built in (I think it's part of the language), exactly how they work differ between implementations. Some of them can be difficult to use so most people use Emacs and SLIME.

Don't forget the trial versions of the commercial lisps, [Allegro Common Lisp]("http://franz.com/downloads/index.lhtml") and [LispWorks]("http://www.lispworks.com/downloads/index.html") that are easy to setup and great for beginners.

As concrete advise I'd say you'd really should learn to use Emacs and [Slime]("http://common-lisp.net/project/slime/"), and then it matters even less which implementation you choose since Slime hides a lot of the differences from the user. [Steel Bank Common Lisp]("http://sbcl.sourceforge.net/") works great for me and seems quite popular. If you don't want to learn Emacs (which you should.. :-) ) consider Allegro or LispWorks if you want  an IDE or [clisp]("http://clisp.cons.org/") if you prefer the command line and a lesser editor (it's not the lisp way, use emacs and slime instead :-)) Clisp only compiles to bytecode (like Python) but has a much better interactive prompt than SBCL.

If you decide to use Scheme, then [PLT Scheme/DrScheme]("http://www.plt-scheme.org/") is hard to beat as a learning environment.

To sum up:
[LIST]
[*]learn emacs and Slime
[*]SBCL is popular and compiles to native code (like many other lisps)
[*]clisp is also popular and has an easy to use interactive prompt but compiles only to bytecode
[*]Allegro and LispWorks have IDEs and are easy to setup
[*] PLT Scheme/DrScheme is great for learning Scheme
[*] btw, did I mention you really should learn emacs if you are interested in Lisp...? :-)
[/LIST]

All of the above IMHO, YMMV...

---

### Post by nitro_n2o on 2007-06-17
Yes, use Scheme: you can play GnuRobots ;)

---

### Post by Jasper84 on 2007-07-10
[quote=rickardg]consider Allegro or LispWorks if you want an IDE or clisp if you prefer the command line and a lesser editor (it's not the lisp way, use emacs and slime instead ) Clisp only compiles to bytecode (like Python) but has a much better interactive prompt than SBCL.[/quote]
Yes, i wander why it is so hard for them to implement use of the home/end and cursor buttons :(. GNUplot does not use those too. I have been playing around with common lisp quite a bit. I guess one could make an ide, because lisps code can be entered via strings.
I have been playing around with [cl-sdl](http://cl-sdl.sourceforge.net/) a bit, but still to find out how to do stuff like reading in libraries like cl-sdl decently. I should learn declaiming stuff and all too, and i do not know how to get a binary executable.

PS learned most of my common lisp from [http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/), [http://www.cs.cmu.edu/Groups/AI/html/cltl/clm/index.html](http://www.cs.cmu.edu/Groups/AI/html/cltl/clm/index.html)

---

### Post by pmasiar on 2007-07-11
> **Masapena said:**
> tried C++, C and Python and I disliked more or less all of them.

If you want very different programming experience, take a look at [FORTH](http://en.wikipedia.org/wiki/Forth_%28programming_language%29)

It was designed to have full access to hardware (any code snippet can be coded in ASM anytime and links seamlessly). 

Warning: it was *not* designed for average clueless programmer: in words of author, it does not go all over you to protects you from errors good programmer should not be doing. Ie. patching binary code of existing function is allowed (and trivial). Is still used in embedded devices, where it's super-compact code and such tricks can be usefull. 

As I said, *very* different language. One of the kind.

---

### Post by sard on 2007-07-13
[http://www.paragent.com/lisp/cusp/cusp.htm](http://www.paragent.com/lisp/cusp/cusp.htm)

Is a Lisp plugin for Eclipse if you can't quite face Emacs yet.

---

### Post by LaRoza on 2007-07-13
How did Python remind you of C?

If you study it seriously, you'll find it to be very powerful.

---

