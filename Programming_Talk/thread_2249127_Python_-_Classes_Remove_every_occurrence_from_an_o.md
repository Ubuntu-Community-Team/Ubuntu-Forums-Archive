---
title: "Python - Classes: Remove every occurrence from an object"
date: 2014-10-19
forum: Programming Talk
---

### Post by Yozuru on 2014-10-19
Hello everyone! 

I am having a lot of trouble with classes, I understand it but I am unable to do this practice problem from my book. 

So I need to make a function that removes every specific occurrence from an object. (Ex: I want to get rid of "goodbye" and it get rid of all occurrences of it)

Currently this is what I have so far(it works great): [http://pastebin.com/qc3xwDVW](http://pastebin.com/qc3xwDVW)

And this is my attempt for the problem: [http://pastebin.com/0Ffntcma](http://pastebin.com/0Ffntcma)

I was thinking about using my erase function and use it in a loop, but I have no idea how to call a function within another one. (I searched around but there was no a lot of useful information on it.)

Any help would be greatly appreciated!

---

### Post by ian-weisser on 2014-10-19
Well, the Forum rules prohibit help with homework assignments.

Stick with it; many of us had trouble wrapping our brains around classes. 



Ignore the following if it confuses you...or if it helps you too much:

Functions do something to whatever data you throw at it. Data in --> function --> data out.
s = delete(paragraph, "goodbye")

Classes may do lots of clever things to specific kinds of data. Data in (init) --> function1 --> function2 --> data out
s = Parareader(paragraph)
s.frobozz()
s.baz()
print(s.delete("goodbye"))


Another way to look at it:

In C, when I have a specific type of data (like Time), I store it in a custom Struct and do all kinds of actions on that data (convert it to UTC, convert it to Epoch seconds, convert it to local timezone), some of which get stored in the struct, too.

When I want to do the same thing in Python, it's time for me to create a Class.

---

### Post by Yozuru on 2014-10-19
Hi Ian!

It is not a homework assignment but a practice problem that I am doing so I can better understand classes. If they are classified the same then I apologize. :)

I will take a look at what you have set out, I really do appreciate the help! I'll keep practicing with classes and hope to get better. :D

---

### Post by ofnuts on 2014-10-20
If you want us to help you could start adding a few comments... What is this class supposed to do? It has a "contents" attribute that sees to be a dictionary... (init with {})? Can you add an exampl of contents? What you are doing is either way to subtle for me, or completely wrong/overly complicated and I tend to think the second solution is somewhat more likely...

---

