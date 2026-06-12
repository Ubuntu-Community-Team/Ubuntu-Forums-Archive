---
title: "Assembly as first language."
date: 2007-01-03
forum: Programming Talk
---

### Post by Silentvoice on 2007-01-03
More and more as I get into programming, I start to believe more that assembly should be a programmer's first language. Over the past two years I've learned C, C++, Perl, Python, Ruby, and obviously with my linux usage, BASH.

Well after learning C and C++ (which I picked up after learning Python) I decided that I wanted to be a computer science major.. But I realized one thing, for all my programming experience, I didn't know jack about how the computer WORKED so I started trying to pick up assembly.... Boy.. after getting so used to IF, WHILE, and ELSE, I was SPOILED. I could not think in terms of assembly, conditional jumps, or using the "general purpose" registers. 

I realized that in order to truly write GOOD code in higher level languages you must first understand how the compilers/interpreters work and how they produce assembly code for your target architecture.

Which brings me to my question to the community here. I think now, after refining my beliefs on teaching programming (or self teaching) that it is a much better idea to send a beginner on assembly, so that when he later learns HLL he can write truly efficient code (and also understand what the machine is doing with his code, rather than just blindly punching it in and blindly compiling it)

note: for the casual person who has just a passing interest, I wouldn't try to scare them away with assembly, as assembly truly is a scary thing to the uninitiated.

Any comments?


BTW: Two great books which helped shape my opinion on this.. 

"Write Great Code" Volume 2 by Randall Hyde -  (although it does not teach assembly, it does teach in detail how compilers work, and how to optimize your HLL code, with some assembly basics thrown in as well)

and "Art of Assembly" also by Randall Hyde - Amazing for figuring out the workings of your CPU, it focuses on the 8086 processor, you start from basics (how to understand binary and hex and data representation such as bits nibbles bytes) and work your way up through boolean algebra and then finally the CPU instructions and how they work. GREAT reference. 

(I believe online versions of these books can be found)

---

### Post by Wybiral on 2007-01-03
While we are in the mindset to state opinions (meaning I am not saying you are wrong, but rather that my opinion differs from yours) I agree... But I disagree. I, much like you, didn't really learn assembly until AFTER I learned C++. I think that: yes, learning assembly definitely changed the way I look at code. But I don't think I would have been interested in programming if I just started at assembly.

I think it's ok to learn higher level languages and get used to programming, and then dig deeper and make sounds like "OH" and "NOW I GET IT" as you figure more out about the machine. Assembly is not a productive language to program in and I think it would have scared the pants off of me when I started programming.

I think if you are going to take the low level route, learn some BASIC (I learned QB) then learn ASM. You really need something to show you loops/conditions in a more abstract way than to just jump right into learning opcodes and dealing with the stack/registers.

