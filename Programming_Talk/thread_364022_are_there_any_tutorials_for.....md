---
title: "are there any tutorials for...."
date: 2007-02-17
forum: Programming Talk
---

### Post by Choad on 2007-02-17
... for making large scale python/gtk projects

most tutorials about pygtk are just simple 1 window apps and all contained in 1 source file

when i look at a "real world" app its in a bazillion source files and i am overwhelmed, and i cant seem to figure out what the hell is going on

so i was hoping for some kind of introduction to multiple source file apps written in python

thx

---

### Post by WiseElben on 2007-02-18
This would come from experience. Mult-file projects contain multiple files because the project is so large that having multiple files make it easier. Looking at "real project" would of course be overwhelming, but when you are the one writing the source, it becomes simple and sensible. It all simply comes from experience.

---

### Post by Choad on 2007-02-18
well then i think i may have to write a tutorial for it once i understand myself. im finding it really difficult atm, not knowing what should be seperate from what

---

### Post by pmasiar on 2007-02-19
> **Choad said:**
> well then i think i may have to write a tutorial for it once i understand myself. im finding it really difficult atm, not knowing what should be seperate from what

Well most likely you will *not* write the tutorial, and let me explain you why:

- there is many ways to skin the cat. Most of them have results good enough, so looking for the best one is waste of time. Exhibit 1: "which programming language I should use for ..." (see also note1)
- many people have preferences inherited from other projects
- needs of a small project might be rather different from a big project. BUT, small project which grew big may just keep the structure by inertia - it works and there are more important things to do.

So after you will be knowledgeable enough to write such a tutorial, you will also know wnough why writing it is a futile excercise - and have much better, more productive  things to do :-)

You might noticed that advice is very generic. And it is - most big projects are like this.

So dont despair. My advice is (IANAL, IMHO, YMMV):

1) dive into google for hour od so to find "best practices" ot "project how-to" for what you want. Try to read it, but if it does not make sense, skip to next.
2) start coding using what you learned and common sense.
3) later you might get into troubles and *then* many of things from (1) which made no sense then, might be good reading - so create a wiki with your own comments.
4) you can also look at structure af other projects like you plan to do, look for inspiration (if it makes common sense)

And of course have fun!

note1: 
"which programming language I should use for ..." is different from "which programming language I should learn first?". I firmly believe that Python is very good as first programming language, or as single language for someone not deeply interested in programming and in need of simple quick solutions, occasionally. Python is good foundation to build your knowledge of other languages (if you need them). Is suited for (insert some random number here) % of tasks, possibly more than any other single language, but in no way it is ultimate answer to one single language.

Ultimate single language will be of course language 42  [ http://en.wikipedia.org/wiki/The_Answer_to_Life%2C_the_Universe%2C_and_Everything]( http://en.wikipedia.org/wiki/The_Answer_to_Life%2C_the_Universe%2C_and_Everything), but it was not started yet

---

### Post by Choad on 2007-02-19
hehe well i have already started

its a very simple tutorial to write actually

i have a simple 1 window app, then i split up its functionality to create a second window to explain how that works, then i have yet to write an example of taking a complex class/function/whatever and having that in a seperate source file

i will be posting it here, so keep an eye out and give it some criticism when its done (criticism is good)

---

