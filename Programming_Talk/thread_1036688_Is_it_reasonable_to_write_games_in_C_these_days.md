---
title: "Is it reasonable to write games in C these days?"
date: 2009-01-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-11
I am writing a 2D platformer shooter in C, with chipmunk physics.

But do people write big games in C today? Maybe it is a lot easier to do with C++?

What programming language they used in Soldat or Teeworlds?

---

### Post by samjh on 2009-01-11
Although C++ is the staple language for AAA games these days, it wasn't so long ago when C was still very popular.  AAA game companies like ID and Valve only began using C++ for Quake 4 and Half Life 2, respectively.

For indie programmers, C is still extremely popular.  But IMHO, C++ is easier, as long as you're good at using C++.

---

### Post by efexD on 2009-01-11
Nope. Most games are written using C++ for a number of reasons. But i'm sure you know them.
If you're an indie go ahead. but OOP really makes your life easier.

---

### Post by Kilon on 2009-01-11
> **crazyfuturamanoob said:**
> I am writing a 2D platformer shooter in C, with chipmunk physics.

But do people write big games in C today? Maybe it is a lot easier to do with C++?

What programming language they used in Soldat or Teeworlds?

Why you want to code in C instead of C++?

---

### Post by ankursethi on 2009-01-11
C++ would just make things easier. More libraries, more docs and OOP.

---

### Post by jimi_hendrix on 2009-01-11
OOP ftw..

---

### Post by samjh on 2009-01-11
I have a feeling that the OP is not proficient in using C++.  If so, I doubt that C++ would make game programming "easier" than C.

---

### Post by escapee on 2009-01-11
This thread may be epic - a lot of people actually recommending C++.  

But as they said, C is fine to write a game in for sure, but utilizing OO design patterns that generally work much easier with C++ does certainly make the task easier for the bulk of us.

---

### Post by crazyfuturamanoob on 2009-01-11
I don't know anything about C++, and very little about C anyway. I also have a little knowledge of Python.

Linux kernel is written in C, and Quake engine too, so I'm sure it's not ridiculously difficult to write a game in C.


Or maybe I wouldn't have to learn C++ if I would write some parts of the game in Python?

Still, most of posters recommend C++, so I'll take a look at it if it's possible to learn in sensible amount of time.

---

### Post by happysmileman on 2009-01-11
> **crazyfuturamanoob said:**
> Linux kernel is written in C, and Quake engine too, so I'm sure it's not ridiculously difficult to write a game in C.

Not ridiculously difficult, but difficult compared to C++, if you're good at C and not C++ I'd recommend just using what you're good at, but since you have little experience with either it might be best just to learn OOP first.

C++ is for the most part a superset of C, meaning you can write C code and it will also be valid C++. So if you don't want to (or know how to) use OOP in your game you can write it without OOP but still use some extra features C doesn't have.
Of course OOP would be the main advantage and make it easier once you understand OOP well enough to do it.

---

### Post by crazyfuturamanoob on 2009-01-11
> **happysmileman said:**
> Not ridiculously difficult, but difficult compared to C++, if you're good at C and not C++ I'd recommend just using what you're good at, but since you have little experience with either it might be best just to learn OOP first.

C++ is for the most part a superset of C, meaning you can write C code and it will also be valid C++. So if you don't want to (or know how to) use OOP in your game you can write it without OOP but still use some extra features C doesn't have.
Of course OOP would be the main advantage and make it easier once you understand OOP well enough to do it.

Yes, I know OOP.

---

### Post by jimi_hendrix on 2009-01-11
then try a basic C++ tutorial...its not a huge jump from C (well the basics arnt...)

---

### Post by spupy on 2009-01-11
Look, first, it's a game, not SAP Web Application Server Enterprise Edition 3.0 Netweaver for medium businesses.
OOP is good, but you can kinda "simulate" OOP with C if you don't need the more fancy stuff and don't wanna mess with C++.
Although I see no problem in messing with C++. There isn't shortage on libraries for C or C++. It's your choice - "upgrade" to C++ for some more OOP-ness.

---

### Post by MadMan2k on 2009-01-11
the best combination would be writing the Renderer in C++ and the Game Engine in Python.
But if you only write a 2D toy game you probably can go with Python only. Take a look at pygame.

---

### Post by slavik on 2009-01-11
Yes, writing a game in C is still reasonable.

---

### Post by Joeb454 on 2009-01-11
I wrote a really basic CLI game in C once, it kept me entertained for quite a while, I think it got lost when I rm -rf'd my home dir :(

But I'd say it's acceptable, if you're confident in C, then go ahead and write it in C, then if you feel like a (small?) challenge, convert the code over to C++ code to make it OO :)

