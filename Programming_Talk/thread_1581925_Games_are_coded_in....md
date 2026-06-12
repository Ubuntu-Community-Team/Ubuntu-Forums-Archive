---
title: "Games are coded in...?"
date: 2010-09-25
forum: Programming Talk
---

### Post by Xender1 on 2010-09-25
Just out of curiosity, what sort of languages are used to program games (like Starcraft 2/WoW/Oblivion/etc)? And also whats a good language to start programing games in (only experience I have is from Flash + ActionScript and DarkBasic).

---

### Post by mrhhug on 2010-09-25
C++.

---

### Post by del_diablo on 2010-09-25
Go!

---

### Post by vek on 2010-09-25
Pretty much every commercial game is coded in C/C++ (usualy C++).

If its on the 360 or the PS3 and its not a "XNA" (community title), the only thing it can be is C++, so most devs aren't interested in developing a game in something else and lock themselves out of those markets.

XNA (360) allows you to code your games in C# and still run it on windows and the 360.

On the PC there are plenty of other options, though, such as PyGame (python) and so on.  Under the hood they're more or less all using c/C++ though.  Games are performance intensive so when it comes to making it easier to program but 100 times slower, or hard to program but 100x faster and smoother... the latter wins every time

---

### Post by worseisworser on 2010-09-25
A combination of C++ and Lua is common for the games you mention.

For smaller games there's usually a lot more options available. If you're a single developer or part of a smaller team (indy), other options are worth considering.

---

### Post by Sammi on 2010-09-25
> **worseisworser said:**
> For smaller games there's usually a lot more options available. If you're a single developer or part of a smaller team (indy), other options are worth considering.
Worth stressing.

Basically: if it's a small game that's going to be run on PCs, then you may use any language that you are familiar/confortable with.

C++ is only a must, for big commercial performance intensive games.

---

### Post by worksofcraft on 2010-09-25
There is a game called Runescape that runs on the Java VM. This has advantages for portability, but it's a bit down on performance and the graphics are simply sad compared to other games.

---

### Post by Some Penguin on 2010-09-25
Design and resources matter so much more for performance than choice of language.  Somebody who's lousy code makes a machine do lots of extra disk or network I/O or who is happy with gratuitous sequential scanning because he doesn't understand how to organize data is going to hurt you far more.

And -most- major general-purpose programming languages can used; I've even seen a quite nice fast-paced side-scroller written in Lisp, for instance, and somebody wrote a 3D FPS engine in Haskell IIRC.  Better to pick one where you're familiar and less likely to mess things up in indecipherable ways.

---

### Post by worseisworser on 2010-09-25
> **Some Penguin said:**
> Design and resources matter so much more for performance than choice of language.  Somebody who's lousy code makes a machine do lots of extra disk or network I/O or who is happy with gratuitous sequential scanning because he doesn't understand how to organize data is going to hurt you far more.

And -most- major general-purpose programming languages can used; I've even seen a quite nice fast-paced side-scroller written in Lisp, for instance, and somebody wrote a 3D FPS engine in Haskell IIRC.  Better to pick one where you're familiar and less likely to mess things up in indecipherable ways.

Yup, here's a recent one in Lisp (Scheme): [http://www.youtube.com/watch?v=5kWgDt1W2ZQ](http://www.youtube.com/watch?v=5kWgDt1W2ZQ)  [http://www.youtube.com/watch?v=_VGZdhOZD4M](http://www.youtube.com/watch?v=_VGZdhOZD4M)   It runs on both Linux and Windows and while quite simple I found it quite enjoyable; I actually completed the demo. :)

---

### Post by Simian Man on 2010-09-25
> **Sammi said:**
> C++ is only a must, for big commercial performance intensive games.

The main reason for the proliferation of C++ in commercial titles isn't even performance.  It's the fact that these game companies have their engines and middleware all written in C++ and it's what their programmers are familiar with.  With tight budgets and even tighter schedules, there's no incentive to switch to newer tools.

As an indie, you don't have these concerns :).

---

### Post by DanielWaterworth on 2010-09-26
> **worseisworser said:**
> A combination of C++ and Lua is common for the games you mention.

It's often the case that there will be some sort of scripting language along side c++ for some of the high-level implementation and games-programmers are known for using asm for code in their tight nested loops.

Lil off topic, wikipedia says "A number of video games such as [The Sims 3]("http://en.wikipedia.org/wiki/The_Sims_3") and [Second Life]("http://en.wikipedia.org/wiki/Second_Life") along with many games based on the [Unity game engine]("http://en.wikipedia.org/wiki/Unity_%28game_engine%29") also make use of Mono."

---

### Post by GenBattle on 2010-09-26
As other people have said, most games are coded in C++.

That said, most of the sorts of games you're talking about have teams of 20+ programmers, so some serious effort and skill is needed to produce the same kind of results. As other people have said, most of the current tools and whatnot are written in C++, so that's what continues to be used. It is also because of the speed factor; alot of optimization goes into making games as fast as possible on users' computers.

If you want to develop games, your best option would be to find a pre-built game engine or framework and then build your game on top of that either through a C++ API, or through a high level programming/scripting language attached to the engine.

