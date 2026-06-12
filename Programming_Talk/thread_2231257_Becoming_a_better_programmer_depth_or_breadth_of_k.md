---
title: "Becoming a better programmer: depth or breadth of knowledge recommended?"
date: 2014-06-24
forum: Programming Talk
---

### Post by veddox on 2014-06-24
Hi everybody, I'm a young hobby programmer who wants to get a little better, but doesn't quite know in which direction to head next... I started off programming by teaching myself Java 2 1/2 yrs ago, followed by Python a year or so back. Right now I'm trying to get some working knowledge of C++, but don't know where to go from there. Should I aim for breadth, and learn more and different languages? (If so, which ones would you recommend and why?) Or should I deepen my knowledge first, and go for stuff like algorithm design, graphics programming or design patterns (with the languages I already know)? Regardless of what you prefer, I would also value a pointer to some good learning resources. Thanks a lot!

 P.S. Related to this post is probably the question of what actually constitutes a "good programmer", but that might be a whole new discussion...

---

### Post by tgalati4 on 2014-06-24
Why do you want to program?

---

### Post by veddox on 2014-06-24
I enjoy making a computer do what I want, and not being dependent on the programs others have written. Chances are I will also need it for my job some day (I want to go into Bioinformatics).

---

### Post by Vaphell on 2014-06-24
better programmer? Imo depth before breadth. It doesn't matter if you can write a few hundred lines of intermediate level code full of naive algos in dozen languages if the design, maintainability, scalability and performance are atrocious.

---

### Post by QIII on 2014-06-24
Go deep first and master something.  A "jack of all trades, master of none" is a problem in software development.  When you have one down, then work on another as you have the need.

The three you have mentioned probably cover 80% of the landscape, with others being really well suited for some of the stuff left over.

But I will also say that the knowledge of a particular language may be a less important quality than the ability to identify, analyze, break down and solve problems.  That is what developers do -- they use code to provide a solution.  All the technical mastery of a language in the world means nothing if it can't be applied.

People laugh when I say this, but some study of classical logic and philosophy go a long way towards that end.  We have several thousand years of written records of how people have thought and developed how to go about solving problems.

It is easier for me to teach a new programmer a language than to teach them to solve problems.

---

### Post by tgalati4 on 2014-06-24
Think of your computer as a toolbox.  The languages and your programming skills are the tools and your ability to use them.  "The computer is not the thing.  It is the thing that gets you to the thing."  

What specifically do you want to do in bioinformatics?  It's a large field of study.  According to [wikipedia]("http://en.wikipedia.org/wiki/Bioinformatics"):

> Commonly used software tools and technologies in the field include Java, C#, XML, Perl, C, C++, Python, R, SQL, CUDA, MATLAB, and spreadsheet applications.[1][2][3]

---

### Post by veddox on 2014-06-24
@tgalati4: I am fascinated by the idea of modelling nature, be it on the level of an individual cell, an organ, or a whole ecosystem. It's still a pretty small area, but one that I think will grow very rapidly in the next few years. Working on something like that would be my dream, but let's wait and see where life leads me...

> It doesn't matter if you can write a few hundred lines of intermediate level code full of naive algos in dozen languages if the design, maintainability, scalability and performance are atrocious.
+1

Any suggestions on how to improve in those areas?

---

### Post by tgalati4 on 2014-06-24
Find a project, roll up your sleeves and start working.  This is an open source plant growth model:  VirtualLeaf

