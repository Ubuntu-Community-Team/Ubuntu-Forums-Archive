---
title: "js: knows the theory but never know how to use it"
date: 2015-10-24
forum: Programming Talk
---

### Post by trigone on 2015-10-24
hi, ):P

here's my issue: i know a good amount of theoretical knowledge about js coding (far from an expert, although it's (relatively) always relative, but with an extensive enough knowledge on the capabilities and properties, and even the good practices to have regarding this language).

yet, whenever i try to write any program, even any bit of code, i just get blocked, frozen, due to the simple fact that i don't seem to know how to use in practice what i know theoretically: i don't know what to begin with, where to store the data, how the program will articulate. in short, i know the theory, but for the practical aspect, i'm nearly completely incapable of anything. tha's exceptionally tiresome, especially since i have currently, for months now, a project that's very important to me that i keep rewriting again and again (or rather, merely a draft of it), without apparently moving forward one bit --and i'm quite sure this project isn't even  that complicated at all (still, not a tic tac toe of course!).

i wonder if anyone would have ideas, tips, references, to help me learn how to write complex enough  programs in JS, considering i already know quite enough (and even if i have a lack for a specific task, i'd just need to learn about it, it's not my problem here).

now, my first intuition would be of course to learn by example of actual code --but it's rather hard to find (foremost due to common use of obfuscation and else), one that has a not too high level of complexity, and for which the "noisy" specificities wouldn't be too numerous. so, as another possible type of help, i'd love to get links to code instructive enough, but still nonetheless understandable (a need for a bit of patience doesn't bother me, i am persevering).
by the way, if possible, i'd prefer plain js code, rather than jQuery-or-the-like heavy transformation of the programming experience (although the libraries like underscore aren't a problem, since they aid the programming without taking it over entirely).

thanks a lot in advance to all that would answer this thread :D

have a nice day!

---

### Post by tgalati4 on 2015-10-25
Perhaps describe the Use Case for your project.  "A User will sit down and use your code to do what?"  If you can describe your problem or what you are trying to perform, then that is one step forward to solving it.

After that, try decomposition; break a big problem down into smaller problems.  Write pseudo code to describe the steps needed to solve these smaller problems.  Once that is done, using js or any suitable language to code up the pseudo code should be obvious.

If you are looking for a js tutorial on how to write complicated code without a Use Case, I don't know of one.  I have gone through some of these:

