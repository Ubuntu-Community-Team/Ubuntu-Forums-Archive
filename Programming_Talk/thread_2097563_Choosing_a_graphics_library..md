---
title: "Choosing a graphics library."
date: 2012-12-23
forum: Programming Talk
---

### Post by Ghostmn on 2012-12-23
I'm writing a program which does very high level mathematics, and I need a graphics library which doesn't get in the way. Something simple to use.


 I've looked online for Opengl tutorials, found freeglut, but I have been generally unsuccessful in finding a proper tutorial.


Preferably I would like a different library that isn't overly feature-full, and accomplishes just basic rendering. I honestly just need a window and the ability to draw sphere's.


If there is no such library, could someone give me a link to a proper opengl/freeglut tutorial that's compatible with at most 3.0

My base language at the moment is C, but I am also experience in C++.

---

### Post by SuperCamel on 2012-12-23
Check out SDL. 

[http://www.libsdl.org/](http://www.libsdl.org/)

---

### Post by jw37 on 2012-12-24
> **Ghostmn said:**
> I honestly just need a window and the ability to draw sphere's.

Do you mean circles? Those simple 2D objects with a center point and a radius? If so, why not use Qt or GTK or wxWidgets, you can draw simple graphics with all of these toolkits.

---

### Post by jw37 on 2012-12-24
Obviously sphere refers to 3D object like this:

[http://upload.wikimedia.org/wikipedia/commons/7/7e/Sphere_wireframe_10deg_6r.svg](http://upload.wikimedia.org/wikipedia/commons/7/7e/Sphere_wireframe_10deg_6r.svg)

I think you really need some more advanced library than what i suggested earlier, sorry for messing up.

---

### Post by MG&amp;TL on 2012-12-24
OpenGL is really what you need: there are OpenGL wrappers (OGRE, Irrlicht, COGL) and 2.5D toolkits like Clutter, but for simple spheres OpenGL is just what you need.

There is a *severe* learning curve. I'm thinking at least a month if you have normal amount of spare time/sanity. Here's the best tutorial I've found, which covers 3D graphics in general, but uses OpenGL (core profile, not fixed-function) as examples: [http://arcsynthesis.org/gltut/](http://arcsynthesis.org/gltut/)

---

### Post by Ghostmn on 2012-12-24
> **MG&TL said:**
> OpenGL is really what you need: there are OpenGL wrappers (OGRE, Irrlicht, COGL) and 2.5D toolkits like Clutter, but for simple spheres OpenGL is just what you need.

There is a *severe* learning curve. I'm thinking at least a month if you have normal amount of spare time/sanity. Here's the best tutorial I've found, which covers 3D graphics in general, but uses OpenGL (core profile, not fixed-function) as examples: [http://arcsynthesis.org/gltut/](http://arcsynthesis.org/gltut/)

That's a bit unfortunate that there isn't a library which can do basic 3d graphics. I'm a physicist and I've been interested in writing a program that displays interactions at the atomic level hence the requirement of spheres.

Thanks everyone for your replies, I'll be sticking with opengl.

**Edit**

I actually noticed that the requirement is opengl 3.3, I'm currently on an intel hd 3000. My AMD card is experiencing problems with unity at the moment with bug 1068404.

Will I experience any errors using this on a only 3.0 compatible device?

---

### Post by trent.josephsen on 2012-12-24
"Basic" is not a modifier that can be sensibly applied to "3d graphics". Much like "fresh raisins" or "C++: The Complete Reference".

---

### Post by Ghostmn on 2012-12-24
> **trent.josephsen said:**
> "Basic" is not a modifier that can be sensibly applied to "3d graphics". Much like "fresh raisins" or "C++: The Complete Reference".

That's not necessarily helpful, and I think you missed the point.

---

### Post by MG&amp;TL on 2012-12-24
> **Ghostmn said:**
> That's not necessarily helpful, and I think you missed the point.

Not helpful, but worth you knowing. There are too many applications and variables for any wrapper to be useful in any one situation. If you drop the spheres requirement, (or I suppose you could emulate them by spinning a texture very fast), I can recommend clutter.

If you're set on 'having it easy', you could use irrlicht: [(tutorials)]("http://irrlicht.sourceforge.net/tutorials/"), to load spheres as models.

As for OpenGL 3.x and hardware requirements, you may be better sticking to 2.x and following these tutorials instead: [http://en.wikibooks.org/wiki/OpenGL_Programming]("http://en.wikibooks.org/wiki/OpenGL_Programming")

---

### Post by Ghostmn on 2012-12-24
> **MG&TL said:**
> Not helpful, but worth you knowing. There are too many applications and variables for any wrapper to be useful in any one situation. If you drop the spheres requirement, (or I suppose you could emulate them by spinning a texture very fast), I can recommend clutter.

If you're set on 'having it easy', you could use irrlicht: [(tutorials)]("http://irrlicht.sourceforge.net/tutorials/"), to load spheres as models.

As for OpenGL 3.x and hardware requirements, you may be better sticking to 2.x and following these tutorials instead: [http://en.wikibooks.org/wiki/OpenGL_Programming](http://en.wikibooks.org/wiki/OpenGL_Programming)

I'm only seeking an easy way simply because I'd rather work on the other parts of the program. Now I have to learn a library, prior to actually working on the most interesting portions of the code base.

Not complaining, but just giving my reasoning for asking for a simpler library. 

Thank you for everyone who has replied.

---

### Post by MG&amp;TL on 2012-12-24
> **Ghostmn said:**
> I'm only seeking an easy way simply because I'd rather work on the other parts of the program. Now I have to learn a library, prior to actually working on the most interesting portions of the code base.

Sorry-it wasn't my intention to presume things-I agree OpenGL is boring. I just meant that there isn't really an easier way. Although do check out irrlicht, in case that works for you. :)

---

### Post by trent.josephsen on 2012-12-24
Someone *could* probably write a 3D graphics library that was simple to use and did just what you want it to do. But in all likelihood you're the only person who would use it, since other people have different requirements than just "draw spheres". There's not much demand for single-purpose DWIM 3D modeling software.

---

### Post by Ghostmn on 2012-12-24
> **trent.josephsen said:**
> Someone *could* probably write a 3D graphics library that was simple to use and did just what you want it to do. But in all likelihood you're the only person who would use it, since other people have different requirements than just "draw spheres". There's not much demand for single-purpose DWIM 3D modeling software.

Well it doesn't have to be a library that does one thing for the programmer. It just needs to be something less overwhelming in general.

---

### Post by trent.josephsen on 2012-12-24
The point I was trying to make is that 3D graphics is a pretty overwhelming topic to begin with. If I were looking for quantum mechanical modeling software, I might find a package with the best user interface ever, but I'd still have to learn some physics just to be able to use it.

---

### Post by Ghostmn on 2012-12-24
> **trent.josephsen said:**
> The point I was trying to make is that 3D graphics is a pretty overwhelming topic to begin with. If I were looking for quantum mechanical modeling software, I might find a package with the best user interface ever, but I'd still have to learn some physics just to be able to use it.

**Complete rewrite**

I get it, I was just wondering if there was something even a bit less overwhelming. I'll be using opengl.

---

### Post by xytron on 2012-12-25
If you just need to draw spheres why not use a ray tracing program such as [Povray]("http://www.povray.org") I think it will be easier for you than to start learning OpenGL, in fact Povray already has a simple sphere object that you can use, and I think you'll be able to do animations faster win Povray than to learn Opengl.

Also Povray supports mathematically defined objects as opposed to working with OpenGL triangles.

---