Once again, I am not doubting you or contradicting your theory, my opinion is just that using the language before you dissect it is a friendlier route (like driving a car before you learn how the alternator's generator works)

---

### Post by Stephen Howard on 2007-01-03
That takes me back, I have a bookshelf just with assembler books - most are the brilliant Lance Levanthall series.  Haven't opened a volume for at least 20yrs.  That said, assembly programming is fun and encourages discipline and planning.  

I would strongly recommend though that you ignore the 16 & 32-bit processors and instead concentrate on the older 8-bit variety because they have fewer registers and operands to get your head around.

The other decision you need to make is whether you're going to be a sixer or an eighter (ie Motorola 6502 or Intel 8080 series processors).  Everyone of good taste is a sixer.

---

### Post by Stephen Howard on 2007-01-03
The step to take after learning assembler is to study compiler design.  In the process you can create your own (simple) language and figure out how to automate its translation into assembler.  You can't go wrong with the Dragon books by Aho, Sethi & Ullman.

You're not a real programmer until you've written your own language that no one will ever use.

---

### Post by Lord Illidan on 2007-01-03
But at the end of the day, does anyone really need to program in Assembly though? I mean, with all these languages around, why do we need it?

Just asking...and I want some info on this too.

---

### Post by python_loving_idiot on 2007-01-03
Learning anything other than Python is absolutely non-essential. If there is a feature missing from Python, you would simply add it *in Python*. The only reason you would ever learn anything else is if you had to support it, but that *never* happens. No one writes in assembly. Not for 20 years. If you simply tell your employer/client that their code is old, they'll immediately budget the time and cash for a full rewrite. Who wouldn't? Python on the web. Python for devices. Python for rdbms. Python for you. Python for me. The only *basic principle* you need to know, is that you need to know Python. It's like learning math. That's just plain stupid. No one does math anymore. It's called a calculator. And it's probably implemented in Python. 

Hail Python. :p

---

### Post by Lord Illidan on 2007-01-03
> **python_loving_idiot said:**
> Learning anything other than Python is absolutely non-essential. 

Hail Python. :p

Why I agree that Python is a first-class language for scripting and for learning programming, and even for some GUI development, I am more interested in game development...where C++ kicks Python out of the window and bounces after it, rips off the snake's head and rams it down the throat of the nearest dog.

---

### Post by Mirrorball on 2007-01-03
I don't think it's a good idea. Feedback is essential to learning and Assembly is too much work and few results. After a week of intensive learning, the student is finally able to print "Hello world." Will he realize that in practice he would have done that with a one line script?

A basic issue: computer hardware evolves and Assembly changes. But a loop will always be a loop; it's logic, not computer hardware. You don't even need a computer to write a computer program and run it. You could perform the instructions yourself or you could use your calculator. Learning about loops is more important than learning about registers.

Also writing extremely efficient code is secondary to writing code that works and is as efficient as you *need.*

---

### Post by Stephen Howard on 2007-01-03
A fair point Illidan.  I have two answers, one philosophical and one practical.  The philosophical answer is that its just good to see what's going on behind the curtain.  The practical answer is that assembler, compiler and architecture knowledge helps you write faster programs in whatever higher-level language you might be using.  With the right knowledge you can choose particular language constructs that can be compiled more cleanly.

---

### Post by IYY on 2007-01-03
I believe that the first language taught should be a very simple one. Something as simple as BASIC should work nicely (but since BASIC is not used nowadays, Python can be a good choice). This is just to show people what programming is, and to teach them to think algorithmically.

Then, a language like C or assembly can be taught. 

The problem with assembly, though, is that the coding style used in it is not considered to be good practice in any other language. For example, loops and if statements are done using basically a "goto" statement, the worst possible thing a programmer could do in any high-level language.

> But at the end of the day, does anyone really need to program in Assembly though? I mean, with all these languages around, why do we need it?

Just asking...and I want some info on this too.

This is actually a fairly good question. Programmers used to believe that a compiler will never be able to make code as efficient as human-written assembly. This is because compilers will often take the safe route, when in fact a faster option could be used (for example, storing a variable in memory rather than a register). However, things changed since then. Compilers today are so smart, that they can compile any program of a significant size better than humans. 

So really, it is highly unlikely that you will need to write programs in assembly. Learning it will make you a better programmer, though.

---

### Post by Lord Illidan on 2007-01-03
> **Stephen Howard said:**
> A fair point Illidan.  I have two answers, one philosophical and one practical.  The philosophical answer is that its just good to see what's going on behind the curtain.  The practical answer is that assembler, compiler and architecture knowledge helps you write faster programs in whatever higher-level language you might be using.  With the right knowledge you can choose particular language constructs that can be compiled more cleanly.

A nice answer.

Let me give you a real life example, starring yours truly.

At the Oh so highly rated College where I attend, we still have to develop our CS projects in Turbo Pascal. (We can present other languages, but then the teacher probably doesn't understand what we wrote and can't help us in any way whatsoever, so what's the worth).

Anyway, with Turbo Pascal, we can program with the BGI interface provided by Borland back in the 90s....when 640*480*16 colours was a luxury.

I tried to improve upon this. But when I saw what I needed to accomplish just with assembly code, I balked. Lines upon lines of registers that didn't mean anything to me...and in the end would probably translate to hours and hours of time which I just didn't have.

The point? C++ with opengl would have been better, for productivity, longevity (so programmers after me would know what I've done) and probably for performance. And as for knowing what goes on behind the scenes, if a language can perform all the crap like garbage collection, etc, then do we really have to know assembly?

---

### Post by Mirrorball on 2007-01-03
Assembly is good for learning and for games (they say), but I hate it. And I don't know how to write efficient code in Assembly, the gcc developers do. I trust them to optimize my code for me.

---

### Post by IYY on 2007-01-03
> if a language can perform all the crap like garbage collection, etc, then do we really have to know assembly?

In my previous post I said that assembly is no longer needed for practical reasons, which is true, but using a language without automatic garbage collection has significant speed advantages.

---

### Post by python_loving_idiot on 2007-01-03
> **Mirrorball said:**
> Assembly is good for learning and for games (they say), but I hate it. And I don't know how to write efficient code in Assembly, the gcc developers do. I trust them to optimize my code for me.

This almost made me cry. Someone, somewhere, knows how to write efficient assembly code. And we **all** trust them to do it. Thank goodness for *those* people.

But they could probably do it better with python, even if they never studied assembly. I recommend:

```

python.writeAssembly();

```

That should work, IMHO.

---

### Post by rolando2424 on 2007-01-03
I'm TRYING to learn Python as my first language because I really like the syntax...

Also I want to become a game developer, so I'll probably switch to C or another language in the future... But for now, I try to learn all I can with Python, and with Pygame (to try and create little games... Haven't done any though :D)

---

### Post by python_loving_idiot on 2007-01-03
> **rolando2424 said:**
> I'm TRYING to learn Python as my first language because I really like the syntax...

Also I want to become a game developer, so I'll probably switch to C or another language in the future... But for now, I try to learn all I can with Python, and with Pygame (to try and create little games... Haven't done any though :D)

Learn everything you can wrap your head around. Learn Python, learn C (if you want), or C++, or Assembly, or how to translate binary directly. There is no *downside* to knowing more than the guy next to you - if you're willing to make the investment. Stay excited. Stay motivated. 

In the future you may find yourself motivated to study the things no one else wants to study, so that you're able to provide products to the rest of us that make our lives easier, better. Because we can all use the TV remote, but very few of us could make one. Or perhaps you'll make millions in game programming. 

Just don't quit.

All of us who know more than a single language, regardless of what we think you should learn, will probably agree that the first one is the hardest, and that - once you clear that hurdle - you will begin to soak up more and more, faster and faster, as time goes on. Just hang in there.

---

### Post by Mirrorball on 2007-01-03
> **python_loving_idiot said:**
> ```

python.writeAssembly();

```That should work, IMHO.
No, you just load your thoughts into the registers and use the think() system call from Assembly. Oh wait, this doesn't exist. Python does really turn your code into processor instructions, but Assembly doesn't do the thinking for you.

---

### Post by Solver on 2007-01-03
My opinion is that programmers are better off starting with something simple - but, of course, learning more when they want to become better programmers. The first lines of code I ever wrote were in QBASIC, and I became interested in programming.

I believe that interest is crucial, and good returns are crucial to interest. Python now seems to be a great first language to learn. When a new guy wants to learn programming, he starts up Python, writes a simple statement, hey, it prints "Hello World"! By the end of the day, he'll be writing simple programs that print different strings based on the user's keyboard input. He immediately sees return for his effort and is eager to learn more.

Assembly is a tad different - it takes quite a lot of understanding to do even the simplest things. It will not give different cool visible results quite as soon, and that's obvious. Of course, a dedicated person will still learn, but it's a different thing.

My second objection to having Assembly as a first language is the question of practical skill. If you learn Python as a first language, you'll soon be able to make something actually useful. Maybe a small application to help with your backups, a simple geometrical calculator, or maybe you'll go modify a part of some GNOME app that is in Python. After learning Assembly, you have a great understanding of how computers work, but your ability to do something really useful is quite limited - now you have to learn another language, a high-level one this time, so you can finally do something.

---

### Post by Wybiral on 2007-01-03
> The first lines of code I ever wrote were in QBASIC, and I became interested in programming.

Same here... Qbasic, windows 3.11, 5th grade.

---

### Post by pmasiar on 2007-01-03
> **python_loving_idiot said:**
> Hail Python. :p

Hi phossal I was afraid you will give up on python. Nice to see you back.

BTW I really like your new nick :twisted:

---

### Post by Solver on 2007-01-03
> **Wybiral said:**
> Same here... Qbasic, windows 3.11, 5th grade.

The memories... I miss Win 3.11. And DOS 6.22, which was absolutely amazing compared to DOS 5. Heh :)

