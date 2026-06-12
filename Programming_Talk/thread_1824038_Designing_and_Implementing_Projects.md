---
title: "Designing and Implementing Projects"
date: 2011-08-13
forum: Programming Talk
---

### Post by RobikShrestha on 2011-08-13
Hi, 
I wanted ask you guys, how do you do a project? I mean, when I design something, most of the time, I have to change the design during implementation and re-design. Is this the way to go? I have learned about OOP but it's easier said than done. I always manage myself to get into confusing periods, and at that time I curse myself for weak design.

Also, how do you work in a team. Does every member have to understand each other's codes? How to standardize the development??

I want some good suggestions. I want you all to share your experiences so that young developers like me can learn more.

---

### Post by cguy on 2011-08-15
> **RobikShrestha said:**
> Hi, 
I wanted ask you guys, how do you do a project? I mean, when I design something, most of the time, I have to change the design during implementation and re-design. Is this the way to go? I have learned about OOP but it's easier said than done. I always manage myself to get into confusing periods, and at that time I curse myself for weak design.

Also, how do you work in a team. Does every member have to understand each other's codes? How to standardize the development??

I want some good suggestions. I want you all to share your experiences so that young developers like me can learn more.

Think better about the design before starting coding; you could also ask for its review on the forums.
Then, just stick with the plan and focus on getting a working program.
Small changes are not bad; sometimes they just have to be made.

As you write the code, note down the improvements you could have made when doing the design and follow them in the next project. Or, after you finished writing ver. 0.1 of your program, write ver. 0.2 where you improve on one or two areas from the previous version.

You should also use a version control system, for obvious reasons.

---

### Post by RobikShrestha on 2011-08-16
Thanks. That was helpful.

---

### Post by ofnuts on 2011-08-17
> **RobikShrestha said:**
> Hi, 
I wanted ask you guys, how do you do a project? I mean, when I design something, most of the time, I have to change the design during implementation and re-design. Is this the way to go? I have learned about OOP but it's easier said than done. I always manage myself to get into confusing periods, and at that time I curse myself for weak design.

Also, how do you work in a team. Does every member have to understand each other's codes? How to standardize the development??

I want some good suggestions. I want you all to share your experiences so that young developers like me can learn more.Well, that's how you recognize seasoned programmers, their code design needs less rework :) There are books on OO code design usually revolving around "design patterns". Some of them try to masquerade as "methodologies" but they are mostly cookbook recipes. They are still useful to avoid reinventing the wheel, this frees your mind for the real design work.

The two big advantages of OO are:

1) you don't need to know much about an object, only its public method/members. The rest is the author's business.

2) if you know the base class, the derived class is fairly easy to master, you only need to learn the new or overloaded methods. By design you know that everything else is identical.

Refactoring in OO is easy and safe, because OO enforces some degree of isolation, and the IDEs help a lot.

There are source code analyzers that can be used to enforce some common programming style.

Writing efficient, elegant and maintainable code is a long process. It is much faster to cut/paste long tracts of code(*) than to ponder what all these objects have in common and create another class. But the time spent is a long-term investment. Mark Twain wrote: *"I'm sorry [I]I didn't have the time to write you a short letter*, so I wrote you a long note instead". [/I]Mark Twain would have been a good programmer.

Cursing yourself is self-criticism. Self-criticism is good. It is the path to wisdom.

---

### Post by RobikShrestha on 2011-08-21
Thanks that was helpful too. Just wondering why there are not more replies. More suggestions would be more helpful.

---

### Post by GeneralZod on 2011-08-21
Good design is more of an art than a science, so there's only so much advice that people can give.  My advice (as someone who is quite focussed on OOP and TDD) is to read some of the classic OOP texts, and practice, practice, practice. 

I made a (very) short list of such texts in this [old post](http://ubuntuforums.org/showthread.php?t=1596468) (you can ignore the stuff about C++ if that's not the language you're using).

---

### Post by Brandon_R on 2011-08-21
You should separate your presentation from logic. That means try to think and execute them separately. Brainstorm and prototype the design in a designing application then code the logic/algorithms. Some libraries aids you in doing this such as Qt with it's Model/View implementation.

---

### Post by pauljwells on 2011-08-21
OO kind of forces you to write better-structured code and makes it easier to fix bugs; If you can break your program into tiny elements, each one is easier to code cleanly and to test. If you're familiar with procedural code you can think of OO as turbocharged subroutines. I also think it helps if you start with an accessible language like Python.
As a practical bit of advice: I explain what my program will do to 'arts' friends and get them to sketch how they'd do the GUI, I don't always use what they draw but as developers we are mostly 'left brain' types and a 'right brain' perspective can bring up things that we just wouldn't think of.

---

### Post by RobikShrestha on 2011-08-25
Thank you very much. I am doing php project write now and it is much better designed than the last ones because I tried to follow MVC model. However there are still many weaknesses like mixing up tiers. However it is an improvement. Guess the way to go is to do more projects and improve while doing so.

---

