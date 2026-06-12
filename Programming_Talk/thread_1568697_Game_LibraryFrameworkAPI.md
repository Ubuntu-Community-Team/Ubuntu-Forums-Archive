---
title: "Game Library/Framework/API"
date: 2010-09-05
forum: Programming Talk
---

### Post by qalimas on 2010-09-05
I'm looking for something that I can't seem to find anywhere.

If anyone knows of a project (preferably open source) that meets these specifications, please post and let me know.


* Uses Python
* Is a game engine (handles audio, video, etc)
* 2D
* Built-in networking library is a plus
* Easy to use API
* Object Oriented
* Supports Linux/Mac (Windows is a plus, but I don't care that much)

For example, if I want to draw a rectangle on the screen with some text, a statement like this would be ideal:```
rectangle = Rect(posX, posY, width, length)
rectangle.text = "hello, this is a new rectangle"
```

I've tried PyGame (wouldn't work on my Mac for the life of me) and Pyglet (wouldn't work on the Mac, fails to load quicktime framework which seems like a very common problem wit no solution for 10.6.4).

---

### Post by phrostbyte on 2010-09-05
Panda3D might be worth looking at, even though it is "3D" :), it probably supports 2D just as well.

---