---

### Post by Mirrorball on 2007-01-03
Qbasic. I wrote a useless program called Dancing Tomatoes. What did it do? I just can't remember.

---

### Post by Wybiral on 2007-01-03
> **Solver said:**
> The memories... I miss Win 3.11. And DOS 6.22, which was absolutely amazing compared to DOS 5. Heh :)

Don't you just miss keywords like "DIM" and "THEN" and "PSET" and "NEXT"

You don't see those too often these days.

Making little pictures with data tables... (1=blue, 2=green, 3=cyan, 4=red...)

And best of all, functions that were in separate windows... And a full language dictionary built into the IDE.

For a MS program, QB was pretty sweet.

---

### Post by Grey on 2007-01-03
I am a professional game developer.  My first language was C++.  I know enough MIPS assembly to write some REALLY crappy programs.  So here's my input on the situation.

I think that learning C++ as my first language was the best language my professors could have possibly picked.  It's a procedural language, so it closely follows how the computer thinks.  But it has some object oriented stuff, so that the language can teach you contemporary concepts.

Learning assembly at a later date, even though I'm not fully fluent was also a great aid to me.  It taught me EXACTLY how the computer thinks, and best programming practices.  In the end, that's really what every programmer should learn when learning assembly.  Assembly is (almost) a dead language.  You aren't going to be using it that often in the real world.  (But you are POWERFUL if are fluent.  Anyone will snatch you up for optimizing really low level code).  What most people get out of assembly should be a deeper understanding of computer internals, and how to optimize their code with higher level languages.  Actually learning to write code in the computer's native language is a secondary objective.

