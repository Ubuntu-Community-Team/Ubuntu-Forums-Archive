---
title: "Media programming"
date: 2009-11-19
forum: Programming Talk
---

### Post by hyperdrinky on 2009-11-19
Hi Guys/Girls,

I'm hoping some of you can offer some advice. I am creating an applications and am looking to add support for playing MP3s and AVIs. I have researched a few different options but am having difficulties deciding which one to use. I am programming using C and OpenGL.

Originally I saw this [ffmpeg/SDL]("http://www.dranger.com/ffmpeg/tutorial01.htm") tutorial but it seems so old that the examples contain code which has been deprecated. I have also been taking a look at the [NeHe AVI]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=35") example but cannot seem to get avifile installed correctly.

Has anyone had any experience with programming an AVI or MP3 player? What API is used and are there any resources/demos?

Thanks in advance

hyperdrinky

---

### Post by denago on 2009-11-19
[irrklang](http://www.ambiera.com/irrklang/)
[fmod](http://www.fmod.org/)
[openal](http://connect.creativelabs.com/openal/default.aspx)
[audiere](http://audiere.sourceforge.net/)

Of those, I've used irrklang a bit and it's farily easy to pick up.  The others are fairly popular as well.

---

### Post by tbastian on 2009-11-19
Assuming you're programming for use on a linux system, gstreamer seems to be a fairly standard library for playing said formats. Don't take my word for it however, I've never actually done any work with it.

---

### Post by hyperdrinky on 2009-11-20
Thanks for the quick responses people. I'll give these a try and see how it goes.

Hyperdrinky

---

