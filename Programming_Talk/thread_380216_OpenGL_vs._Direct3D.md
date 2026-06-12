---
title: "OpenGL vs. Direct3D"
date: 2007-03-09
forum: Programming Talk
---

### Post by MedivhX on 2007-03-09
Which one is better API? What is each of them better for? What are their advantages/disadvantages?

 Tell me all about them!!! :biggrin: [-o<

---

### Post by duff on 2007-03-09
[http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL](http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL)

---

### Post by MedivhX on 2007-03-09
I've already seen that article:

The neutrality of this article is disputed.

---

### Post by duff on 2007-03-09
You think you aren't going to get a biased answer to that question here?

---

### Post by WW on 2007-03-09
Heh, the neutrality of *everything* should be disputed.  As they say, there is no view from nowhere.

---

### Post by MedivhX on 2007-03-09
> **duff said:**
> You think you aren't going to get a biased answer to that question here?

Well, I probably will LOL, but still I'd like to hear ubuntuforums' peoples opinions. :D

---

### Post by Wybiral on 2007-03-09
They both have similar features... It's not hard to work with either.
But OpenGL isn't stuck in MS world, so I'd say OpenGL is better.

---

### Post by knight17 on 2007-03-09
From what I have heard DirectX is easy.But Microsoft may not open it up

---

### Post by lnostdal on 2007-03-09
> **MedivhX said:**
> Which one is better API? What is each of them better for? What are their advantages/disadvantages?

 Tell me all about them!!! :biggrin: [-o<

bah .. you're kidding; right?

now, why didn't you just ask:

[quote=MedivhX]
Windows vs. Linux: Which one is better OS? What is each of them better for? What are their advantages/disadvantages?

Tell me all about them!!!  :biggrin: [-o<[/QUOTE]

you see; if you really where a programmer you'd have some real question about directx or opengl but you don't and you aren't so you want to somehow "participate" by creating conflict and flamewars  (yes, you really are that bored)

..i instead suggest you go grab a couple of books and resources if you want to get into game/gfx programming:

* The C Programming Language (order it from amazon)
* [http://nehe.gamedev.net/](http://nehe.gamedev.net/)
* [http://www.opengl.org/documentation/red_book/](http://www.opengl.org/documentation/red_book/)
* [http://www.opengl.org/documentation/blue_book/](http://www.opengl.org/documentation/blue_book/)

i've written down how to get started with the very basic practical stuff under Ubuntu (actually; the same setup works under many distros and many OSes, Windows also), here: [http://nostdal.org/~lars/writings/about-c-getting-started-under-ubuntu/](http://nostdal.org/~lars/writings/about-c-getting-started-under-ubuntu/)

..now go away, stop [fishing/trolling]("http://redwing.hutman.net/~mreed/warriorshtm/troller.htm") and come back later when you have a _real question_ about programming, directx or opengl .. you will of course probably find that most people here are more familiar with opengl for obvious reasons

---

### Post by grusifix on 2007-03-11
I think that OpenGL is better. I can't my DX programs compile under Ubuntu. gcc tells me that I'm lacking some libraries.

---

### Post by Wybiral on 2007-03-11
> **grusifix said:**
> I think that OpenGL is better. I can't my DX programs compile under Ubuntu. gcc tells me that I'm lacking some libraries.

Dx and D3d were made specifically for windows.

I really don't think they're that much different and I've programmed with both.

BUT, since OpenGL is super portable (Linux friendly is my main concern) I would certainly go with OpenGL over direct3d any day.

---

### Post by lingnoi on 2007-03-12
OpenGL runs on Linux, Mac, Windows, Xbox, Xbox360, Playstation 2, Playstation 3, Playstation Portable, Nintendo Wii, Gamecube, Nintendo DS and some mobile phones (not as many features in the phone version).

DirectX runs on Windows, Xbox, Xbox 360, any other microsoft products that I forgot to mention.

Although if you write an openGL app it won't compile first time on all the platforms I mentioned its pretty portable compared to the DirectX library.

In this day an age its all about applications. Just like how you wouldn't write a web page that only worked in IE you shouldn't write a program that only works in Windows.

I think everyone has the right to choose their favorite OS and it doesn't make development harder to use a different API. If you are thinking about cross platform development then you should look at a library called libSDL which allows you to write games for Linux, Mac and Windows.

It doesn't really matter which is "better" and to be honest I don't really see the difference as they both tell the graphics cards to draw polygons to the screen, surely its the graphics card that matters since it does all the hard work.

---

### Post by j_g on 2007-03-12
> surely its the graphics card that matters since it does all the hard work.

Well, before anything gets to the hardware, it has to go through a device driver. On a modern OS that supports the concept of user and kernel modes, an application is not allowed to do direct I/O to the hardware. It must use the driver. So, if you have an API and driver that doesn't support a particular card's "hardware accelleration", then you're going to suffer a significant performance hit. It's as if that aspect of the hardware doesn't even exist at all. So, checking the driver support for a given API is very important if hardware performance is of concern.

---

### Post by Wybiral on 2007-03-12
Well, OpenGL is really just an API, there are actually software rendered versions.

MesaGL, for instance, supports software rendering.

SDL also gives you the option of initializing the surface as hardware or software rendered.


OpenGL basically just does all of the annoying stuff like matrix transformations and polygon rasterizing for you.

---

### Post by quakeboy on 2007-03-13
Well I would argue that OpenGL is better. 

Reason. 

1)Performance. It is supported directly by many hardware manufacturers. In fact all Graphics  Card manufacturers support both Direct3D and OpenGL at hardware levels.

Doom 3 was written using OpenGL. Do you want any other reason??

2) Portability. It can be compiled on almost any platform with very very little changes.

3) It is controlled by a common board with members from Intel, NVidia, ATI, Microsoft etc.

4) My Personal programming experience. Its very good and better than Direct3D.

5) But if you are concerned about productivity than all other factors. Then DirectX helps you better with all lot of built in utility classes for camera, matrices etc.

But OpenGL is what I would recommend. Clean Programming model is another reason.

---

### Post by Dullstar on 2009-10-23
I don't know what the differences are, EXCEPT DirectX/Direct3D are purely Microsoft products.  I'd go with OpenGL if you're looking for cross-platform software.  OR even Linux only software.

---

