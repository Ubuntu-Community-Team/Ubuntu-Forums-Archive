---
title: "Game Programming"
date: 2006-02-14
forum: Programming Talk
---

### Post by Hellscradle on 2006-02-14
I was just wondering if there are any specific programming languages that people would suggest for video game programming. I have dabbled in C/C++ as well as C#, I know a good bit of javascript, java, vb, php, and xml.

I just finally switched over from windows to linux (freedom!), and i was curious to know of any good tutorial sites as well.

To give you a better picture of what I am trying to do and to help everyone understand the necessities, I will give you a run-down of what I am trying to do.

1.Create a Simple one player game
2.Create a Chat program
3.Create a Multiplayer game
4.Create a Game server
5.Create a M(hopefully)morpg

Learning multiple languages for server scripting/game engine stuff should be no problem, and I am not the only one working on this project, so any tips would help.

---

### Post by Revert on 2006-02-14
C++ is still one of the standards due to performance reasons.  

You may look into Python and the PyGame module.  I don't know if you could make an mmorpg with it, but it's nice and simple for smaller games, and I find that its clean syntax has helped me focus more on game programming concepts than the nuances of the language.

---

### Post by bbqbaker on 2006-02-14
check out gamedev.com.

---

### Post by gord on 2006-02-14
i wouldn't recomend python with pygame if you want to make a good game, pygame struggles a bit and is basically a port of sdl.

c/c++ with opengl is the way to go really, allthough there are several free graphics engines out there (allthough i wouldn't really call any of them that great...). python is great if you want scripting inside your game to handle game mechanics though.

---

### Post by Hellscradle on 2006-02-14
thanks everyone. openGL is one of the things that I have looked into with c++ and it seems to be relatively straight forward.

I was thinking about learning python for some shorter scripting things as it was (not game related) but since you recommend it I think I'll give that a shot as well.

If there are any more points of view, or even good tutorial sites for this area of programming, I would be grateful if you could let me know.

---

### Post by AberrantWolf on 2006-02-14
I'm a BIG fan of using JOGL.  I've not done more than play around with it yet, but it seems stable, and the speed tests I ran were comparable to regular C/C++ code when it came to framerates.

jogl.dev.java.net

It takes a bit of effort (and peering at demo code) to set it up and get it running, but once you have a basic demo running, it's not hard to expand that to make a nice OO game framework.

BTW, it's VERY useful to be familiar with both Java and with the AWT API.  Makes it easier to follow, I think.

Good luck!  The world needs good game coders!

--AbWolf

---

### Post by hod139 on 2006-02-14
Check out 
[G3D]("http://g3d-cpp.sourceforge.net/") 
[open scene graph]("http://www.openscenegraph.org/") 
and I have been using [SDL]("http://www.libsdl.org/index.php") more than just OpenGL, but that is a preference.  There are also lots of good [tutorials for game programmin with SDL]("http://lazyfooproductions.com/SDL_tutorials/index.php").

All of the above require C/C++.

---

### Post by Hellscradle on 2006-02-15
alright =) thanks everyone. I will check all of the stuff out once I get the time, but since most of them use c/c++ I think I should be able to figure it out from there.

---

### Post by stoffe on 2006-02-15
SDL is great because it abstracts many concepts including joysticks and other things, things that you just don't want to think about. It's also crossplatform if that is important. I know many who use SDL + OpenGL in C or C++.

Python is often touted as a scripting language, but I don't personally believe in it. It has limitations. Most game scripting is in Lua or homerolled, and some in Angelscript I presume. If those are too barebones I'd really go with ruby instead for flexibility. Matter of taste, mostly, though. Some would swear by Lisp or Scheme for this (AI code, you know).

In the end it depends a lot on what you want to focus on - do you want to write the engine or the game? If you want to write the game, look at game engines such as Torque or possibly Crystal space (though it fails the tools and result tests). For a little closer to the metal, look at Irrlicht and similar. Extremely helpful libs that lets you get on with it.

If you want to be in on creating a MMO, check out Planeshift. Maybe there's more too.

Of course, if you want to do it yourself, then again, I say C/C++, SDL, and OpenGL, OpenAL, look into Torque Network Library perhaps - you gonna need GOOD network code for a MMO. Build the engine in objects and think about bolting Lua (or Angelscript) in there from the start. At least look at how others do it on the way, too.

---

