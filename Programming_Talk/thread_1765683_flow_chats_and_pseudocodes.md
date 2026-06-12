---
title: "flow chats and pseudocodes"
date: 2011-05-23
forum: Programming Talk
---

### Post by android272 on 2011-05-23
so Im taking a logic and design class at DeVry and we are doing flow chats and pseudocodes. my professor seas that you should do one or the other for all code. that if I do this it will make programming so much easier and less time consuming.

but in my opinion they seem to take more time.  flow charts seem to be a complete wast of time, but pseudocodes seem more useful because you can easily just convert to real code, but why not just code.

---

### Post by simeon87 on 2011-05-23
Pseudocode is useful for explaining algorithms to technical people.

Flow charts are useful for explaining basic algorithms to non-technical people.

When you're programming yourself, they're a waste of time.

---

### Post by Barrucadu on 2011-05-23
They can be helpful (high level flow charts in particular) if you're working in a team, to ensure that everyone knows exactly what's going on, but I would say that, for the most part, they're completely useless unless you're very new to programming and so haven't really got into the "programmer mindset" yet.

---

### Post by JupiterV2 on 2011-05-23
Maybe I'm missing the point but, speaking from personal experience, planning your project will save you a lot of grief. While perhaps a flowchart or pseudo-code specifically may not be of much help, if you spend the majority of your time on design you'll find you'll have less bugs, clearer code, and a more robust program. An example I once read:

If you spend 20% of your time planning you'll spend 80% of your time coding and debugging. Conversely, if you spending 80% of your time planning then you'll spend 20% of your time coding and debugging. Why is this significant? Because coding and debugging take a lot more time than planning. Design a good program and you'll not only create a better product, you'll save yourself a lot of time.

So, perhaps this is what your professor is trying to demonstrate? Or perhaps they're trying to round out your education for when you have to demonstrate/justify your design to the rest of your programming team? Or when you have to do a little PR because you're a project lead, or you have to provide the data to your project lead, and need to demonstrate to your audience (a prospective client, for example) what you are trying to do? What if you've designed an API and you need to explain the design flow to your users/fellow programmers?

I suppose it depends on your goals as a programmer.

---

### Post by Barrucadu on 2011-05-23
Of course planning is important, but I find flowcharts and pseudocode a pretty inefficient way of doing it. I plan things in a very much top-down approach - I need to make a program to do X. What are the constituent parts of X? What are the constituent parts of those? Et cetera. Unless it's a particularly big project, that doesn't seem to take much time though.

---

### Post by Mr. Shannon on 2011-05-23
I had one professor that required both and another that required neither.  My personal opinion is that when you are learning, too much planning can waste time since you don't know what's possible yet.  My preferred method is either to just start coding (very small projects) or to write the comments and then fill in with code (larger or more complicated projects).  I see flow charts as useful only when you don't get too detailed with them, otherwise they waste a lot of time.

When you are programing something on your own, then choose the method that makes coding easier for you.  Otherwise, we must put up with our professors methods, however unproductive they seem.

PS: my largest program so far was around 2000 lines, including documentation, so I would not consider myself the best source for this information

---

### Post by PaulM1985 on 2011-05-23
I have been trying to start some fairly large projects on my own recently and if I had been purely coding I am fairly sure I would have come stuck.

By drawing flow diagrams and sometimes just writing down a user work flow, it allowed me to:
1) Get bogged down in the little details in some areas of my app without forgetting the overall picture and user experience of the whole system.
2) Allow me to leave the development altogether for a couple of weeks and be able to get back into it easily whereas I expect I would have struggled without my notes.
3) Identify error cases that I hadn't previously considered.  Drawing up a flow diagram can make you think of all possible events that can happen and think more from a users perspective, whereas when I am straight coding, I tend to just think about the standard success case and hope to come back to the error cases at a later date (and usually forget to).

