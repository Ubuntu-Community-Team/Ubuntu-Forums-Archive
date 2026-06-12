---
title: "Haskell IDE/Compiler"
date: 2006-10-26
forum: Programming Talk
---

### Post by Endow on 2006-10-26
What's my best option?

---

### Post by nereid on 2006-10-26
As far as I know there ain't a special Haskell IDE. You can use emacs or vim to write your applications.

The Glascow Haskell Compiler is the only compiler available in Ubuntu (sudo apt-get install ghc6). You can also use Hugs but this is only an interpreter but GHC also contains an interpreter.

---

### Post by tzulberti on 2006-10-26
Hugs (it runs interpreted like Java):
hugs - A Haskell 98 interpreter

hmake:
hmake - The Haskell Make System

It creates an executable. gedit has highlight for Haskell...

---

### Post by coder_ on 2006-10-26
Haskell and FP confuses me... It's very cool and interesting, but confusing...  It's hard for me to grasp full FP.

I think they need an FP-schools channel on freenode, like a couple of the #foo-schools channels that I've heard of.  The "teacher" posts a lesson date/time and all the people that want to participate and learn can go there for an "interactive tutorial" where they can ask questions and try it on their computer in their terminal.  That'd be neat to have.

---

### Post by tzulberti on 2006-10-26
> **coder_ said:**
> Haskell and FP confuses me... It's very cool and interesting, but confusing...  It's hard for me to grasp full FP.


One gets used to it, and I really like it. I have been programming in Functional for one year one (for the university) and i REALLY like it. It is true that if you know C++, C, it is a bit confusing at the beginig...

---

### Post by nereid on 2006-10-27
@tzulberti
What kind of programs do you write in Haskell? It is the same as always, after you have learned a new language you want to use it, but you don't know what to write ;)

---

### Post by tzulberti on 2006-10-27
I have done nothing but excercise for the university... It is a [Functional Language]("http://en.wikipedia.org/wiki/Functional_programming")... It is quite easy once you get used not to create a variable every time you need one... You could do things like fibonacci:

f n = f (n-1) + f (n-2)

Sorry for my english :)

---

