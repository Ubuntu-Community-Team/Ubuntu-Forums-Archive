---
title: "Need a very fast cross-platform graphics toolkit"
date: 2009-07-30
forum: Programming Talk
---

### Post by Volt9000 on 2009-07-30
I'm starting a new project, written in C++, that will require rendering some simple, 2D graphics. But I need this to be FAST, since I may be potentially rendering large graphical canvases with lots of elements.

What's a nice, FAST, cross-platform graphics toolkit that will allow me to do this? I was considering using wxWidgets, but thought about Qt as well.

Any thoughts?

[Edit]
I should note this will NOT be purely a graphics rendering app-- it will be a "regular" Linux/Windows app with a window in it that will do the rendering.

---

### Post by JordyD on 2009-07-30
> **Volt9000 said:**
> I'm starting a new project, written in C++, that will require rendering some simple, 2D graphics. But I need this to be FAST, since I may be potentially rendering large graphical canvases with lots of elements.

What's a nice, FAST, cross-platform graphics toolkit that will allow me to do this? I was considering using wxWidgets, but thought about Qt as well.

Any thoughts?

[Edit]
I should note this will NOT be purely a graphics rendering app-- it will be a "regular" Linux/Windows app with a window in it that will do the rendering.

Does the whole rendering have to be super-fast? If you only need a specific part to be super-fast, you can write it in something like SFML or SDL and use it in conjunction with Qt or wxWidgets, on a separate thread.

By the way, both SDL and SFML are cross-platform. They are not for displaying normal widgets, they are for drawing things like sprites and shapes, animating them, etc. They are often used for games, but they're made to be more general so that they can be used for many multi-media kinds of things. SFML also has a tutorial for embedding SFML in Qt apps at [sfml-dev.org]("http://www.sfml-dev.org/").

I hear that SFML is faster than SDL, but I have no idea how true that is. As for APIs, SFML is object-oriented and SDL not.

---

### Post by monraaf on 2009-07-30
> **JordyD said:**
> Does the whole rendering have to be super-fast? If you only need a specific part to be super-fast, you can write it in something like SFML or SDL and use it in conjunction with Qt or wxWidgets, on a separate thread.

By the way, both SDL and SFML are cross-platform. They are not for displaying normal widgets, they are for drawing things like sprites and shapes, animating them, etc. They are often used for games, but they're made to be more general so that they can be used for many multi-media kinds of things. SFML also has a tutorial for embedding SFML in Qt apps at [sfml-dev.org]("http://www.sfml-dev.org/").

I hear that SFML is faster than SDL, but I have no idea how true that is. As for APIs, SFML is object-oriented and SDL not.

Well I agree with most part, but I've never heard of sfml before so I don't know about that. Looking in synaptic it appears that not one application in the repositories makes use of sfml. There are tons of applications that use SDL, the sml wiki lists only 4 applications that use sfml. I'm curious if it's faster than SDL then why is nobody using it?

---

### Post by Volt9000 on 2009-07-30
No the whole thing doesn't have to be superfast.
In fact the graphics rendering *shouldn't* be that intense.

The thing is, there's a Windows app that I'm trying to re-rewrite. At the moment it's written in MFC, and it's quite slow. I've started rewriting it in C#, but I found out soon enough that C# can be even slower.

All I'm doing is rendering a large number of individual pixels. I considered something like SDL or FLTK, but I'm not sure how well they will integrate. All I need to do is ensure the contents of only one window render quickly. The rest of the app is just straight widgets.

---

### Post by monraaf on 2009-07-30
> **Volt9000 said:**
> No the whole thing doesn't have to be superfast.
In fact the graphics rendering *shouldn't* be that intense.

The thing is, there's a Windows app that I'm trying to re-rewrite. At the moment it's written in MFC, and it's quite slow. I've started rewriting it in C#, but I found out soon enough that C# can be even slower.

All I'm doing is rendering a large number of individual pixels. I considered something like SDL or FLTK, but I'm not sure how well they will integrate. All I need to do is ensure the contents of only one window render quickly. The rest of the app is just straight widgets.

Yes but are these pixels moving or not? If they are just static I suppose any canvas widget will do.

---

### Post by JordyD on 2009-07-30
> **monraaf said:**
> Well I agree with most part, but I've never heard of sfml before so I don't know about that. Looking in synaptic it appears that not one application in the repositories makes use of sfml. There are tons of applications that use SDL, the sml wiki lists only 4 applications that use sfml. I'm curious if it's faster than SDL then why is nobody using it?

Linux is faster than Windows, why does nobody use it?

Your argument is pointless.

SFML has less coverage, but better (IMO) documentation and tutorials that are provided by the actual developers, not users.

