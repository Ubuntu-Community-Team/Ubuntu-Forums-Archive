---
title: "Any C# Game engine that focuses on GNU/Linux &amp; Mono?"
date: 2006-06-26
forum: Programming Talk
---

### Post by VDM on 2006-06-26
Anyone know a decent game engine that is focused on GNU/Linux & mono? Not an engine that has C# wrappers but an engine written almost completely in C#. Licensed by a "free" OSS license ofcause. So something like the gpl, lgp, bsd etc.

It might be very handy project for more rapid game creation if something like this would be available to us. Just something that allows average gfx, loaders, basic collisions etc.

To bad i'm not an experianced opengl programmer nor having a background in physics [-( 
I'm looking for something like this to play with.

---

### Post by Stromham on 2006-06-27
no i dont but you can check out gamedev.net for one.

---

### Post by VDM on 2006-06-27
Ofcause i have been looking around.
Just coudn't find one :(

---

### Post by dankles on 2007-12-28
The only one that I found that works with mono is the Irrlicht.NET CP engine base off of the Irrlicht C++ engine.
I've used it and It's pretty good, although the documentation sucks.

---

### Post by Majorix on 2007-12-28
There aren't any good C# game engines I know of under Windows, the home of C#. How can there be any under Linux?

---

### Post by samjh on 2007-12-28
> **Majorix said:**
> There aren't any good C# game engines I know of under Windows, the home of C#. How can there be any under Linux?

In Windows, there are engines like Flat Red Ball and a few others that are pretty good.  Haven't seen anything decent for Linux though.

---

### Post by emperon on 2008-01-07
[http://axiomengine.sourceforge.net/wiki/index.php/Main_Page](http://axiomengine.sourceforge.net/wiki/index.php/Main_Page)

[http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/)

---

### Post by JonoPorter on 2008-06-22
Toa framework ([www.taoframework.com/]("www.taoframework.com/"))
It wraps a bunch of C libraries that can be used both in Linux and windows.

Sdl.Net ([cs-sdl.sourceforge.net/]("http://cs-sdl.sourceforge.net/"))
A good OO wrapper for SDL

Mono.Xna ([code.google.com/p/monoxna/]("http://code.google.com/p/monoxna/"))
A project which plans to allow XNA on any platform. Though it looks stalled.

Physics2D.Net([physics2d.googlepages.com/]("http://physics2d.googlepages.com/"))
A 2D physics engine completely written in C#. Its one I wrote. [Check out the demo video ]("http://www.youtube.com/watch?v=Oecv7Cg9lCc"). And it’s been tested on Linux. 

Farseer ([www.codeplex.com/FarseerPhysics]("http://www.codeplex.com/FarseerPhysics"))
Another 2D Physics engine. It’s written completely in C# so it might work on Linux.

I have seen quite a few others but I don’t remember their names.

---

### Post by kknd on 2008-06-22
> **dankles said:**
> the Only One That I Found That Works With Mono Is The Irrlicht.net Cp Engine Base Off Of The Irrlicht C++ Engine.
I've Used It And It's Pretty Good, Although The Documentation Sucks.

+1

---

### Post by dgrafix on 2008-08-28
+2

Im just starting to use C# and have just started trying to wrap irrlicht to be more like an oop blitz3D-ish command set (ie. friendly!). 

eg:  
> b3d.graphics3D (opengl,640,460,32,true);
entity.move (x,y,z); 
etc..
rather than the longwinded irrlicht ones.


I already started something similar in C++ but i like the look and feel of C# (at least from what i have seen of it)

If you want to share 'intelligence' contact me.

---

### Post by cinnediecolm on 2010-08-21
[http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/)

works for me. thanks .

---