So no, I would say learn a high level language first.  It's more useful, and easier to learn, which is important for the beginning computer scientist.

---

### Post by Solver on 2007-01-03
> **Wybiral said:**
> Don't you just miss keywords like "DIM" and "THEN" and "PSET" and "NEXT"

All of those are still alive in modern versions of Basic, actually. Well, Pset isn't likely to be used, but the other three are. Despite what some say, Visual Basic is a useful language in certain circumstances - since .NET it's even a decent language, not something that breaks every standard and convention there is.

---

### Post by Wybiral on 2007-01-03
EEEK. I don't like VB.

FreeBASIC is OK and Basic4GL is pretty awesome.
(As well as it's linux buddy Basic4SDL, click on my signature)

But I'm not too partial to VB.

---

### Post by pmasiar on 2007-01-03
> **Silentvoice said:**
> Well after learning C and C++ (which I picked up after learning Python) I decided that I wanted to be a computer science major.. But I realized one thing, for all my programming experience, I didn't know jack about how the computer WORKED so I started trying to pick up assembly.... Boy.. after getting so used to IF, WHILE, and ELSE, I was SPOILED. I could not think in terms of assembly, conditional jumps, or using the "general purpose" registers. 

I realized that in order to truly write GOOD code in higher level languages you must first understand how the compilers/interpreters work and how they produce assembly code for your target architecture.

Which brings me to my question to the community here. I think now, after refining my beliefs on teaching programming (or self teaching) that it is a much better idea to send a beginner on assembly, so that when he later learns HLL he can write truly efficient code (and also understand what the machine is doing with his code, rather than just blindly punching it in and blindly compiling it)

note: for the casual person who has just a passing interest, I wouldn't try to scare them away with assembly, as assembly truly is a scary thing to the uninitiated.

I am not sure how many people started with Assembler as first language, I was one of them (long time ago, for IBM/360). It was not very pleasurable experience - it is just lots of hard work for not much gain. IMHO most people treated to ASM will just run away screaming. I did not - I did not knew any better :-) I actually wrote code for IBM/360, i8080 and PDP/11 assembler. PDP was very nice code, very orthogonal. i8080 is bloody mess compared to it. Then it got worse, I looked at i286 and gave away on assemblers. :-)

Much better is to learn concepts of programming using simple language like python, then if you like it, go deeper, learn couple trickier languages. C for sure, will prepare you for assembler. One of canonical statically typed OO languages like C++/C#/java. Then try very different languages which will blow your mind and make you think hard, like Lisp, Forth, Prolog, XSLT, SQL. Each is very different. 

I was really influenced by Forth: it is incredibly sharp tool. Highly recommended, simple, compact, fast and dangerous. Comparing with other languages, it has no concept of shielding programmer from any error. In Forth, you can directly manipulate data and procedure stack, and replace interpreter if you want to. Programming in Forth is writing new language to solve problems at hand. Ahhh, sweet memories.... Never used it since College. :-(

But starting with ASM, especially for a beginner, will IMHO make 99% people fail and reject programming. Which might be your secret plan all along :-)

---

### Post by pmasiar on 2007-01-03
> **rolando2424 said:**
> Also I want to become a game developer, so I'll probably switch to C or another language in the future... But for now, I try to learn all I can with Python, and with Pygame (to try and create little games... Haven't done any though :D)

If you plan to program for living, you better be prepared to learn many different languages. Even if you will not write assembler, it helps to understand CPU architecture (and where CPU cycles are wasted). But C might be enough. 

