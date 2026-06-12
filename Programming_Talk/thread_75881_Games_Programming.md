---
title: "Games Programming"
date: 2005-10-14
forum: Programming Talk
---

### Post by dadomingues on 2005-10-14
Hi,

I wanna know what languages, methods and tools are the best to develop games? "Anyone" tell me about Allegro, C++, Python and Blender.

Thank you! :D

---

### Post by Lord Illidan on 2005-10-14
I believe Blender is used to produced ray traced graphics, not games. For games, c++ is used a lot in Linux. In fact, if you download the source of a c++ computer game like globulation (run a google search), you can see the source code for it.

---

### Post by dadomingues on 2005-10-14
I know that with Blender we can use python to scriptings and I listened that games can be made with it. Other people defend Allegro and C++, but I'm a newbie in programming games' world. I read an article about XP (eXtreme Programming) saying that it is utilized by many programmers. Is it true?
Should I utilize C++ with Allegro libs, too? I will analize source codes to learn but I would like to know your suggest.

If you can help me... Thank you!!!

---

### Post by stimpack on 2005-10-15
Having worked in the games industry it was all C and Assembler. Some C++ but certainly nothing else. Its all about speed and alot of these fancy languages have a pretty savage performance hit.

---

### Post by Lord Illidan on 2005-10-15
C/C++ and Assembler is the fastest you can get...Other languages are slooow..

---

### Post by jshipley on 2005-10-15
I have found python with pygame to be a very good combination for game making. They can't really compare to C w/ assembly for power and speed, but they don't have to. Unless you are going to be making a huge game where speed is critical, python should do the job beautifully. Plus, it is easy and fun to use.

---

### Post by ~J~ on 2005-10-15
[QUOTE=jshipley]I have found python with pygame to be a very good combination for game making. They can't really compare to C w/ assembly for power and speed, but they don't have to. Unless you are going to be making a huge game where speed is critical, python should do the job beautifully. Plus, it is easy and fun to use.[/QUOTE]

Agree with you 100%!

Look at how funs game were and whilst Python and Pygame aren't the fastest by far, speed isn't the only thing that makes a good game.

---

### Post by jobezone on 2005-10-15
There are also free 3d and 2d engines you can use, like crystal space (3d) and sdl (2d).

---

### Post by remin8 on 2005-10-17
If you will be programining a cross-platform game, I would suggest C/C++ with SDL (which CAN do 3D via OpenGL) so it is relativly fast. I use Anjuta with SDL under ubuntu and it works very well.

---

### Post by dadomingues on 2005-10-17
I found some texts about games in linux pointing ClanLib 3D and SDL 2D. I think all, or most of, 3D engines utilize OpenGL. As Allegro as ClanLib are not tools for visual modeling, but CrystalSpace and Blender are.

I know we can develop games with Blender, but by the Crystal home page its better because optionally use OpenGL (on all platforms), SDL (all SDL platforms), X11 (Unix or GNU/Linux) and SVGALIB (GNU/Linux), assembler routines using NASM and MMX. Blender is excelent too (python language to animate objects and more tutorials in own website)... Maybe Crystal is better for games ... I dont know.

CrystalSpace + SDL + Cpp + extralibs ...
Blender + Python + extralibs ...

If you made a game with them, you can say me!

Thanks guys, if I "discover" something more, I will post it here!
Thanks again!

---

### Post by dadomingues on 2005-10-17
I found in [http://www.codeguru.com/Cpp/misc/samples/games/article.php/c10583/](http://www.codeguru.com/Cpp/misc/samples/games/article.php/c10583/) a text about OGRE 3D. It likes cool.
About Anjuta I didnt find many things... [http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/) is out...

---

### Post by kudu on 2005-10-17
Best thing is to pick something, anything, and LEARN it. Don't get sidetracked! There's a lot of stuff out there.

---

### Post by SeanCallan on 2005-10-18
I prefer C/C++ w/ OpenGL for actually code development.

Right now I'm working on my own 2d/3d side scroller.  I have some education in game animation and 3d enviroments but I absolutely love side scrollers.

---

### Post by clayasaurus on 2005-10-19
I use the D programming language ([www.digitalmars.com/d)](www.digitalmars.com/d)), as one of its early adopters, there is a small group of D game programmers slowly paving the way to make it a more attractive alternative to C/C++, it has the same performance and a really fast compilation, and it can directly interface with C. By the time it hits v1.0 it should be a nice alternative to C++.

I also use SDL (mixer + image + net), OpenGL, and Lua. Note this is my first attempt at a game, but I am persistant. Here is a screenshot. 