[http://ejohn.org/apps/learn/](http://ejohn.org/apps/learn/)

[http://htmldog.com/guides/javascript/advanced/](http://htmldog.com/guides/javascript/advanced/)

Perhaps I am missing the point completely.

---

### Post by trigone on 2015-10-25
No your advises are wise. I think it's because i can't find the words to explain my problem.

I'd say the closer concept to my specific lacking would be that of paradigm: like eg a functional programmer going for the first time towards OO, or vice versa. It wouldn't be for lack of knowing the basic blocks of the language (and i include in this, more "advanced" topics like in your links* (closure, js-style inheritance, ..., and the various uses of these, like currying for example)), but at first it would appear very hard to consider what to start by, and where to put the functions, the variables.

for example, an OO programmer will typically create conceptual objects and put functions in it; the functional programmer will use a more or less verb-centered coding structure. it's mostly about the choice, and the intuition, of the structure of the code necessary, or even adequate, to any big enough task i want to accomplish, that seems to be lacking. the theory, i got it. i know how the code works, and how to do a simple, small task. and to some extent i could cut down into pieces some task, but what would be lacking is the global view of how all this system is going to actually work. i don't know which part should be separated one from another: as an example do i separate the inter-object/variable/database "communication" system from all elements, or do i insert it more or less generically into each element, more OO-style? and to which extent one is easier to write and/or conceptualize?
in short, i lack practical knowledge ^^ i know i should just code and code again, but it doesn't appear to "click" with time, and so i feel like i lack some crucial knowledge ...

not really sure if i'm clearer now than earlier... :/

* = to be more clear on that subject, i'd say i've got about the theory  level obtained when finishing those "advanced" tutorials on the language  structure, plus miscellaneous tidbits.

---

### Post by tgalati4 on 2015-10-25
Refactoring code is part of the process.

Make it work.
Make it work pretty.
Make it work elegantly.

Many times the initial approach to get some program to work is quick and dirty.  So you try to clean it up and make it look pretty, but then it is too slow to accomplish what you want.  Then you attempt to make it elegant.  And that may take refactoring.  Writing from scratch with a new architecture--perhaps using a different database and a different set of graphics frameworks.  

Functional versus object oriented, use what is easier or quicker to get something working.  Only with working code and preliminary functionality can you assess what programming approach is best.  You might program a web page operation using an Object Oriented approach and it works for a few users, but then when 1,000 users slam it, it breaks down.  So you refactor it with a functional approach, profiling it, and rewriting it using a different language, different widgets, different toolkit, to get the performance that you need.

It's a hard process to describe without a working example.

---

### Post by mystics on 2015-10-25
> **trigone said:**
> i know i should just code and code again, but it doesn't appear to "click" with time, and so i feel like i lack some crucial knowledge ...

Not clicking is very common. You really can't get better at programming unless you practice, and it may take seeing something a few times before you end up just doing it naturally. How much coding experience do you have with JavaScript? I'm assuming you have at least some, but it sounds to me like you built up a lot of theoretical knowledge without doing much in terms of code examples. If I'm wrong, what have you done so far?

Also, don't feel ashamed about using Google to find an answer to a problem. Ideally, when you're learning, you want to put in the effort to figure out the solution to the problem, but there's no shame in looking up syntax or reading what others have to say about the problem. It will help your understanding of the language to grow, and if you already understand a lot of the theory, then the practical should come a lot easier to someone who never bothers with the theory.

Overall, try not to get discouraged by having trouble. Programming is challenging, and as much as you've probably already heard about it, practice is absolutely critical to learning how to program. And if you come across an answer to a question you have, pick it apart and figure out why it works. This goes beyond just simple syntax but down into the logic the person used to reach that conclusion. It may not make perfect sense the first time, and you may need to see things a few times before it really starts just coming naturally, but it will go a long way to solving problems, some of which you may never have seen.

---

### Post by Dimarchi on 2015-10-26
To some extent, complex is a collection of simple things...just lots and lots of them. Thus, my advice is to start with the simplest thing your project may require and build upon it. You may find yourself refactoring what you have written so far after a while and that is a good thing. You are learning. Keep on practising!

Does it have to be something related to your project? No - you can apply what you learn in any case. I'm merely saying what has been said above, just in a different fashion.

---

### Post by trigone on 2015-10-26
thanks for all those advices! i'm going to try to put them into practice, and see if time does the trick :)

---

### Post by hoboy on 2015-10-26
Hi trigone.

Few years back I wrote something similar to your question.
There is a difference between theories  of a languages, platforms and  problem solving.
programming is about problem solving.
Learn to solve problems first on paper, never start to program a task before having a clear solution.
when you have the solution, start with the simplest flow.
by using Js, and look the net how others have solved the same problem, but never copy paste do the effort to type.
and learn how to read the api and understand how to recognized a function that will give you the data you need in the solution of the your problem.
Many people said code first, but my problem was code what ?
Good luck you will get there

---

### Post by tgalati4 on 2015-10-26
What hoboy said is quite true.  In a perfect world, you will have all the time and resources to fully develop a Problem Statement, Explicit and Implicit Requirements, a Requirements Flowdown, and a Specifications Document--what the code is supposed to do.  You could spend months developing this, and not write one line of code.  This is a classic Systems Engineering approach.  

To speed up the process, Agile Programming was developed which starts with a Use Case, uses multiple, quick cycles to develop a new application and phases of improvement over time.  

Now Dev/Ops is a method getting developers and operators together to shorten code development cycles by getting early feedback and continuous unit testing--more programming may be used in making reliability tests than the actual code to perform a service.

So, yes, problem solving is important to all three methods.

---