For programming games, take a look at [Game Maker]("http://en.wikipedia.org/wiki/Game_maker"). It is closed-source proprietary freeware, but incredibly good for games. In GM, you will make your first playable game in a week, fully in GUI without writing a line of code. Just manipulate GM objects, set properties, etc. Really cool. Then you might be tempted to make something similar for Linux in Python - it would be a killer IMHO.

---

### Post by nfm on 2007-01-03
I don't agree with people who say that assembly is a dead language, I see it everywhere where full power of a pc has to be used. Good encoders and decoders are written in C with use of assembly, I've seen it in x264 and xvid, which is where my interest is in, but there are a lot more of programs taking advantage of speed that asm provides.

Also, BIOS I think is written purely in asm, home appliances such as microwave uses asm. I'm learning C, I have some classes in school that teach me Java, but I don't like it because it is inefficient ans uses classes in a weird way, but it teaches me how object oriented  programming works. After I 'll master C, I will learn a bit of C++ , after that I will learn bit of assembly so I will be able code something that needs lots of processing power and compile it with C.

@pmasiar, Great post, I love to misuse  the power of C and its memory allocation.

---

### Post by Wybiral on 2007-01-03
> **nfm said:**
> I don't agree with people who say that assembly is a dead language, I see it everywhere where full power of a pc has to be used. Good encoders and decoders are written in C with use of assembly, I've seen it in x264 and xvid, which is where my interest is in, but there are a lot more of programs taking advantage of speed that asm provides.

Also, BIOS I think is written purely in asm, home appliances such as microwave uses asm. I'm learning C, I have some classes in school that teach me Java, but I don't like it because it is inefficient ans uses classes in a weird way, but it teaches me how object oriented  programming works. After I 'll master C, I will learn a bit of C++ , after that I will learn bit of assembly so I will be able code something that needs lots of processing power and compile it with C.

@pmasiar, Great post, I love to misuse  the power of C and its memory allocation.

I've done enough assembly programming to say this... Yes, it is very useful at times and is very powerful. But it takes a lot longer to program in, and a lot more code... And is often very disorienting when your project gets too big. It does great for device communication... But I wouldn't set out to make a large program in it... Graphical programs, almost impossible (well, small ones are ok, but it is very limited).

Embedded assembly is great to speed up tedious routines in C, but it comes with a cost... Portability. Assembly language is very specific. Also, modern compilers are pretty advances... C/C++ compilers these day's can optimize your output to about what you could get from raw assembly, at a 1/100th of the time it would take to write (depending on how large the program is).

I think assembly is fun, and very educational... But not very efficient these days.

---

### Post by nfm on 2007-01-03
@Wybiral, good post. **I always have command-line programs in mind** ](*,)  (I don't code guis), I agree that modern compilers are pretty advanced but x264, a h.264 encoder, still uses asm with C even though it is compiled with gcc, so hand-coded asm is still faster than translated C by a compiler to machine code, at least that's what the main developer of that program once said. Sorry that I didn't stay on the topic...

---

### Post by Hendrixski on 2007-01-03
Umm, there are people who program in Assembly day in and day out.  They went to college to study Electrical Engineering or Computer Engineering, they write CPU level code that makes everything else just magically work.

If you're not one of those people, why bother?  I learned assembly in college and never used it since.  I may have learned about CPU's in the process, but I have never used that knowledge since and I think it was a waste of time.

---

### Post by pmasiar on 2007-01-03
Two more thoughts about assembler.

1) Years ago I read about research that regardless of the language, programmer writes about 30 lines per day (including project changes, meetings, debugging etc). Maybe now with slicker languages and better tools it is 60 lines. So using language which requires more lines to do same thing is just takes longer - is not cost effective.

It is about managing layers of abstraction.  Read [The Humble Programmer]("http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html") by famous Edsger W. Dijkstra, author of [notoriously famous]("http://en.wikipedia.org/wiki/Considered_harmful") (at least for graybeards :-) ) essay [Go To Statement Considered Harmful]("http://www.acm.org/classics/oct95/"). It was *way* before OOP.

2) Optimizing compilers. After 50 years of research, there is lot of ways compiler can optimize code - sometimes beyond capabilities of average smart human.

---

### Post by Wybiral on 2007-01-03
> I learned assembly in college and never used it since.

Never? I agree that it's not efficient in terms of development time and portability, but I think it's still fun to program in... It's like a challenge.

