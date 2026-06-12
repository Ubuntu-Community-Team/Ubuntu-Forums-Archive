---
title: "Why are larger projects harder to change?"
date: 2011-04-22
forum: Programming Talk
---

### Post by worldsayshi on 2011-04-22
A Philosophical question: I'm currently working on my perhaps largest project in terms of lines of code maintained by myself (I'm working on it alone). Perhaps it's for me the most concise example of seeing the whole process of a project growing simultaneously in size and overhead. For every part I add, the next part gets a little harder (or rather, more work intensive) to integrate. And my choices of how to integrate next part is to some extent limited by every added part. Let's call this tendency 'stagnation'.

0. Do you agree on my formulation of the problem and that there is such? I'm interested in getting a concise understanding of this dynamic:

1. Why (the meta why, or something like that) does this happen? What should be, in general terms, done to avoid 'stagnation' of this sort? As far as contemporary understanding of this goes and as far as my knowledge goes, there is no way to avoid this in the extension. Good programmers can only postpone stagnation somewhat. This 'stagnation' means that a project has to choose between starting over or adding more and more programmers to the project while the added amount of features per time stays the same. When starting over, a lot of the knowledge of how the old system failed can be used to reduce a lot of the overhead, but soon the project will be back in stagnation again.

2. While the skill of the programmer probably is a great factor, what other factors are there? How large role does the language play? Does for example functional programming languages postpone stagnation further than 
(just) object oriented ones?

3. Do you believe that this stagnation can be avoided almost entirely by advances in language technology?

---

### Post by doas777 on 2011-04-22
0- yes, a larger code base requires a larger maintenance effort. this increases based on the amount of code that is shared across usecases. that is a truism. 

1- i wouldn't use the term stagnation. in the end, you choose to start over if the architecture of the application was not fit to the task in totality, or to changes that have been introduced. if the usecases are all known at the beginning, this can only be an indication of a poorly designed architecture. that said, hind sight is 20/20, and there will always be a few kludgy hacks introduced by changes in the requirements with any project of scope. Technical obsolescence of the platforms used may also be a good reason to start anew. Right now for instance, my project team is writing a web-based replacement for a WinForms app. 

2- Object oriented design principals provide a wide array of ways to specialize shared functionality for each usecase with only a minimal addition of code. Inheritance, Interface implementation, and a number of useful design patterns should give you the tools you need to add specialized functionality to a shared code base that has been appropriately designed. As an aside, Refactoring tools are very helpful in extending shared code to handle more specialized cases while maintaining the existing functionality. I've never seriously worked with a functional langague, so can't advise you there. at the same time, I see the principals of encapsulation and extendability inherent in OO as a real boon in this regard. 

3- no, not really. not a langague thing. if you are wrinting new modules and having trouble integrating them, then it is likely that the folks writing the new modules are taking their eyes off the prize and forgetting the big picture. this can happen if the coders are not appropriately informed as to the larger context of the module at design time, or if the application is being designed on the fly, without regard for the next set of deliverables.

---

### Post by Reiger on 2011-04-22
Architectural changes are more difficult as the project gets bigger, yes. But feature changes/additions/removal should not be. 

Examples of the first case: 
-The change from the prototype stage where string literals might be coded into the application to fetching it from some message catalog;
- The change from where all library code and data files are known/assumed in advance to a setup where library dependencies may be added/removed at will and the program will simply enable/disable dependent features at build/run time.

The reason why such changes get more expensive as the project gets bigger is because they are fairly fundamental to how the project is developed on top of these decisions. That is the structure and the behaviour of the code of the project depends on these decisions. So a change has a complexity in line with the size of the (sub) project which is why if all instances of literal messages must be replaced with catalog lookup, this is more difficult to do with 150 files to update than with 15 files.

Examples of the second case:
-Add a new command to a menubar.

If that sort of thing gets steadily more complex as the project wears on then there is a good chance that your project needs a rethink of what components it consists of and how these should interact with each other in general. The only reason why this sort of thing might become more difficult is because there is an increasing amount of code that is not relevant to the change which obscures the code that is, and possibly an increasingly difficult game of state juggling going on.

---

### Post by robots.jpg on 2011-04-22
I'd agree that programming language plays almost no role here, except to  whatever extent its features facilitate or encourage modular,  maintainable code.  The main issues are usually in communication, design,  and changing requirements (due to poor communication or who-knows-what).

If you're some kind of wizard who can assemble a complete and final list  of  features from day one, or if you have the option to just tell the users  to "deal with it" when they ask for something outside the scope of  the project, you probably won't run into these problems.  If  you're a regular person, it's just a fact of life that people will  manage to come up with things that mess everything up.  Gathering complete and accurate information from the users is a completely separate art from the actual design and implementation.

---

### Post by era86 on 2011-04-22
0. This 'stagnation' seems like more of a macro problem in software.  What I mean is rather than the code-writing process itself, it can/should be address at the software architecture and possibly data modeling level.  In short, yes I agree with you. 

1. It's natural, I think, for code/solutions/approaches in large projects to become obsolete or dated.  As time progresses, so does the technology (whether it be raw computing power or coding techniques).  I think if the project becomes to unwieldy to maintain and you feel like you're tacking on hack after hack to get even simple features in, then it might be good to completely redesign the system.

2. I think besides programmer ability (which is most of it), software architecture and project management have a lot to do with the long-term maintainability of large projects.  Also, a really extensible and generalized (not too much) data model.  I'm feeling the pain in that last sentence...

3. Possibly... projects became increasingly more maintainable as OO-languages became more popular, I think.  Also, I think I'd hate to write large projects in assembly.

---

