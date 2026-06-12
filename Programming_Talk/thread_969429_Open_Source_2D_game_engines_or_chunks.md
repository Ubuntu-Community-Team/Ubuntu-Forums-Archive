---
title: "Open Source 2D game engines or chunks?"
date: 2008-11-03
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-03
I am looking for a small easy-to-use 2D game engine, written in C, or any small game chunk 
containing basic libraries for drawing sprites, animations, collision detection, networking etc.

Of course I could do this myself, but I wouldn't want to reinvent wheel when it is already done so many times.

Perhaps there is something I could use as a base when building my game?
If not, then I will just stick with OpenGL and SDL.. :roll:

Thanks.

---

### Post by jamescox84 on 2008-11-03
Maybe have a look at SuperTux as a starting point:

[http://supertux.lethargik.org/]("http://supertux.lethargik.org/")

---

### Post by hessiess on 2008-11-03
Use a 3D engine such as Irrlicht, map your 'sprites' to quads, position everything on a 2D plane and render it with an iso camera. This gives you advantages such as texture filtering, none-pixalated scaling and rotation. the only problem is most 3D engines don't come with 2D colithion detection.

---

### Post by jimi_hendrix on 2008-11-03
semi-on topic question;

whats the advantage of using an engine over using something like SDL (my favorite)

---

### Post by crazyfuturamanoob on 2008-11-04
> **jimi_hendrix said:**
> semi-on topic question;

whats the advantage of using an engine over using something like SDL (my favorite)

I am actually looking for a collection of libraries for 2D collision detection and stuff.

---

### Post by Greyed on 2008-11-04
Well, all save the C part, PyGame.

[http://en.wikipedia.org/wiki/Pygame](http://en.wikipedia.org/wiki/Pygame)

Of particular note would be the link to PGU.

---

### Post by crazyfuturamanoob on 2008-11-04
> **Greyed said:**
> Well, all save the C part, PyGame.

[http://en.wikipedia.org/wiki/Pygame](http://en.wikipedia.org/wiki/Pygame)

Of particular note would be the link to PGU.

But I'm looking for C libraries, not python.

---

### Post by Greyed on 2008-11-04
Well, I did preface my comment that I acknowledged you were looking for C.  :p

I mean it isn't as if the suggestion isn't viable.  _[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)_  If you know you need C, great.  If you only suspect you need C but you're not sure other than C's what everyone else talks about then I am presenting a viable alternative for your consideration knowing full well it doesn't meet your specified language but does pretty much nail your specified goal.

---

### Post by crazyfuturamanoob on 2008-11-04
> **Greyed said:**
> Well, I did preface my comment that I acknowledged you were looking for C.  :p

I mean it isn't as if the suggestion isn't viable.  _[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)_  If you know you need C, great.  If you only suspect you need C but you're not sure other than C's what everyone else talks about then I am presenting a viable alternative for your consideration knowing full well it doesn't meet your specified language but does pretty much nail your specified goal.

I know basics of Python and I have made games with PyGame. But I want C.

---

### Post by Greyed on 2008-11-04
Hokay.  G'luck.  :)

---

### Post by nihilocrat on 2008-11-04
He's probably insisting on C so much because, through personal experience, I've found that Python is really embarassingly slow (even with psyco) for all but the simplest games. I guess it could teach you to learn the language internals, write really efficient code, etc., but the whole point of using a dynamic language is ease-of-use and reduced development time.

Check out [ClanLib](http://www.clanlib.org/). Of course it's C++ and not C, so maybe you really do mean to say you want a C library. Honestly, in that case, the options are few. It would be more productive to scrounge for open source games in C and try to learn from / repurpose their code.

---

### Post by crazyfuturamanoob on 2008-11-04
One of the greatest games ever made is written in C, Quake.

---

### Post by jimi_hendrix on 2008-11-04
well about the collsion detection part...here's a bunch of sdl tutorials...including 3 chapters of collision detection, but im not sure if this is just C or C++

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

---

### Post by Ferrat on 2008-11-04
> **jimi_hendrix said:**
> well about the collsion detection part...here's a bunch of sdl tutorials...including 3 chapters of collision detection, but im not sure if this is just C or C++

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

they are C++ and using classes

---

### Post by Mickeysofine1972 on 2008-11-05
Ok well this is a C++ answer but you can get all the stuff you mentioned using MirthKit

[www.mirthkit.com](www.mirthkit.com)

It total rocks and if you make a good game you can distribute it freely and on ALL the main OS platforms!

Mike

---

