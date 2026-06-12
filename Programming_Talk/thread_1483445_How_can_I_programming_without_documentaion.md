---
title: "How can I programming without documentaion"
date: 2010-05-14
forum: Programming Talk
---

### Post by EftekasatMasreya on 2010-05-14
There are some problems in open source 
when I want to programing some of open source like add some feature or so on 
I faced a big problem ... There isn't documentation about this source???
I Depended on reverse engineering but some times there are some code I can't understand it
I'm Just open this thread to know .. Are there documentation for all open sources or what?

---

### Post by lisati on 2010-05-14
Having good documentation about how a program works sure can help, particularly when you want do modify or adapt something that someone else has written. 

When I was working full time as a programmer many years ago, the companies I worked for encouraged their staff to document things properly. Unfortunately, with software we obtain through the internet, we aren't always afforded that luxury. This leaves us with having to rely on experience, general know-how, and the ability to research how things work.

---

### Post by doas777 on 2010-05-14
each project should provide it's own documentation. if it does not, ask the dev team. if they ahve some they will likely pass it on.

---

### Post by StephenF on 2010-05-14
Is everything fully documented? No. Keeping large amounts of documentation on a fluid codebase requires considerable effort for it to remain in sync.

Whenever documentation is found it will almost certainly be in English though there are automated translation tools available.

---

### Post by HotCupOfJava on 2010-05-15
Yeah, it would be nice to have documentation, but that will frequently NOT be the case. Part of being a programmer is having to sometimes solve the puzzle of what a particular piece of code is trying to accomplish.

---

### Post by mmix on 2010-05-15
[http://en.wikipedia.org/wiki/Software_documentation](http://en.wikipedia.org/wiki/Software_documentation)

[http://en.wikipedia.org/wiki/Literate_programming](http://en.wikipedia.org/wiki/Literate_programming)

---

### Post by nvteighen on 2010-05-15
Just something... Sometimes, when a code base is still very immature, it's more worth not to have documentation because it'd add the cost of mantaining something doomed to be change sooner or later. From my observation, I see that the only documentation available in early stages are code comments and very stubby function-interface descriptions... never full-fledged API documentation.

---

### Post by (&amp;*4h*)#$ on 2010-05-16
In my experience in coding in open source projects (in which we don't follow some rules of software engineering), one of the projects that I handled did not have a separate documentation for what is within the code. Rather, most of the time it is found among the comments in the code, to help you trace what is going on.

Of course, personally, I would prefer having separate documentation describing the structure of the program, but as what some have already mentioned, the development pace might be too fast in order to provide a completely accurate explanation of the structure. Unless, of course, it has reached a stage when overhauls are not very common. (That is, when the project has gone large enough.)

That is when code reading skills might come in handy. Although I do not find that particularly helpful when the project has become extremely large already. (And the structure of their components are not quite clear.)

---