Speaking of challenges, check out this site: [http://esoteric.voxelperfect.net/wiki/Main_Page](http://esoteric.voxelperfect.net/wiki/Main_Page)

Probably the biggest advantage to using assembly is code size, you can write some TINY programs in it, sometimes 100's of bytes, check this out: [http://www.muppetlabs.com/~breadbox/software/tiny/](http://www.muppetlabs.com/~breadbox/software/tiny/)

But yeah... Not very productive, but it's still fun to play with as a hobby.

---

### Post by Silentvoice on 2007-01-03
Thanks for all the feedback. I was interested in what the general opinion on the matter would be.

For the comments that said assembly is inefficient for large applications - Yes I agree, you would not write an office suite in assembly. however, I mean to learn assembly so that you better understand the system, not for any pragmatic purposes ( although those come later when you can write more efficient code)

And for the comments stating that modern compilers are advanced and make assembly almost a dead language.

This is completely not true, no matter how advanced a compiler is, it is only as good as the code that you feed it. The number one thing I hate hearing out of programmers is how good a compiler is, or bashing other compilers, this lets me know that they don't know how to write decent code on their own. Yes, optimization features on compilers have come a long way, and are quite intricate now, but a veteran programming something in C and compiling it will not even come close to a veteran assembly programmer in terms of efficiency.

Not that I'm suggesting more things should be written in asm, I believe HLL code is much better because it is portable, and READABLE :)   but asm itself should never be disqualified as dead.

---

### Post by Wybiral on 2007-01-03
> a veteran programming something in C and compiling it will not even come close to a veteran assembly programmer in terms of efficiency.

But, the average C programmer will usually produce better code than the average assembly programmer.

I know that *theoretically* a good assembly programmer has absolute freedom and should be able to write programs 10x smaller and faster than a compiled program, because operations in a compiled language are generalized and assembly allows you to write specific code...

But it isn't always true. Assembly hits a level of complexity at times that the code, even by professional assembly programmers, is not up to par with what the compiler is able to do. The compiler is a machine that can consider way more options than a single person can. So unless that person is just gifted... Well written code from modern compilers will probably hold it's own.

HOWEVER... I never said anything about the compiler being some kind of magical cure for bad code... You still have to write good code, it won't fix a majority of problems (since a lot of problems are too technical and complex for the compiler to have built in fixes for) but the compile is able to use the higher level language and generate some pretty good code for.

---

### Post by lnostdal on 2007-01-04
I agree; both a strong left and right hand is needed.

[http://download.savannah.gnu.org/releases/pgubook/](http://download.savannah.gnu.org/releases/pgubook/)

..but do move on to HLLs as soon as possible; there is a reason we moved from punch-cards to better and more suitable ways of expressing stuff.

Now as to what end to start in I'm not sure; as one mentions here one might bore oneself to death messing with ASM as a newbie. :)

---

### Post by supirman on 2007-01-04
When I started college, I had just become interested in computers (as my family purchased our first one when I was a senior in High School), so I started with a double major in Electrical Engineering and Computer Science.  I can tell you right now, if they had started me off in a class learning assembly, I would have been entirely uninterested and probably dropped the computer science major.  As it turns out, my first class was learning the fundamentals of programming using c; my interest was captured from the beginning.  

Having said that, I felt more comfortable learning assembly as I progressed in my coursework and as my knowledge of the entire subject area grew.  I now work in the telecommunications equipment manufacturing industry, and I've written software from assembly, to c, to c++, and even python.  Being well rounded is an asset.  Even if you never use it, it still wouldn't hurt you to learn it, as it will just further your understanding.

And for those who say "as long as **someone** knows how to do assembly, like the compiler writers, then why should I learn"....  Think of a complex graphing calculator.  In engineering courses, these things are amazingly helpful.  If we all rely too heavily on them, however, and don't learn how they work, who will make future generations of such devices?

---

### Post by rolando2424 on 2007-01-04
> **pmasiar said:**
> If you plan to program for living, you better be prepared to learn many different languages. Even if you will not write assembler, it helps to understand CPU architecture (and where CPU cycles are wasted). But C might be enough. 

For programming games, take a look at [Game Maker]("http://en.wikipedia.org/wiki/Game_maker"). It is closed-source proprietary freeware, but incredibly good for games. In GM, you will make your first playable game in a week, fully in GUI without writing a line of code. Just manipulate GM objects, set properties, etc. Really cool. Then you might be tempted to make something similar for Linux in Python - it would be a killer IMHO.

I have used Game Maker (and RPG Maker) in Windows, and I didn't like them...

I just did some tutorials and nothing more.

I want to know and understand how to write games :D

---

