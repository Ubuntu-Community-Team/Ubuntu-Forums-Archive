---
title: "Game Maker for Linux"
date: 2010-10-03
forum: Programming Talk
---

### Post by &gt;reflex&lt; on 2010-10-03
I'm a programmer that develops games, game engines, and tools for making games. I'm currently developing a cross platform game creator to develop rpg tactics styled games. I've been programming it for a year now, and using the QT framework. Soon I plan on porting it to linux, which requires me to recompile 3rd party libraries. I was wondering if there is a need for Game Makers in Linux, and if it's worth it to develop a more general purpose game maker in the future for this platform. Are developers interested in it, or do you have your preferred game maker that you would rather use?

---

### Post by nvteighen on 2010-10-03
There was a clone mantained by a former member of these forums. It was called "Game Baker", written in Python... The code is available, but I'm not sure what happened with that project: [http://code.google.com/p/game-baker/](http://code.google.com/p/game-baker/)

---

### Post by Somelauw on 2010-10-03
> **>reflex< said:**
> I'm a programmer that develops games, game engines, and tools for making games. I'm currently developing a cross platform game creator to develop rpg tactics styled games. I've been programming it for a year now, and using the QT framework. Soon I plan on porting it to linux, which requires me to recompile 3rd party libraries. I was wondering if there is a need for Game Makers in Linux, and if it's worth it to develop a more general purpose game maker in the future for this platform. Are developers interested in it, or do you have your preferred game maker that you would rather use?

I would be interested since I like games.
I tried gamemaker(yoyogames.com) on windows, but if lacked too much features and only works for windows.
I have been tinkering about making my own gamemaker once, but never got enough time to start creating it.

---

### Post by &gt;reflex&lt; on 2010-10-04
> **Somelauw said:**
> I would be interested since I like games.
I tried gamemaker(yoyogames.com) on windows, but if lacked too much features and only works for windows.
I have been tinkering about making my own gamemaker once, but never got enough time to start creating it.

If you have the technical skills then I'm sure you can contribute. First you have to be fluent in c++, and here is a list of 3rd party libraries I use, excluding the qt framework modules.

// image loading
managed by the qt framework, otherwise freeimage

// input management
ois

// ois dependencies windows specific
dxguid dinput8

// rendering
 opengl32 glu32

// font loading
 freetype

// compression
 libz

// audio & video decoding
 avcodec avformat

// audio
openal

---

