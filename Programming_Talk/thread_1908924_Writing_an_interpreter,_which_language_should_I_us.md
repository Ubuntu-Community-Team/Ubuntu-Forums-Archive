---
title: "Writing an interpreter, which language should I use?"
date: 2012-01-14
forum: Programming Talk
---

### Post by Kimm on 2012-01-14
Hey guys!

As a 15ECT project course at my university I'll be writing a scriptable animal population simulator. The idea is that the user writes scripts that determine what happens to individual animals each year.

Now, I'm not sure which would be the best language to write it in. I would like it to be cross-platform, and I will make it a terminal application so essentially any language should work! I have more experience with C# than any other language, but I'm not sure if this is suitable for the purpose (also not sure if I want to put the ability to run the software in the hands of a single company (Microsoft)). I also have some experience with C++ using Qt4, this could also work. I have never written anything in Java, but I might concider learning it. Other than these languages I've concidered Objective-C since it appears to have simple ways of managing strings and lists, but I have never even touched it!

Any ideas? I've never written an interpreter before, so this will be a big project for me.

---

### Post by CptPicard on 2012-01-14
Some Lisp variant, maybe Scheme. They're great for interpreters, and in the process of learning how languages translate into other languages and how program execution is evaluation of programming language expressions, you'll learn a lot about programming in general as well.

---

### Post by Tony Flury on 2012-01-14
I would also consider Python to be an option, due to it's good input, string, list and general data handling abilities.

To be honest - for a project like this - go with a language you are comfortable with.

---

### Post by MadCow108 on 2012-01-14
pypy is certainly one of the most interesting ways to write interpreters, you get a jit compiler (almost) for free:


[Tutorial: Writing an Interpreter with PyPy, Part 1](http://morepypy.blogspot.com/2011/04/tutorial-writing-interpreter-with-pypy.html)

[Tutorial Part 2: Adding a JIT](http://morepypy.blogspot.com/2011/04/tutorial-part-2-adding-jit.html)

---

