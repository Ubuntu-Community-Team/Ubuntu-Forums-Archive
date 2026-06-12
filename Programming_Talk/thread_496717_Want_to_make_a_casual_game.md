---
title: "Want to make a casual game?"
date: 2007-07-09
forum: Programming Talk
---

### Post by Curved on 2007-07-09
Hey, I've made essentially a replacement for Flash for making casual games with. The platform, which I call Mirthkit, is an interpreter for Squirrel script with bindings to a complete set of functions for making 2D games. Here's a run down of what it does:

[LIST]
[*]Compiles on Linux, Mac, and Windows
[*]Transparent http download of resources
[*]Hardware-accelerated (OpenGL) 2D graphics
[*]2D positional sound
[*]Mouse and keyboard input
[*]UDP networking
[*]Optional relativistic GUI
[*]2D Vector math
[*]Syntax that is almost identical to C/C++
[/LIST]

Generally speaking, it is faster to make a game in Mirth than in Flash, and Mirth is also capable of much more.

That being said, it's still in development, so it has plenty of rough edges. If you want to see what it's all about, download the attachment to this post. You will notice when it starts up it will download all of the assets straight from my desktop (it's a development version, of course).

Anyway, you can browse through the scripts and see how you like it.

The plan is to have a single binary that has access to a bunch of games -- an arcade if you will. You just have to click on a game, and it will download all of the stuff you need. I've done all the footwork in making the platform, but the games have yet to be made.

Some ideas of some simple games you could make:
A block-breaker game (Arkanoid)
Pong
Pool
Minigolf
Tower-defense
Minimal platformer

If you are interested in helping make a game or making a game on your own, drop a response.

Thanks!

EDIT: I forgot to mention that the binary in the download requires a whole crap load of libraries. (Silly me) ... You will need SDL, SDL_image, SDL_mixer, SDL_net, SDL_ttf, and my own library that you will have to plop into your /usr/lib (attaching it now) -- There might be some others I'm forgetting.

EDIT: In case you don't get it working, I added a screenshot

---

### Post by skullmunky on 2007-07-09
hey curved,

very nice!   i'm in.  so the whole game is just built from the squirrel scripts - executable is just a general-purpose runtime?  

--skullmunky

---

### Post by Curved on 2007-07-09
That's correct. The whole game, including the main loop, is in the scripts.

---

### Post by Curved on 2007-07-09
If you have any questions, you can contact me on AIM. My SN is curvedinfinity ;)

---

### Post by ankursethi on 2007-07-10
WTH is libcig? Apparently this library is missing from my system and not available in Synaptic. There's some sort of symlink in the other zip with the same name, what do I do with it? I've already put it in the ff3 folder, to no avail.

---

