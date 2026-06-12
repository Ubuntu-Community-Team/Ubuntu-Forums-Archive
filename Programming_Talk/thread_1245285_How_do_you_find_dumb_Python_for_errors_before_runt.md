---
title: "How do you find dumb Python for errors before runtime?"
date: 2009-08-20
forum: Programming Talk
---

### Post by skullmunky on 2009-08-20
Coming from C++, I'm used to the compiler catching all my dumb typos, undeclared variables, wrong argument counts, etc.  How do you check a python program before running it?  

I have an app that just died in an embarrassingly public way b/c of a typo in a variable assignment which then led to an index out-of-bounds error which then ... well you get the idea.  How do you check for this kind of stuff in Python at coding time instead of runtime?

---

### Post by wmcbrine on 2009-08-20
You don't.

Test thoroughly before deployment, and stop making  so many typos, that's my advice.

---

### Post by Copernicus1234 on 2009-08-20
All languages that use a runtime environment work the same. You cant compare them with C.

---

### Post by pepperphd on 2009-08-20
You should always thoroughly test your programs, whether they are written in C, Python, or whatever.  C will let you compile and run a program with an uninitialized pointer so you can't rely on it to find errors for you. C will let you compile a program with if(i = 0){}, which I can't see for any reason being what you intended to write.

---

### Post by Jacks0n on 2009-08-20
As wmcbrine said, you pretty well don't. That's the downside of dynamic languages. However there's tools out there that can check for that stuff if you're after that. They're not 100% perfect but they're very helpful at times.

Try [pylint]("http://pypi.python.org/pypi/pylint") and [pychecker]("http://pychecker.sourceforge.net/"). If you use an IDE I'm sure you can write a script to run one of them, then execute the script.

---

### Post by skullmunky on 2009-08-21
@wmcbrine: hehe, true. 

@JacksOn: thanks, I'll try pylint.  It'll be helpful for cases like mine where the time required to generate the error during runtime is greater than the available time between beginning of coding and the deployment deadline...

---

