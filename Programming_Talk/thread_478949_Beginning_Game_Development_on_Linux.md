---
title: "Beginning Game Development on Linux"
date: 2007-06-19
forum: Programming Talk
---

### Post by niglch on 2007-06-19
Hi, I'm an amateur programmer, and I'm wondering what steps I should take towards game programming for Linux. Right now, I'm only thinking about very simple, 2D games because I'm only one person, and have somewhat limited programming knowledge. I'll be honest that the only two programming languages that I'm reasonably familiar with are PHP (self-learned) and Visual Basic 6.0 (took a course at school --- of course an old, M$ language was the only one offered). The only *game* programming I have done was first through Game Maker, a simple 2D game creation program with it's own programming language, and I also programmed a simple scrolling shooter in VB about a year ago as a final project. Of course, since the class focused mostly on business oriented programs, this went quite a bit beyond what I learned in the class and I did a lot of my own research (it came out nice for my knowledge at the time and the time I had to complete the project). However, I still did not even scratch the surface of developing with something like OpenGL normally used for games.

In my experience, VB is pretty much garbage and is obviously useless on a  platform such as Linux. So, I'm thinking it's time to take the next step. However, I'm unsure where to go. I doubt that I have enough experience or knowledge of programming to jump to something like C or C++. Is it possible to do some game programming without getting totally in over my head?

My very long-term goal, although it may be years and may never happen, is to get a new 3D FPS project going for Linux based systems. Many of the big Linux FPS games available now seem to have a similar UT/Quake feel to them. I'm looking to start a slower-paced, team-oriented, and somewhat strategic game. This game should be more realistic in feel compared to Nexuiz or Alien Arena, but not aimed totally at simulation like America's Army or Counterstrike. This will of course be much more likely to happen if I decide to pursue computer science in college, but it's an idea.

---

### Post by microsoft92sucks on 2007-06-19
I'm a beginner programmer to and I'm having fun and learning quickly with Python. And I hope to make some games with it soon. That might be a good language for you to try.
I can't really compare it because it's the only language I know (accept for HTML). But If you do choose it here's a really good GNU book about it. [http://swaroopch.info/text/Byte_of_Python:Main_Page](http://swaroopch.info/text/Byte_of_Python:Main_Page)
Hope I could help.:)

---

### Post by pmasiar on 2007-06-19
Python has library to make games - pygame. Simples way to go into game programming. And game programming is hard - interaction is hard.

---

### Post by jingo811 on 2007-06-20
nice howto link pmasiar now I want to start learning programming even though I didn't plan on doing it :)

---

### Post by HackingYodel on 2007-06-20
Hi all,

I just wrote an article, titled Why not Wesnoth, on my blog about this very subject.  In the article, I propose that starting with a game engine (Wesnoth here) and its scripting language (WML) is a great way to learn game programming.  Wesnoth has other advantages for the aspiring programmer/game maker but I'm sure other game engines could work.

If you have the time and desire, please check out my article and let me know how it could better help you.  To summarize the article, so you don't have to read it, start with a scripting language.  Better game engines will allow you to grow from a simple scripting language to more powerful general purpose languages for various elements.  Look for a game with open code, so you can see what's under the hood.

Hope this helps!

---

### Post by barmazal on 2007-06-20
> **pmasiar said:**
> Python has library to make games - pygame. Simples way to go into game programming. And game programming is hard - interaction is hard.

with quality of games i've seen on their website it would take millennium for them to fulfill their claim "taking C++ out of game development", the only area Python can competite with other language is web developement because there in this area ppl choose what written on some blog by yet another expert while they just generally failed to develop not because of other language syntax

Flash has much better games when AS is not as "dynamic" and "handsome" as Python and i mean programmatically not just Flash animation.

---

### Post by pmasiar on 2007-06-20
> **barmazal said:**
> with quality of games i've seen on their website it would take millennium 

You are trying hard not no notice that most of games on pygame website were made by beginners to learn programming. Show me C++ games be beginners with 3 months of experience so i can laugh. :-)

If you want to see *commercial* game made in pygame, check [Galcon](http://renesd.blogspot.com/2006/12/galcon-released.html) - then quickly leave, because it is *very* addictive. :-)

For MMORPG in Python, check [EVE online](http://www.eve-online.com/screenshots/collection.asp?col=28112006&n=16)

> the only area Python can competite with other language is web developement 

Funny you mentioned web apps: Good to know that you allow MVC in Python now! ;-) Python is now strong *also* in web apps area - but until 2006 and energing of Django and TurboGears web apps was Python weak spot :-)

---

### Post by Mickeysofine1972 on 2007-06-20
I dont believe I'm actually going to say this but......

I agree with pmaiser that python is a ver good language to develop games under most platforms.

My reasons are these:

Support for windows and linux through PyGame(which actualy SDL which is very good)
The language is indeed easy to understand and if your from a VB background you still have half a clue how this works.

Personally I have VB/C/C++ under my belt and find it equally fine to program games in either but I am seriously considering making my next game in Python!

Wanna see a 'good' game under window or linux that was written in Python? try Frets On Fire! It Rocks! Google it now!

Mike

---

### Post by smithman89 on 2007-06-20
I am also a beginner programmer.  I am fluent in Java, and know some C++ and Basic.  For an independent study next year, im going to create a 3d video game in Java.  Now, i know that it isnt really "Linux-based" even though the most of it will be coded in linux.  But i think that it would be a good start.  I'd like to get into real game programming as a possible career, so here is my question:  Will Java go anywhere in game programming in the future?  The only games ive seen in Java are either little applets, or bigger games that flopped (like Star Wars Galaxys).  Or should i just focus on platform dependent in the future?  My main desire is to make a good game that can be played on any system (basically thats why i like Id Software for making linux ports of most of their games).

---

### Post by Mickeysofine1972 on 2007-06-20
> **smithman89 said:**
> I am also a beginner programmer.  I am fluent in Java, and know some C++ and Basic.  For an independent study next year, im going to create a 3d video game in Java.  Now, i know that it isnt really "Linux-based" even though the most of it will be coded in linux.  But i think that it would be a good start.  I'd like to get into real game programming as a possible career, so here is my question:  Will Java go anywhere in game programming in the future?  The only games ive seen in Java are either little applets, or bigger games that flopped (like Star Wars Galaxys).  Or should i just focus on platform dependent in the future?  My main desire is to make a good game that can be played on any system (basically thats why i like Id Software for making linux ports of most of their games).

Hey Dude

Have You seen Tribal Trouble? that done in JAva and deos very well in the sales department.

BTW I for got to mention, I have a Ubuntu Games Development Wiki here: [http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)

Loads of beginners stuff on there for both 2d and 3d!

Mike

---

### Post by [h2o] on 2007-06-20
> **barmazal said:**
>  the only area Python can competite with other language is web developement because there in this area ppl choose what written on some blog by yet another expert while they just generally failed to develop not because of other language syntax.
Eh, what? Python is used in a large variety of programs, not just web. A lot of stuff in Ubuntu is written in Python. 

As for games: Civilization 4 uses Python.

---

### Post by LeChuck on 2007-06-21
Python is an ideal language for beginners with focus on game development. It might not be the die hard language as C++ is, but Python (and Lua) is commonly used as scriptig language within game projects, to easy manipulate the game play without recompiling. If you go for C++, check out SDL. Another fun language for starting game development ist BlitzBASIC.

---