[http://www.plantphysiol.org/content/155/2/656.full](http://www.plantphysiol.org/content/155/2/656.full)

When you reach into your toolbox and you are missing a tool, then that is the language to study.

---

### Post by tuhdo1710 on 2014-06-25
Someone compiled a list of courses: [http://blog.agupieware.com/2014/06/online-learning-intensive-bachelors.html](http://blog.agupieware.com/2014/06/online-learning-intensive-bachelors.html)

The core courses you should learn:

- Algorithms (you can use ones from the list or find on Coursera), both theory and programming
- Computer Network
- Computer Architecture (at least be able to read hardware spec and write assembly)
- Compilers (available on Coursra)
- Operating System (at least understand how it works).
- Theory of Computation

Learn to use the toolchain depends on the language requires, by yourself. It's part of the process to become a better programmer.
And find a usable editors. At least use vim/emacs. For emacs, checkout my guide: [http://tuhdo.github.io/emacs-tutor.html](http://tuhdo.github.io/emacs-tutor.html)

---

### Post by King Dude on 2014-06-27
I've come to the understanding that being a master at programming in one language is seven-fold times better than only having a half baked proficiency in several languages.
 
That being said, you want to ask yourself, "What exactly am I going to program?" There's programming on the hardware/OS level, mostly C and Assembly, and there's more higher level application programming, popular languages include but not limited to C++, Python, Java, Perl, Ruby, Lua, HLA, etc. 

If you want maximum speed and do not care for complicated code, C or Assembly is what I'd recommend. If your priority is portability, Java is great for that. If you're into scientific programming, Python and FORTRAN is popular in that field, and a new language has emerged called Julia that seems promising. 

Keep in mind that if you learn a language, aside from various differences in syntax, it should not differ too much from another language, so if you lose interest in one language moving to another may prove to be not that difficult, especially if the two languages are from the same family (such as C++, C, and C# for instance).

Goodluck

---

### Post by llanitedave on 2014-06-27
> **QIII said:**
> 
People laugh when I say this, but some study of classical logic and philosophy go a long way towards that end.  We have several thousand years of written records of how people have thought and developed how to go about solving problems.


I won't laugh about that at all.  Having a *real* education makes people better in just about any field, I think.

---

### Post by trent.josephsen on 2014-06-28
[Fairly recent although brief thread on this very topic](http://ubuntuforums.org/showthread.php?t=2206742). Two comments I liked:

[quote=Don_Stahl]learn enough to know what is the right tool for a task[/quote]

[quote=buzzingrobot]Dabble until you know what you have an affinity for, and what seems unlikely to ever make sense. Then, focus on what you like and what you're good at.[/quote]

---

### Post by CptPicard on 2014-06-28
I guess I've seen things from the "working out the details is a homework excercise" perspective for too long, but I've got to say I'm a big fan of being a generalist. The really interesting differences between programming languages are in the ideas they embrace.

On the other hand, it is true that in order to actually pragmatically being able to achieve anything, you'll probably want to be good at the language you're using. So I'd suggest you "work" in one or two languages, but keep on dabbling in other languages that are different enough that you wouldn't use them for your daily work. I don't write Prolog for a living but I certainly find it interesting...

---

### Post by slonk on 2014-06-30
> **veddox said:**
> Hi everybody, I'm a young hobby programmer who wants to get a little better, but doesn't quite know in which direction to head next... I started off programming by teaching myself Java 2 1/2 yrs ago, followed by Python a year or so back. Right now I'm trying to get some working knowledge of C++, but don't know where to go from there. Should I aim for breadth, and learn more and different languages? (If so, which ones would you recommend and why?) Or should I deepen my knowledge first, and go for stuff like algorithm design, graphics programming or design patterns (with the languages I already know)? Regardless of what you prefer, I would also value a pointer to some good learning resources. Thanks a lot!

 P.S. Related to this post is probably the question of what actually constitutes a "good programmer", but that might be a whole new discussion...

You seem to be too focused on languages. OSes and APIs are important, too. 3 language are already too many for you, although it is probably a good thing that you realized Java isn't it early enough :)

Design patterns aren't something that gets you to write cool programs on your own.  You should be familiar with standard algorithms, because that makes you at least realize when you are about to do something stupid even when facing other problems.  You should have an idea about the performance model of your language and how it relates to the CPU.  CPU, OS, language and a bit of algorithms is a very useful stack.

---

### Post by ofnuts on 2014-06-30
OSes and APIs are very temporary things in a programming career... even more temporary than programming languages(*). 

What remains used throughout is: some [basic knowledge of computer science]("http://en.wikipedia.org/wiki/Algorithms_%2B_Data_Structures_%3D_Programs"), the ability to learn new things, and the ability to transform a complex problem into the sum of individually simpler bits at the "tactical" level (coding style) and the "strategic" one (application architecture). 

Everything else is on StackOverflow :)

(*) [This site]("http://thedailywtf.com/default.aspx") is the daily demonstration of what happens when programmers know only OSes, programming languages, and APIs, even very well so.

---

### Post by CptPicard on 2014-06-30
+1, **ofnuts**, I couldn't be more in agreement.

It's the "translation of problem into programming language at the tactical/strategic level" where some breadth comes in handy; it gives ideas for different kinds of approaches even if your actual current language in use doesn't support them directly.

---

### Post by veddox on 2014-07-01
@slonk: what exactly do you mean when you say that OSes are important?

---

### Post by tgalati4 on 2014-07-01
Operating Systems are important in that your code has to execute in an operating system environment.  It could be an embedded system (like a RaspberryPi) or a blade server running a cloud service.  Your program has to compete for resources--CPU cycles, RAM, disk space.  An inefficient program won't scale as more people try to use it.

Refactoring--an important programming skill--is the art of throwing away the current code and rewriting from scratch.  Refactoring is often needed because of how the code runs (poorly) within its operating system.  Refactoring could involve changing languages or updating frameworks depending on what is  needed to improve performance.

---

### Post by trent.josephsen on 2014-07-01
> **tgalati4 said:**
> Refactoring--an important programming skill--is the art of throwing away the current code and rewriting from scratch.
No, that's practically the *exact opposite* of refactoring. Refactoring is making small incremental changes that alter the code's structure but not its content, and is generally much more difficult than throwing it all out and starting over. Both skills are called for in different situations, but rewriting is usually easier, and therefore refactoring is more valuable IMO.

---

### Post by gordintoronto on 2014-07-02
A "good programmer" writes programs which work. In the business world, company policies and procedures dictate that some programs include a lot of logic. I have seen programmers who could write a 4,000-line program, and after extensive testing, it went into production. I have seen other programmers who would write a 400-line program, then spend the next couple of weeks fixing the bugs.

Here are the words you need to really, really understand: and, or, not.

A "good programmer" is not slow. Writing 100 lines of code in a day, is slow. Writing 300 lines of code in a day is not slow.

I will also vote for depth. If you can make use of every feature of one language, you have mastered the language. You need to master one language, and almost everything you learn will apply to other languages. Over a long career, I mastered a couple of languages, and dabbled in maybe 30. (Early on, I learned how to read IBM manuals, so I could help people, when they were using a language which I had never used.)

---

### Post by ofnuts on 2014-07-02
> **gordintoronto said:**
> 
A "good programmer" is not slow. Writing 100 lines of code in a day, is slow. Writing 300 lines of code in a day is not slow.


You cannot avoid taking in account the code quality here.... With cut and paste you can very quickly write a 2000-lines untestable and unmaintainable monster. In very many projects there is a very tight schedule for initial code delivery, followed by an "open bar" policy for testing and bug fixing that tends to foster this kind of bad code. And code survives you. Write your code as if you could be called for an emergency bug fix, 6 months from now, the day you have a hangover or a bad flu.

A good programmer knows when/where perfect code is necessary....

---

### Post by gordintoronto on 2014-07-02
> **ofnuts said:**
> You cannot avoid taking in account the code quality here.... 

I couldn't agree more. I should have made it clear: 300 lines of original, working code is not slow!

---

### Post by ofnuts on 2014-07-03
> **gordintoronto said:**
> I couldn't agree more. I should have made it clear: 300 lines of original, working code is not slow!

Yes, but 100 lines of code with the very same functionality (if due to a clean code structure, not to abuse of one-liners) is definitely better. Less code, fewer bugs, less testing necessary(*). The 3x slower programmer (who still delivers his code at the same time as the fast one) could be more productive in the long run, by requiring less work from others.


(*) Because the code has likely fewer paths, so the testing can achieve complete code coverage with a much smaller set of inputs.

---

