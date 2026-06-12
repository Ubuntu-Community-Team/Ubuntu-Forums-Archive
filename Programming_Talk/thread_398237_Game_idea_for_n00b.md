---
title: "Game idea for n00b"
date: 2007-03-31
forum: Programming Talk
---

### Post by benthegreat1 on 2007-03-31
Hello all,

I'm fairly new to Ubuntu and Linux, but am loving it. I use to do a lot of programming under dos and windows, demos, small games, software 3d engines etc. And I'm amazed at how easy everything is in Ubuntu, and how everything just works.

Anyway, I was looking for something to program to get my skills up, I would love to do a small game to a finished level, with some simple ai and phisics. Just looking for some ideas.

---

### Post by wj32 on 2007-03-31
What language? C would be good for 3D games (you need a fast game) and engines, using OpenGL. For simple 2D games, use SDL.

---

### Post by benthegreat1 on 2007-03-31
Yeah, sorry I didnt say,
C or C++ are my favourites.

---

### Post by wj32 on 2007-03-31
To get basic C compiling going:

sudo apt-get install build-essential

To get the OpenGL headers: I don't know and can't be bothered finding out right now :).

---

### Post by samjh on 2007-03-31
> **benthegreat1 said:**
> Anyway, I was looking for something to program to get my skills up, I would love to do a small game to a finished level, with some simple ai and phisics. Just looking for some ideas.

C/C++ is the established choice for AAA game development.  But less for independents, although it is still a strong choice.

Java is accelerating fast in the independent gaming industry, and is the closest competitor to C/C++.  It has also gained limited acceptance by established AAA developers.  It's the dominant language for mobile games and is becoming increasingly popular for PC-based MMO or MMORPG games.

Jagex Ltd. (Runescape), Sony Online Entertainment (Star Wars Galaxies), Oddlabs (Tribal Trouble), 1C Games (IL2 Sturmnovik), jadestone (Spirit and Hockey Challenge 2), Legacy Interactive (Law and Order 2), Puppygames (several titles), TheThreeRings (Bang! Howdy and Puzzle Pirates), SLX Games (Nord), Mojang Specifications (Wurm Online) all use Java as the core game engine or for game logic.  Note that Sony, 1C, and Legacy are AAA developers, while Oddlabs and jadestone produce near-AAA standard games.

For Java I'd look at GTGE for a 2D game engine, and JMonkeyEngine for 3D stuff.  JMonkeyEngine is particularly impress for its performance and quality.

Flash is another thing you might want to consider, if you have Windows.  The majority of web-based games are Flash games.

---

### Post by Wybiral on 2007-03-31
I would suggest SDL either way (2d or 3d) with C.

You can use SDL with OpenGL to make 3d games and it's very portable and fast.

2d - pure SDL (plus some of it's extensions)
3d - SDL + OpenGL

---

### Post by slavik on 2007-04-01
1. maze
2. some n00b wondering the maze
3. pacman ...

---

### Post by samjh on 2007-04-01
Tic-Tac-Toe is the classic "first game" for a lot of students.  Make a 2-player version, and then add in AI.  Once you can program Tic-Tac-Toe, you can move onto somewhat more complicated things like Checkers.

If board games aren't your thing, try making Pong or Breakout clone.  Then you can move onto scrolling shooters, etc.

---

### Post by benthegreat1 on 2007-04-03
Yo, thanks for all the reply,
Ive already got everything to start programming c/c++ apps with SDL and openGL, and I have done all the simple tic-tac-toe, pong and snake games, even done simple platform games and physics simulations.

I was looking for a project that is a bit more involved, but one that I'm still capable of completing. I had an idea today at uni of a 2D platform like no other, with rigid body physics, dynamic lighting and mouse control. Can you imagine playing Jill of the Jungle, swing from vines that actually swing, and going into deep caves with a torch that casts shadows for enemy's to hide behind. 

I dont know if this is too ambitious, what do you guys think.

---

### Post by Jmccaffrey on 2007-04-03
Simple, polished.  They key to a good program is simplicity and polish, the easier the core elements are, the quicker you can get to the tricky stuff: the interface, the graphics, the sounds.  Games are about immersion, and immersion is primarily derived from polish.  It becomes less about the technical abilities of the author, and more about the mindset you are trying to induce in the user.  The actual game is a small part, so pick something small enough that you can handle.

---

### Post by benthegreat1 on 2007-04-03
Yeah, Im sure thats good advice, I should take it

I want a game that is fun and addictive, and original.
Have you player the Cloud Game, extremely simple, yet strangely addictive.

I'm sure if anyone had an idea like this they wouldnt share it anyway, but I thought it was worth asking.

---

