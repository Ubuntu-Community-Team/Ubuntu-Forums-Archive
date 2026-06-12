---
title: "openGL, SDL or what??"
date: 2007-01-11
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-11
If someone wanted to get into 3D programming with C++, which is the best thing to use and what are the qualities of each?
-openGL
-SDL
-glut
I have no idea what each of thier qualities are, I just know they exist.
Thanks in advance.

---

### Post by Lord Illidan on 2007-01-11
Try using Wikipedia to search for them.

Basically, you can control them all with SDL, as SDL is like a gigantic framework which can control sound, 3D graphics and more.

---

### Post by Ben Sprinkle on 2007-01-11
So SDL is like the linux directx? COOL!

---

### Post by Wybiral on 2007-01-11
Yeah, SDL is like directX and OpenGL is like direct3d... They work together nicely. OpenGL is better than direct3d, IMO, but... SDL+OpenGL is almost always the way to go for 3d in linux.

---

### Post by Ben Sprinkle on 2007-01-11
Is opengl better for that graphics part or sdl? And what's this glut crap?

---

### Post by Lord Illidan on 2007-01-11
> **Goat Spirit said:**
> Is opengl better for that graphics part or sdl? And what's this glut crap?

Since you refuse to search the wikipedia...

[http://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit](http://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit)

[http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer](http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer)

Now, SDL has been used for games like Quake 4 and UT2004 (in their Linux implementations, so it is an linux game standard, just like Direct X.

---

### Post by tpg on 2007-01-11
> **Goat Spirit said:**
> If someone wanted to get into 3D programming with C++, which is the best thing to use and what are the qualities of each?
-openGL
-SDL
-glut
I have no idea what each of thier qualities are, I just know they exist.
Thanks in advance.

OpenGL is used for all the 3D drawing operations. However, in order to use OpenGL, you need to first create a window for it to draw to. The simples way of doing this is to use a framework, such as GLUT or SDL. GLUT is specifically for creating windows for OpenGL, and doesn't do much else. SDL contains its own (2D) drawing functions, and is often used on its own, however you can use its sound and input libraries etc. and use OpenGL for drawing. The [Ubuntu Gamedev]("http://ubuntu-gamedev.wikispaces.com/") has a few tutorials on SDL / OpenGL to get you started. For learning OpenGL, see the [NeHe]("http://nehe.gamedev.net/") tutorials.

---

### Post by Wybiral on 2007-01-11
Well, GLUT does SOME stuff, like text in OpenGL (which SDL does not) and things like pre built models (sphere, teapot, etc...) and it handles key/mouse motion.

But, with GLUT you give it a reference to all of the functions (main loop, key catch, mouse, ...etc) and it takes control and calls them itself.

With SDL, it never takes control, so you do all the calling... This makes SDL more versatile and easier to integrate into pre-existing programs (you don't have to redo everything to work with GLUT calling everything)

In my opinion, GLUT does great for small stuff, like demos and such...

But SDL is the way to go when you want to start a full fledged program.

---

### Post by tpg on 2007-01-11
> **Wybiral said:**
> In my opinion, GLUT does great for small stuff, like demos and such...
I agree. The only problem I've had with GLUT that's put me off is that it can't seem to handle fullscreen properly - the window never seems covers up the Gnome toolbars, although I can't think of an example right now (I haven't used GLUT for ages)!

---

### Post by Ben Sprinkle on 2007-01-12
Thanks all. Illidan, I can't use wiki because it's blocked at my school lol. ;)

---

### Post by Lord Illidan on 2007-01-12
> **Goat Spirit said:**
> Thanks all. Illidan, I can't use wiki because it's blocked at my school lol. ;)

Oh sorry for that. Why the hell is it blocked, though? I hate this damn censorship, we had a case at school, too.

---

### Post by Ben Sprinkle on 2007-01-12
> **Lord Illidan said:**
> Oh sorry for that. Why the hell is it blocked, though? I hate this damn censorship, we had a case at school, too.

It used to not be for the first month or so of school, it's blocked for 'talking sites', I guess because you can edit articles, how gay.

---

### Post by Lord Illidan on 2007-01-12
> **Goat Spirit said:**
> It used to not be for the first month or so of school, it's blocked for 'talking sites', I guess because you can edit articles, how gay.

That sucks mate. Why don't you talk to the admins. The wikipedia **should not **be blocked especially when it is an educational site!!

---

### Post by Ben Sprinkle on 2007-01-12
That's what me and my teacher said. Unfortunatly only teachers can request site validations, teachers have alot of work and are not going to waste thier time. :(

---

### Post by cybrid on 2007-01-27
> **Goat Spirit said:**
> That's what me and my teacher said. Unfortunatly only teachers can request site validations, teachers have alot of work and are not going to waste thier time. :(

That's absurd, wikipedia is like having the biggest encyclopedia in the whorld without spending a a ton of $$$ in a ton of books and without having to spend 20 mins seaching for a certain topic. Have your teachers gone nutts or what?.

Full access to knowledge should never be forbbiden.

---