[http://svn.dsource.org/projects/warbots/web/index.html](http://svn.dsource.org/projects/warbots/web/index.html)

I won't settle for anything less than 'starcraft meets crobots.'

G'day.

~ Clay

---

### Post by bytter on 2005-10-19
[QUOTE=dadomingues]I read an article about XP (eXtreme Programming) saying that it is utilized by many programmers.[/QUOTE]

XP is a methodology for software engineering! It is not a platform, it is not a language nor it is a collection of libraries. It is a philosophy, a common practice among several engineers, programmers and system analysts. It emphasizes on team programming, version control, code reuse, iterative development, early coding, heavy refactoring, high availability of end-users and stakeholders, unit-testing, a good dose of analysis, and the supernatural ability to *smell* your code [Beck, Kent]. :D

The best way to describe XP is: "Ready! Fire! Aim.. Aim... Aim..."

---

### Post by dadomingues on 2005-10-20
[QUOTE=bytter]XP is a methodology for software engineering! It is not a platform, it is not a language nor it is a collection of libraries. It is a philosophy, a common practice among several engineers, programmers and system analysts. It emphasizes on team programming, version control, code reuse, iterative development, early coding, heavy refactoring, high availability of end-users and stakeholders, unit-testing, a good dose of analysis, and the supernatural ability to *smell* your code [Beck, Kent]. :D

The best way to describe XP is: "Ready! Fire! Aim.. Aim... Aim..."[/QUOTE]

As an other system, a game has to be estructured and documented. Or not? I think yes. Looking for games I found a text about it using XP to project. Do you say its complicated (I know nothing about XP)? How do you do? Do you just "type"? There is an other known methodology to develop games?

Sorry my many questions... Thank you!

---

### Post by bytter on 2005-10-20
Heya there,

[QUOTE=dadomingues]As an other system, a game has to be estructured and documented. Or not? I think yes. Looking for games I found a text about it using XP to project. Do you say its complicated (I know nothing about XP)? How do you do? Do you just "type"? There is an other known methodology to develop games?[/QUOTE]

No problem, just put your questions. XP is a methodology you can follow... It is not tightly bounded with any kind of software (i.e., you can apply it to games, system applications, custom applications, even operative system design, it doesn't matter), as long as it is OO (Object Oriented).

To get along with what is eXtreme Programming, you may need to read some books and meditate on them. XP must not be looken upon as just a technique. XP is a philosphy for planning, analysis and development. Must of us learn XP without even knowing, though there are some ideosyncrassies in it that most people aren't even aware.

To begin, I would first choose an OO language and *learn* it... It doesn't really matter what language (Java, C++, C#, Boo, among several others). Then I would start to learn UML to be able to express and structure my ideas in a layer much higher than code. If there is a "client" involved (i.e., the person or people you're making the software to), UML will be your interface to the outside world. After that I would read through *Design Patterns* and practice a lot. I would have the Refactoring book as my Bible. I would learn how to use SVN (no CVS, please :)) and other collaborative tools. And then, finally, I would adventure myself into what it is called the XP... Of course you can do it all the other way round if it suits you :)

Here are some "cult", must read, books and links:

[LIST]
[*]**Planning Extreme Programming**, *Kent Beck and Martin Fowler*, 0201710919
[*]**Extreme Programming Explained**, *Kent Beck*, ISBN 0201710919
[*]**Refactoring: Improving the Design of Existing Code**, *Martin Fowler*, ISBN 0201485672
[*]**Design Patterns: Elements of Reusable Object-Oriented Software**, *Gamma, et al.*, ISBN 0201633612
[*][http://www.extremeprogramming.org/](http://www.extremeprogramming.org/)
[*][http://www.dofactory.com/patterns/Patterns.aspx](http://www.dofactory.com/patterns/Patterns.aspx)
[*][http://www.uml.org/](http://www.uml.org/)
[*][http://en.wikipedia.org/wiki/Rational_Unified_Process](http://en.wikipedia.org/wiki/Rational_Unified_Process)
[*][http://en.wikipedia.org/wiki/Extreme_programming](http://en.wikipedia.org/wiki/Extreme_programming)
[/LIST]

Asking if it is complex? No.. It's extremely simple! You can grasp the simple concepts of everything I've mentioned in a short time, and then mature them as you go along the road. But XP will require from you a deep understanding of software design and development, no doubt. It will push you to higher levels of abstraction when looking upon software.

Is it the only methodology available? No, of course not. Let's make a metaphor. Suppose you are given the task to build an ant. The power of XP is that, when you build an ant, you build one that if it later requires, it will be able to fire weapons, have armor and fly. Also the ant would be able to know itself and construct other ants. Everyone who would look at the ant would understand its inner works at the first time, and would extend the ant to make cofee, toasts, and act like a pet if they want. Also your ant would sorta look like a Lego. It will stick to other ants as modules and together they would make a super ant. This is the philosophy behind XP: modularized, elegant, code-reusable, flexible and always-thinking-in-the-future design. But... Sometimes... You just need a f***ing ant! XP will not tell you  what is the best way to go. But it will teach you to adjust yourself to the needs as you go along.

Most developers fear change. They look upon their spaghetti code, feeling chills just to think on it. It is not uncommon to hear one saying: "I don't know how it works. But it works. Sure it should have been done in another way, but no way I'm gonna touch that code." Developers like this develop resistance to change. XP, on the other hand, embraces change. XP emphatizes on early refactoring: "If it smells bad, refactor! As early as possible!"

So sticking to XP would utimately be a personal decision (unless you're in a team that uses it, like me). But you can't imagine what XP is until you actually start to do it.

Welcome to the frontier of software design :D

Cheers!

---

