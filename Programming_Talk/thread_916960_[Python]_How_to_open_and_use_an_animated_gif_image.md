---
title: "[Python] How to open and use an animated gif image?"
date: 2008-09-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-11
Ok, I am making a platformer, with python + pygame. 

I made this awesome animation with gimp:[img]http://img162.imageshack.us/img162/419/stkmanbg1.gif[/img]

So how can I load all the frames in separate surfaces with pygame?

And that animations has alpha values too.

---

### Post by cb951303 on 2008-09-11
I highly recommend some sort of [sprite]("http://en.wikipedia.org/wiki/Sprite_(computer_graphics)") class for your game (I don't know if pygame has it already).

---

### Post by crazyfuturamanoob on 2008-09-11
> **cb951303 said:**
> I highly recommend some sort of [sprite]("http://en.wikipedia.org/wiki/Sprite_(computer_graphics)") class for your game (I don't know if pygame has it already).
Here is also some instructions for opening animated gifs, but I don't get it.
[http://www.pythonware.com/library/pil/handbook/format-gif.htm](http://www.pythonware.com/library/pil/handbook/format-gif.htm)
How can I use the images? Where are the surfaces of each subimage?? 
Could someone make me a pygame example, with my animation, that how can you use animated gifs?

---

### Post by cb951303 on 2008-09-11
I don't know anything about pygame but in SDL(which is on what pygame is based) if you load a gif image it only loads the first frame. That's why you should use sprites for your animation. That's the standard way of doing 2d animations in games not gifs.

---

### Post by pmasiar on 2008-09-11
My amazing google-foo skills, by searching pygame + sprite 8-) suggests to read:
[http://www.pygame.org/docs/tut/SpriteIntro.html](http://www.pygame.org/docs/tut/SpriteIntro.html)

---

### Post by amdlintuxos on 2010-02-06
Hi, i know it's to late, but probably this will help to others, like it helped me yesterday. Example with explanation are here.
[http://shinylittlething.com/2009/07/22/pygame-and-animated-sprites-take-2/](http://shinylittlething.com/2009/07/22/pygame-and-animated-sprites-take-2/)

---

