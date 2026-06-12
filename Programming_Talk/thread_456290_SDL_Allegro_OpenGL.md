---
title: "SDL? Allegro? OpenGL?"
date: 2007-05-27
forum: Programming Talk
---

### Post by ankursethi on 2007-05-27
I just took a look at SDL and Allegro. Since I haven't ever dabbled into game programming, I don't quite understand what "OpenGL support" means. Allegro and SDL both seem to support OpenGL, but isn't OpenGL itself a 3D API? Are these two wrappers around OpenGL or what? What should a newbie learn, OpenGL or Allegro, if he wants to take a step towards  game programming?

PS : this is just a general question concerning both 3D and 2D programming. I think I'll begin with 2D and then move on to 3D.

---

### Post by Mickeysofine1972 on 2007-05-27
Take a look at the Ubuntu Games Developers Wiki at:

[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)

Mike

---

### Post by ankursethi on 2007-05-28
Those are tutorials. I was looking for some suggestions. Anyway, if I create a 2D game in, say, SDL, can I have 3D graphics in the same game as well? Like 3D on a 2D background?

It's just that I have an idea and I want to make sure I can implement that before I start. I'll probaly be using SDL because the game wiki has some nice tutorials on that.

---

### Post by Cows on 2007-05-28
I programmed in both SDL and Allegro. Never in OpenGL but I would say OpenGL is much better in supporting multi-platforms then DirectX. SDL is much harder but much better then Allegro since you actually control every aspect of your program.

---

### Post by ankursethi on 2007-05-28
I have never even thought of using anything other than OpenGL for 3D, but what I wanted to know was what OpenGL support in SDL means. Is it some kind of wrapper around the original API? And the other question - whether I can do 2D and 3D in the same application.

---

### Post by slavik on 2007-05-28
when it is said that SDL supports OpenGL, it means that you can use SDL as a wrapper around some OpenGL functions.

for example: OpenGL does not have a way of obtaining a window (or input management), this was why GLUT was created. SDL gives you more control than GLUT (at more code having to write yourself). In a nutshell, SDL can create a window with OpenGL context so that you can use OpenGL there. SDL (I am not really sure about this) allows you to create multiple windows, all with OpenGL context, so you could have something like GIMP but all with OpenGL.

Also, some calls to some OpenGL functions change (ones to do with setting some attributes to the state machine).

---