SFML is in C++, not C, which I think is a wonderful advantage because it means it integrates more nicely with object-oriented code.

Regardless, they're both nice libraries. It doesn't matter what you use.

---

### Post by JordyD on 2009-07-30
> **Volt9000 said:**
> No the whole thing doesn't have to be superfast.
In fact the graphics rendering *shouldn't* be that intense.

The thing is, there's a Windows app that I'm trying to re-rewrite. At the moment it's written in MFC, and it's quite slow. I've started rewriting it in C#, but I found out soon enough that C# can be even slower.

All I'm doing is rendering a large number of individual pixels. I considered something like SDL or FLTK, but I'm not sure how well they will integrate. All I need to do is ensure the contents of only one window render quickly. The rest of the app is just straight widgets.

SFML integrates with X, Qt, Win32, and wxWidgets (as in it has tutorials for it, they're at the website).

I don't know what SDL integrates with, but it's *probably* (guessing here) similar.

---

### Post by monraaf on 2009-07-30
> **JordyD said:**
> Linux is faster than Windows, why does nobody use it?

Your argument is pointless.

SFML has less coverage, but better (IMO) documentation and tutorials that are provided by the actual developers, not users.

SFML is in C++, not C, which I think is a wonderful advantage because it means it integrates more nicely with object-oriented code.

Regardless, they're both nice libraries. It doesn't matter what you use.

Well, I was just curious why you are plugging a library that AFAICS nobody uses.

---

### Post by JordyD on 2009-07-30
> **monraaf said:**
> Well, I was just curious why you are plugging a library that AFAICS nobody uses.

I use it. I prefer it over SDL, which I've also used. Like I said, it doesn't matter what he picks, they're both good.

Plus, SFML's documentation is complete, and makes it easy to learn/use.

---

### Post by Volt9000 on 2009-07-31
Thanks for the info, guys! SFML sounds like a good choice, I'm gonna check it out.

---

### Post by Sockerdrickan on 2009-07-31
SDL blitting is painfully slow compared to OpenGL rendering obviously.

---

### Post by ZuLuuuuuu on 2009-07-31
I'm in a similar situation where I need to show a few thousand simple shapes (they will move because the canvas should be smoothly scaled, zoomed etc.). I'm currently thinking of using simple drawing capabilities of wxWidgets as it has been told to me that I can achieve this kind of thing via using double buffered "device contexts" as is named in wxWidgets. There is also a widget called wxGLCanvas if I need uber-fast canvas, though I don't have time to learn OpenGL right now, so I will use the first solution.

So far my experience is that wxWidgets has unfortunately pretty poor documentation compared to Qt or even GTK+. There is only 1 book and it is more like a reference manual instead of a step-by-step like approach. There are a lot of sample code though. The community usually encourages you to learn from sample codes which I don't like much because I'm a book/tutorial kind of guy. The IRC channel is not "that" active but active enough to usually get answers in 4-10 minutes.

Here is a beautiful and relatively short tutorial if you are curious about wxWidgets:

[http://zetcode.com/tutorials/wxwidgetstutorial](http://zetcode.com/tutorials/wxwidgetstutorial)

Especially "Device Contexts" topic will interest you as it shows how to "draw" things.

Please write what was it like to use -the solution you choose here- so that I can also think about using it accordingly for my project if needed :)

---

### Post by Volt9000 on 2009-07-31
Thanks for the tutorial link, ZuLuuuuuu!

I too found the documentation quite lacking, which is why I was a bit hesitant to use it.

Nice to know about wxGLCanvas, though-- with it I might be able to avoid using a separate library for the rendering part.

---

### Post by slavik on 2009-07-31
> **Volt9000 said:**
> I'm starting a new project, written in C++, that will require rendering some simple, 2D graphics. But I need this to be FAST, since I may be potentially rendering large graphical canvases with lots of elements.

What's a nice, FAST, cross-platform graphics toolkit that will allow me to do this? I was considering using wxWidgets, but thought about Qt as well.

Any thoughts?

[Edit]
I should note this will NOT be purely a graphics rendering app-- it will be a "regular" Linux/Windows app with a window in it that will do the rendering.
OpenGL

---

### Post by skullmunky on 2009-08-01
opengl is probably going to be the fastest; other fast options will probably at some level use opengl anyway, so you could just go with that in the first place.

I think it also does depend on other things about the project - whether you're moving a lot of polygons around, or moving a lot of sprites, or just drawing a lot of stuff fresh each frame (like for example an audio visualizer).  

If you also have a large canvas, which you need to scroll around in, Qt claims to be well designed for that...

---