The company i work for does this. We have a custom build game engine with LLVM sitting on top of it with our own custom scripting language. This allows us to very rapidly develop rich applications; using this technique you can bang a basic 2D game together in a couple of days. Building everything from scratch, this could take weeks.

---

### Post by ja660k on 2010-09-26
> **worksofcraft said:**
> There is a game called Runescape that runs on the Java VM. This has advantages for portability, but it's a bit down on performance and the graphics are simply sad compared to other games.


Clearly you havnt heard of minecraft
[http://minecraft.net/](http://minecraft.net/)

its in java using openGL.
its portable: mac, linux, windows & in browser.

it shows that a game doesnt need intense graphics to be fun, its still in aplha and the creator has made well over $1,000,000.

something to think about :)
oh and EVE online is written in python.

---

### Post by juancarlospaco on 2010-09-26
LOLcode

---

### Post by simeon87 on 2010-09-26
> **ja660k said:**
> Clearly you havnt heard of minecraft
[http://minecraft.net/](http://minecraft.net/)

its in java using openGL.
its portable: mac, linux, windows & in browser.

it shows that a game doesnt need intense graphics to be fun, its still in aplha and the creator has made well over $1,000,000.

something to think about :)
oh and EVE online is written in python.

From the site: "I've only got one more feature to add; multiplayer support." - that may not be a very good sign, multiplayer should always be done first or the game should be designed thoroughly with multiplayer in mind.

---

### Post by dv3500ea on 2010-09-26
A brilliant (Worms like) game called [Hedgewars]("http://www.hedgewars.org/") is interesting - it is written in Pascal, Objective-C, Haskell and Lua.

---

### Post by shawnhcorey on 2010-09-26
As an indy, I would choose the graphic and physics engines first and then choose the language works best with them (meaning C++ :)).

---

### Post by worseisworser on 2010-09-26
> **shawnhcorey said:**
> As an indy, I would choose the graphic and physics engines first and then choose the language works best with them (meaning C++ :)).

Yes, no "The Humble Programmer" here.

---

### Post by worseisworser on 2010-09-26
> **DanielWaterworth said:**
> It's often the case that there will be some sort of scripting language along side c++ for some of the high-level implementation and games-programmers are known for using asm for code in their tight nested loops.

Lil off topic, wikipedia says "A number of video games such as [The Sims 3]("http://en.wikipedia.org/wiki/The_Sims_3") and [Second Life]("http://en.wikipedia.org/wiki/Second_Life") along with many games based on the [Unity game engine]("http://en.wikipedia.org/wiki/Unity_%28game_engine%29") also make use of Mono."

Yeah, JavaScript, C# or Boo (similar to Python) can be used. It seems they are using custom implementations that compile to native code, but I haven't looked closely at this.

---

### Post by shawnhcorey on 2010-09-26
> **worseisworser said:**
> Yes, no "The Humble Programmer" here.

"The three chief virtues of a programmer are: Laziness, Impatience and Hubris." Larry Wall, creator of Perl

I got at least one of them.  ;)

---

### Post by unknownPoster on 2010-09-26
> **ja660k said:**
> 
oh and EVE online is written in python.

Not entirely true. Much of the UI and client side things are in fact written in Stackless Python, however a good bit of the backend and server-side are written in both C and C++.

---

### Post by juancarlospaco on 2010-09-26
But you can use C as part of the python code, its a feature of python itself,
you can use gui toolkit code too, tcl on python code i.e.

---

### Post by worseisworser on 2010-09-26
> **juancarlospaco said:**
> But you can use C as part of the python code, its a feature of python itself,
you can use gui toolkit code too, tcl on python code i.e.

Yup, it is common to combine C and HLL code. Several languages and environments can do it and it is quite simple, e.g.:

```

$ cat library.c

int sum(int x, int y){
  return x + y;
}


$ gcc -g -Wall -fpic -shared library.c -o libtest.so


....
....


CL-USER> (load-foreign-library "/home/lnostdal/programming/c/libtest.so")
#<FOREIGN-LIBRARY {1003A7DA01}>

CL-USER> (foreign-funcall "sum" :int 40 :int 2 :int)
42


;;; To make calling the function a bit nicer or more transparent:

CL-USER> (defcfun sum :int (x :int) (y :int))
SUM

CL-USER> (sum 10 15)
25

CL-USER>  

```

---

### Post by shawnhcorey on 2010-09-26
> **worseisworser said:**
> Yup, it is common to combine C and HLL code. Several languages and environments can do it and it is quite simple

And if you use the Watcom C++*compiler, you can embed assembler in your C code.

---

### Post by Barrucadu on 2010-09-26
That works with GCC, too. Though the syntax for GCC's inline asm is just plain weird.

---

### Post by directhex on 2010-09-27
Typically, games are written with two major engines, in two distinct languages.

There's the high-performance stuff, which needs a decent maths degree and an intimate knowledge of C or C++ (e.g. graphics engine, physics engine)

And there's the rapid-development stuff you can get the artists to do, which is typically Lua but might also be C#, Python, or something home-made (e.g. all the rules that define a game, like how guns in a FPS behave).

For some real-world examples, Civilization 4 is C++/Python, Civilization 5 is C++/Lua. The Sims 3 is C++/C#. Second Life moved from their own scripting language to C#.

---

