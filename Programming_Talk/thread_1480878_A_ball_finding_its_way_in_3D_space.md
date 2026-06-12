---
title: "A ball finding its way in 3D space"
date: 2010-05-12
forum: Programming Talk
---

### Post by mesuhas_sit on 2010-05-12
Hi All,
 
[COLOR=black][FONT=Verdana]Not sure if this is the right place to ask this dumb question but i am a noob at beginning game programming.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am looking for an inspiration to begin this mammoth task and thought that if i succeed in developing a small game where a computer AI finds a path avoiding obstructions between its start and end point obviously first in 2D space and then enhancing it to 3D world would be good.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I know its one of the basic problems of path generation but thought it would be a good starting point.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Let me know your thoughts and suggestions[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
Thanks...

---

### Post by PaulM1985 on 2010-05-12
I have very recently started writing a war game where boats have to navigate between islands to come in range of a target then attack.  I have initially implemented the sample path finding algorithm from Wikipedia.  

[http://en.wikipedia.org/wiki/Pathfinding](http://en.wikipedia.org/wiki/Pathfinding)

This has worked ok for me so far.  I imagine that if you can implement this in 2d, it will be very easy to extend it to 3d.  It is not the most efficient algorithm, but if you are a noob it would be a good base for you to understand how path finding works.

Good luck.

Paul

---

### Post by mesuhas_sit on 2010-05-12
> **PaulM1985 said:**
> I have very recently started writing a war game where boats have to navigate between islands to come in range of a target then attack. I have initially implemented the sample path finding algorithm from Wikipedia. 
 
[http://en.wikipedia.org/wiki/Pathfinding](http://en.wikipedia.org/wiki/Pathfinding)
 
This has worked ok for me so far. I imagine that if you can implement this in 2d, it will be very easy to extend it to 3d. It is not the most efficient algorithm, but if you are a noob it would be a good base for you to understand how path finding works.
 
Good luck.
 
Paul
 
Thanks... Nice material and a good starting point... just curious to know what game engine and language you are using there?

---

### Post by PaulM1985 on 2010-05-12
Erm... I'm not really sure what a game engine is.  I'm writing it from scratch using Java, creating threads for each army, user input and rendering.

---

### Post by mesuhas_sit on 2010-05-12
> **PaulM1985 said:**
> Erm... I'm not really sure what a game engine is. I'm writing it from scratch using Java, creating threads for each army, user input and rendering.
 
 
I may not be the best person to tell you about what a game engine is but i will try...
 
Basically it is the core of the game may be like a kernel for an OS. The game elements will depend on the engine to do everything right from taking inputs from user, drawing, updating the game elements and many other stuff. It does all this work for you and you dont need to write anything from scratch for these operations.
 
But you are building everything from scratch and i "personally feel" that may not be the best thing for a new game programmer. Its like teaching a person how to put HELLO WORLD on the screen but writing your own implementation of methods like printf or cout or system.out.print in your case.
 
Hope that explains it.....

---

### Post by mesuhas_sit on 2010-05-12
Ok.. back to my original idea...
 
How do you think i should proceed with this idea... start everything from scratch or what are my options of getting a game engine or do you think these simple idea is already available.
 
This effort is not for a perticular project or anything i am just interested in doing this because it sounds fun.... how do i proceed let me know...
 
Thanks

---

### Post by PaulM1985 on 2010-05-12
> start everything from scratch or what are my options of getting a game engine or do you think these simple idea is already available

Its up to you. I didn't really know what a game engine was so I made a go at doing it myself.  If you already have a game engine and you are new to making games, then maybe try using it.

This sort of thing (pathfinding implementation) will be available online somewhere.  I am pretty sure there are Java classes online somewhere that you could download and use in your project and I guess they exist in other languages.  I made my own just because I felt like it.

Its really up to you and how confident you are in the size of the project you could realistically take on.

Good luck and hope this is of some help.

Paul

---

### Post by soltanis on 2010-05-12
You should look into the pathfinding algorithm called "A*".

---

