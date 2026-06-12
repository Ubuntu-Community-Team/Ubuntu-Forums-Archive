---
title: "Game Programming?"
date: 2008-05-19
forum: Programming Talk
---

### Post by PFSpectrum on 2008-05-19
I want to start to develop games in c++. I have read a few books on c++ and want to try programming games. I found out about Allegro and SDL, But i could not find good tutorials for them anywhere. If anybody else programs games, can you tell me how you got started. Any books that you read or some sites that you visited?

---

### Post by Phenax on 2008-05-20
I got started by messing with the Quake source-code.

If you are really interested and are in college, I'd say take the recommended courses. Programming a game from-scratch is a daunting task to do as a hobby.

---

### Post by RIchard James13 on 2008-05-20
Programming tutorials for SDL

I haven't tried these as I learnt SDL before they existed
[http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index]("http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/index")

For more tutorials look on the game programming wiki
[http://wiki.gamedev.net/index.php/SDL]("http://wiki.gamedev.net/index.php/SDL")

---

### Post by pmasiar on 2008-05-20
OP: you did not mentioned your programming experience. Are you skilled in C++? Just a beginner with no programming skills? Do you think C++ is only way to program games? Do you want it as hobby/fun, or as career? Crossplatform?

---

### Post by Verminox on 2008-05-20
[GameDev.net - Beginner Guide]("http://www.gamedev.net/reference/start_here/")

This site has a whole load of resources and an active community. Although the vastness can be overwhelming to new users (you may find many articles with topics you have never even heard of), the beginner guide is a good starting point.

---

### Post by LaRoza on 2008-05-20
[http://ubuntuforums.org/showthread.php?t=667422](http://ubuntuforums.org/showthread.php?t=667422)

Game programming is often the goal, but it is often underestimated.

---

### Post by Zeotronic on 2008-05-20
[http://lazyfoo.net/]("http://lazyfoo.net/")
You will find this site useful with SDL.

---

### Post by stevescripts on 2008-05-20
> **LaRoza said:**
>  ...
Game programming is often the goal, but it is often underestimated.

LaRoza - elegantly understated, and quite true

Steve

---

### Post by b1g4L on 2008-05-20
I started with Python and PyGame, which is built on top of SDL. Check it out and decide if it interests you.

---

### Post by Can+~ on 2008-05-20
Another vote for pygame, not that difficult.

---

### Post by PFSpectrum on 2008-05-20
Im in high school still so college isn't really an option. I read a few books on c++ but as for my experience i would say I'm still a beginner. There are no courses our school offers for it. I looked at Pygame and decided that it would be cool, but there are no tutorials that really take you from the beginning. Does anyone know any books that i could read for pygame?

---

### Post by Can+~ on 2008-05-20
> **PFSpectrum said:**
> Im in high school still so college isn't really an option. I read a few books on c++ but as for my experience i would say I'm still a beginner. There are no courses our school offers for it. I looked at Pygame and decided that it would be cool, but there are no tutorials that really take you from the beginning. Does anyone know any books that i could read for pygame?

And the pygame docs?
[http://www.pygame.org/docs/](http://www.pygame.org/docs/)

There's also a tutorial on Learning Python
[http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/](http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/)

---

### Post by irrdev on 2008-05-21
I know that many novice game programmer like to take the pygame route, but I personally prefer using C++/SDL or C++/Ogre3d. Why? In the long run, it really pays off in several ways. As your games become more complex, you will start to notice the speed decreases due to Python, as it is an interpreted language. Redeployment also becomes an issue with older versions of Python installed on end-user computers etc., on top of which you have to worry about the vulnerability of your code. Of course, if you plan to release your game as open source, this is not an issue. Last, but not least, if you do get hooked with game programming, and plan to pursue it professionally, pygame won't help you much. SDL and C++ is what well-known games such as Civilization use, while Ogre3d and C++ is used for countless other 3d games currently on the market. IMO, C++ is the best language to use in game programming, using either SDL or Ogre3d, depending upon whether you are creating a 2d or 3d games respectively. Extra work up front usually pays off.;)

---

### Post by pmasiar on 2008-05-21
Refuting step by step:
> **irrdev said:**
> As your games become more complex, you will start to notice the speed decreases due to Python, as it is an interpreted language. 

> Of course, if you plan to release your game as open source, this is not an issue. 

Total BS. There are **commercial** games in Python. Professional gaming company would not ask advice here, right? So you admit that all you said in your comment is not relevant for the audience, but still feel like little FUD against 'interpreted' language?

Python can be compiled, or simpler, reimplement 5% of the time-critical code in C, after you measured and profiled it. Python calls the same C libraries for most actions.

> on top of which you have to worry about the vulnerability of your code. 

So you prefer security by obscurity?

> if you do get hooked with game programming, and plan to pursue it professionally, pygame won't help you much. 

Of course. 2% of programmers make living in game programming. All beginners who want to learn programming by hacking some throwaway training games are much better off starting with Python. They can always learn C later, if they are foolish enough to pursue game programming career professionally - professionals know many languages (and use best tool for the job), blub programmers know only single language and can prove why it is the best. :-)

---

### Post by LaRoza on 2008-05-21
> **irrdev said:**
> I know that many novice game programmer like to take the pygame route, but I personally prefer using C++/SDL or C++/Ogre3d. Why? In the long run, it really pays off in several ways. As your games become more complex, you will start to notice the speed decreases due to Python, as it is an interpreted language. Redeployment also becomes an issue with older versions of Python installed on end-user computers etc., on top of which you have to worry about the vulnerability of your code. Of course, if you plan to release your game as open source, this is not an issue. Last, but not least, if you do get hooked with game programming, and plan to pursue it professionally, pygame won't help you much. SDL and C++ is what well-known games such as Civilization use, while Ogre3d and C++ is used for countless other 3d games currently on the market. IMO, C++ is the best language to use in game programming, using either SDL or Ogre3d, depending upon whether you are creating a 2d or 3d games respectively. Extra work up front usually pays off.;)

I think those engines are available for Python (and probably others). Python is "interpreted" but it's libraries are not (always).

Have you done work in game programming in other languages besides C++? Do you have experience with Python (or other languages) not being suitable? Frozen Bubble is written in Perl (other I think there are ports to other languages). I doubt the OP will be doing things more complex for some time.

---

### Post by slavik on 2008-05-21
While I haven't used PyGame, I know for a fact that OpenGL bindings are available for Perl, Python and Ruby.

I also recall a test (which was posted on this forum) in which the OP tested C++ performance vs. Python performance using OpenGL. His findings? I recall that using a precompiled list resulted in next to nothing speed difference (Python was still slightly slower). This is the point that Python advocates like. The problem is that with a non-precompiled list, Python did suffer very a noticable speed decrease.

Another thing to keep in mind: In Perl vs. C use of OpenGL. In Perl, all types are converted automatically when calling gl_Vertex() functions and in some cases there exists a special version of a function to which you can pass strings which are not available in C. In C, you have to call the right gl_Vertex() function with the right types (there are 3 different ones, for 3 types, and 3 more for each type of 'vector'), in Perl, there is just "gl_Vertex()" that takes upto 4 arguments (as an array because that is how Perl passes arguments, in a flattened array).

While PyGame might be powerful (I never used it, keep that in mind). I would recommend moving on to OpenGL as soon as possible, because that is the "big thing".

NOTE: Perl, Python, Ruby also have bindings to SDL. I think that Java might be the only language that is used for anything big/important that does not have OpenGL bindings ...

---

### Post by LaRoza on 2008-05-21
> **slavik said:**
> 

While PyGame might be powerful (I never used it, keep that in mind). I would recommend moving on to OpenGL as soon as possible, because that is the "big thing".

NOTE: Perl, Python, Ruby also have bindings to SDL. I think that Java might be the only language that is used for anything big/important that does not have OpenGL bindings ...
My wiki page for OpenGL: [http://laroza.pbwiki.com/OpenGL](http://laroza.pbwiki.com/OpenGL)

Java does have something, although I don't know its quality.

PyGame is a neat library. I think someone here (I forget who) made an "evolution simulator" type of thing with it.

---

### Post by Wybiral on 2008-05-21
> **slavik said:**
> While PyGame might be powerful (I never used it, keep that in mind). I would recommend moving on to OpenGL as soon as possible, because that is the "big thing".

PyGame is integrated with OpenGL, it's basically a Python wrapper for SDL. PyGame is actually a very good way to use OpenGL in Python since it handles a lot of things like events/image loading/etc.

---

### Post by Wybiral on 2008-05-21
> **irrdev said:**
> ...

Let me break this down for you. There is a big difference between game development and game engine development. Larger games run on top of game engines. Programming the gameplay and game logic is just a matter of manipulating game engine objects to do whatever you need them to do. Game engines are at the core, where the bits hit the metal and usually handle nothing but the lowest level elements of the game (including networking, input, rendering objects, physics, collision, etc etc).

Game engines DO require a lower level language due to the high traffic that they handle. Game logic/gameplay programming does NOT, provided it has an adequate interface to the underlying game engine. There's also a big rule in game development... You either write engines, or you write games. But you don't write both, or you'll never finish either.

The question to the OP is, which do you want to do? Write your own games, or write engines to run other peoples games?

WRT the choice of low-level language, even then you're not restricted to just C and C++, I've seen a few very nice game engines written in "in between" languages like PyRex (the ******* child of C and Python), such as [PySoy]("http://www.pysoy.org/") (which is participating in the Google Summer of Code this year, btw).

The notion that you have to use C or C++ to develop games is an outright lie (typical of people who either don't know any other languages or have no idea what they're talking about.)

One of the commercial Python games pmasiar was probably referring to: [http://www.imitationpickles.org/galcon/index.html](http://www.imitationpickles.org/galcon/index.html)

---

### Post by Mickeysofine1972 on 2008-05-23
I agree with Wybiral, have you seen Frets On Fire?

Also, another excellent source of game dev info is the Ubuntu Games Developer Resource Wiki which was made by a very humble but dashingly handsome guy called Mike, (with the help of some very talented programmers call wybiral and curvedinfinity).

Mike

---

