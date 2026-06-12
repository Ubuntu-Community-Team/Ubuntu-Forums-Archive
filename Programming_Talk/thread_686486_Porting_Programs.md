---
title: "Porting Programs"
date: 2008-02-03
forum: Programming Talk
---

### Post by jayk121121 on 2008-02-03
When people talk about porting a program to a different OS, what does that mean?  As long as you have the source code, shouldn't it just be a matter of recompiling it?  What exactly do people change in the source code when they port it?  :confused:

P.S.  Sorry for all the questions.

P.P.S.  I am not a C programming expert.  I only know the basic idea (you write source code and then you compile it into machine code).  Please take that into consideration when you answer.

---

### Post by LaRoza on 2008-02-03
> **jayk121121 said:**
> When people talk about porting a program to a different OS, what does that mean?  As long as you have the source code, shouldn't it just be a matter of recompiling it?  What exactly do people change in the source code when they port it?  :confused:

P.S.  Sorry for all the questions.

P.P.S.  I am not a C programming expert.  I only know the basic idea (you write source code and then you compile it into machine code).  Please take that into consideration when you answer.

It depends on the program. For all Ansii C programs, yes, recompile with an Ansii compiler. You can use gcc on Windows and Linux for this (among others).

If you are using libraries, like GTK, you would have to have those libraries available. GTK is available for Windows, so you could do most GTK apps for Windows.

If you are using the lower level aspects of the operating system, it gets trickier or impossible. 

If you are still learning, learn the standards, then go into specific libraries. 

You will see how much or how little the operating system matters depending on what you are using and what you are trying to accomplish.

---

### Post by pmasiar on 2008-02-03
Many programmers selected one platform over the other because it has some features they need for the application. So they may use those features - and as a result, app is not easy to port to another platform.

---