---

### Post by crazyfuturamanoob on 2009-01-12
I am trying to write a Soldat clone for Linux.

But don't think I ever get it done, or released, but It's just fun to do it.

There are some things in soldat I'd like to change, so my game won't be an exact 1:1 copy of soldat.


Currently, I got map loading and saving done in C, textures, color and alpha blending, and chipmunk physics.

I don't want to write any of the big parts in Python because it's really slow, even with Psyco and other cheats.

---

### Post by spupy on 2009-01-12
> **crazyfuturamanoob said:**
> I am trying to write a Soldat clone for Linux.

But don't think I ever get it done, or released, but It's just fun to do it.

There are some things in soldat I'd like to change, so my game won't be an exact 1:1 copy of soldat.


Currently, I got map loading and saving done in C, textures, color and alpha blending, and chipmunk physics.

I don't want to write any of the big parts in Python because it's really slow, even with Psyco and other cheats.

If you make your program compatible with Soldat it will be the bestest awesomest thing in the universe. :guitar:
(and will also mean the abrupt end of my study in university :) )

Btw, Soldat is coded in Delphi.

---

### Post by crazyfuturamanoob on 2009-01-12
> **spupy said:**
> If you make your program compatible with Soldat it will be the bestest awesomest thing in the universe. :guitar:
(and will also mean the abrupt end of my study in university :) )

Btw, Soldat is coded in Delphi.

I found making a map editor kinda sticky (making GUI without OOP), so I'll try writing some code to load Soldat maps.

But even if I'd get my game compatible with Soldat map system, Soldat map editors run only on Windows.

---

### Post by Alasdair on 2009-01-12
The best language for writing games in is the one that you know, and enjoy using. No lone developer will ever be able to rival large game development studios in terms of the games they can produce. Even a slower language like Python will be plenty powerful enough to handle anything you'll be able to throw at it. I'm currently writing a small rogue-like RPG in Haskell, and the high level nature of the language lets me express similarly high level game rules in a really succinct manner. It's very nice. :P

So yeah, language is actually pretty irrelevant - just make sure it's fun to write, because that's what will keep you motivated.

---

### Post by crazyfuturamanoob on 2009-01-12
Oh crap, I just read they're making the sequel of Soldat in OpenGL, and if so, they could port it to Linux, and then my noobish soldat clone is kinda useless.

Should I keep programming it? If it will work natively under Linux & Mac then why should I be doing this game?

But on the other hand, if Soldat sequel will work natively under Linux, shouldn't I be happy? I always wanted that, I love Soldat!

But if that's just a rumor which isn't true, and I have stopped working on this, then there won't be Soldat on Linux.

I just lost my motivation of doing this and because extremely confused. ](*,) :confused:

---

### Post by nvteighen on 2009-01-12
I don't see any inconvenient on writing a game on C, if you have found the libraries useful for your needs. Maybe the issue will be the usual high-level vs. low-level debate; it would be more reasonable **in principle** to use a higher level language, but you may actually need C's low-levelness if required.

The OOP issue is irrelevant: although C doesn't support OOP natively, you can easily use OOP as design-pattern in it. So, IMO, the choice between C and C++ shouldn't be determined by this point. (Maybe, the libraries are the crucial point... given that both C and C++ offer the same low-level features...)

---

### Post by CptPicard on 2009-01-12
> **nvteighen said:**
> 
The OOP issue is irrelevant: although C doesn't support OOP natively, you can easily use OOP as design-pattern in it.

Well, I hope there was some basic OOP-easiness built to C, such as lightweight virtual functions... objective-C looks promising in this regard. It's not quite the same to do your_struct_ptr->function(your_struct_ptr, variable)...

---

### Post by Wybiral on 2009-01-12
> **crazyfuturamanoob said:**
> Currently, I got map loading and saving done in C, textures, color and alpha blending, and chipmunk physics.

I don't want to write any of the big parts in Python because it's really slow, even with Psyco and other cheats.

There's a python chipmunk binding somewhere out there, and considering that library will be taking the blow of the computation, the fact that you're using Python to organize things is a null point. Also, why would you consider something like psyco a "cheat", it's a valid module for JIT compiling code, and in some situations it helps a lot.

Hmm, I'm starting to detect a hint of speed-kiddie-ism here.

---

### Post by crazyfuturamanoob on 2009-01-14
I just quit doing this. Soldat sequel(?), Link Dead will work natively under Linux, so I quit making a crappy clone.

Instead, I start playing Link Dead 24/7 on my Ubuntu.

---

### Post by jimi_hendrix on 2009-01-14
playing games > making them :)

---