These are just a few examples for someone working on their own.  If you were to be working within a large team or providing information to clients this sort of information would be very useful there too (as explained in some of the previous posts in this thread).

Paul

---

### Post by r-senior on 2011-05-23
I make mind maps. People think I'm weird. I don't care.

---

### Post by android272 on 2011-05-24
so I guess that I need to do some real coding before I will understand what they are needed for.  I have done some coding but the biggest iv done was 60 lines real code and 150 lines in a program that did not coding for me. 

flowcharts still seem to time consuming, but ill see how they get as the classes go. pseudocodes are becoming my Favorite of the two because it can be easily turned into real code.

the good news is that my professor seas that companies in Ohio are leaning to pseudocodes

---

### Post by slavik on 2011-05-25
> **simeon87 said:**
> Pseudocode is useful for explaining algorithms to technical people.

Flow charts are useful for explaining basic algorithms to non-technical people.

When you're programming yourself, they're a waste of time.
you are wrong.

if you have some complex logic, it can be possible to draw it out via chart/pseudocode and the real code will simply work.

sidenote: I once spent 2 month on pseudo code for a logic, took me a day to write the code.

---

### Post by simeon87 on 2011-05-25
> **slavik said:**
> you are wrong.

if you have some complex logic, it can be possible to draw it out via chart/pseudocode and the real code will simply work.

sidenote: I once spent 2 month on pseudo code for a logic, took me a day to write the code.

Without further elaboration, I can't see whether your 2 months + 1 day could have been shortened if you had done some prototyping and experimental implementations along the way.

Either way exceptions prove the rule.

Most programming work can be divided into smaller tasks that can be connected to each other later (create a data structure, create a mechanism for sending data to a server, create a small rendering loop, etc and you end up with a video game). If you're doing mathematical or very technical programming then you'll naturally be thinking more about the steps that need to be performed.

---

### Post by Blackbug on 2011-05-25
I had same opinion about flowcharts, pseudocodes, class diagram, sequence diagram a year back. I used to hate myself making design and these diagrams.
But, now I am realising their importance.
 
If you make your design efficient you will save more than 50% time wastage while coding. Because when design is clear coding is not far from reach. But, if you start coding before being clear on design, you will stuck on many points and may be will have to start from scratch again.
 
But, everyone realizes its importance with experience, initially almost everyone hates it..

---

### Post by Tony Flury on 2011-05-25
I would not neccessarily say that flow charts and pseudocode are the best tehcnique, but i would advocate some form of design methodology.

I have found doing UML type graphical designs, (Class diagrams, ERD etc) are useful techniques, especially when doing OOP. Doing prototyping as part of the design process is very powerful too.

---

### Post by slavik on 2011-05-25
> **simeon87 said:**
> Without further elaboration, I can't see whether your 2 months + 1 day could have been shortened if you had done some prototyping and experimental implementations along the way.

Either way exceptions prove the rule.

Most programming work can be divided into smaller tasks that can be connected to each other later (create a data structure, create a mechanism for sending data to a server, create a small rendering loop, etc and you end up with a video game). If you're doing mathematical or very technical programming then you'll naturally be thinking more about the steps that need to be performed.
what I am saying is that the prototyping was done on paper.

---

### Post by rg4w on 2011-05-25
I make GUI apps so I start with a clear understanding of the user's workflow, both within the app and the things that happen just before and just after using the app (no matter how complete an app is it's always a sort of "middleware" in the user's workflow).  I often use flowcharts for that.

But before I dive into the algos that make that UI happen, I keep in mind an old maxim I came across:  "Show me your data structures and I'll show you your algorithm."  So before I write any code I'll usually define the data structures the code will need to support the workflow.

By the time I have a clear understanding of what the program needs to do for the user and the data structures to support that, the algos pretty much write themselves.

I don't do much in the way of psuedocode since most of my work is in a language so high-level (LiveCode) that it reads like psuedocode anyway.

---

