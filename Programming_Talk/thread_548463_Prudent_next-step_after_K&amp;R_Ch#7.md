---
title: "Prudent next-step after K&amp;R Ch#7"
date: 2007-09-11
forum: Programming Talk
---

### Post by nss0000 on 2007-09-11
Gents:

Continuing my tutorial expedition into C-land. I'd appreciate a considered opinon ... have just coded my tutorial way through K&R Ch#7 ... as to the next-prudent learning step. No question here of my having "mastered" all the material --- but now, I sure get a lot more worried a lot faster when coding ....  %^\ 

Anyrate I can imagine several  plausable next-steps:

1) Pick a non-trivial text/numeric exercise and code thru-it.

2) Study "system"(?)/Linux coding issues ...(ie) move away from application type coding.

3) Graphic coding in Linux.

4) ??

I do want my choice and effort leading toward a solid overall(?) and growing ability to attack C/Linux/hardware coding tasks. Being semi-retired does have benefits ... short-term I can make robust choices and need please noone , but myself.  

Any advice appreciated.

---

### Post by samjh on 2007-09-11
Whatever takes your fancy. :)

If you're interested in tinkering with lower-level stuff, start by learning about network programming using C.

Programming using BSD Sockets will not require you to study computer systems engineering, but it is low-level enough to get you thinking in terms of bits and bytes, rather than the more abstract representations of data you are probably used to.  Oh, and screwing up with network programming probably will not crash your computer (something that can easily happen if you try to tackle low-level programming too early).

Start with a brief overview here: [http://en.wikipedia.org/wiki/Berkeley_sockets](http://en.wikipedia.org/wiki/Berkeley_sockets)

And then get down and dirty here:
[http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

As a project, try to see if you can make a program that will retrieve files from websites, like a very basic derivative of the [wget](http://www.gnu.org/software/wget/) utility.

After that, you will be well-prepared to tackle things like encryption, multimedia encoding/decoding, and low-level tasks that sit between the very complicated area of kernel development and the more abstract area of user applications.

---

### Post by pmasiar on 2007-09-11
There are couple good resources for training tasks:

* [Project Euler](http://projecteuler.net/index.php?section=view) - numerical tasks
* [my wiki :-) ](http://learnpython.pbwiki.com/#Solvingproblems) collects task for learners. I recommentd Python for learners, but you can solve them in C too.
* link above has also book "Etudes for programmers" which is IMHO the best book with tasks to solve
* after you are done with it, pick a open source project doing something you like, and join it. Every project likes to get new develpers on board, and will help newcomers willing to learn. As an old-timer, you might like [http://en.wikipedia.org/wiki/Midnight_commander](http://en.wikipedia.org/wiki/Midnight_commander) - after 25 years, still no better file manager was invented.

---

### Post by Mirrorball on 2007-09-11
Are you new to programming or just new to C? If you are new to programming (maybe even if you aren't), I suggest you start studying good coding practices. Hopefully you will never have to maintain your own messy code. Nothing is more depressing than looking at code you wrote yourself and having no idea what each function does and how to modify the program, and when you modify it, you introduce a thousand bugs. The book Code Complete is great for this. It has tips for naming variables, organizing code in functions, writing comments etc.

Then I'd start my own project, something fun like a game, whatever you want. At the same time, I'd learn an object oriented language: Python, Ruby, Java, C++ etc. Learning Python or Ruby will give you the HUGE advantage of knowing a very high level scripting language. It will make your life 10 times easier.

---

### Post by LaRoza on 2007-09-11
> **Mirrorball said:**
> 
 I'd learn an object oriented language: Python, Ruby, Java, C++ etc.

+1 for Python, but you could also go to a lower level, with Assembly. Even if you don't use Assembly, it is good to know so you better understand how C (and higher languages) work.

---

### Post by Mirrorball on 2007-09-11
Assembly would be my next step after Python.

---

