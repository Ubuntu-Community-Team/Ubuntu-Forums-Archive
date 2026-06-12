---
title: "Problem finding a good 2D graphics library for animations (tried cairomm)"
date: 2009-04-06
forum: Programming Talk
---

### Post by dennis90 on 2009-04-06
Hi!

I am working on a simple 'solar system' simulator program in C++. It uses gtkmm for drawing the UI and I tried to use cairomm for drawing the celestial bodies and animate them but I found that this way it is laggy as hell.

Unfortunately I didn't found much documentation for this library and that's why I am asking for your help.
First I tried creating a separated thread that calculates forces and redraws the objects but the app crashed when the thread tried to draw on the context. (Why?) Then I connected the drawing function to *Glib::signal_idle()*. That way redrawing was OK but it was laggy.

Now I don't really know what to do. To tell the truth I really like cairomm and I would like to use object oriented APIs now. So I ask if you know a solution either by finding an other library or giving me some hints on correcting this code.

Thanks

---

### Post by hessiess on 2009-04-06
If you just want to draw graphcs to a window you could try Quad-Ren (see sig, resolution independent, object oriented, WIP) or SDL (software based(slow), resolution dependent without external libs). Otherwise look into OpenGL.

---

### Post by Firestom on 2009-04-06
For drawing graphics, I suggest Simple Directmedia Layer. The API is very low-level but works fine.

Another alternative would be to use Macromedia Flash. Flash uses it's own Actionscript language and allows to make Vector drawing. It's not compilable, it needs Macromedia Flash installed, but it's very intuitive.

Best Regards!

---

### Post by krazyd on 2009-04-06
I know you're already on gtkmm, but have you considered KGLengine? Some links:

[http://techbase.kde.org/Development/Tutorials/Games/kglengine/kglengine-simpleBox](http://techbase.kde.org/Development/Tutorials/Games/kglengine/kglengine-simpleBox)
[http://techbase.kde.org/Projects/KGLEngine2D](http://techbase.kde.org/Projects/KGLEngine2D)
[http://techbase.kde.org/Development/Tutorials/Games/KGLEngine2d](http://techbase.kde.org/Development/Tutorials/Games/KGLEngine2d)
[http://www.youtube.com/watch?v=dbqhCKxK9o4](http://www.youtube.com/watch?v=dbqhCKxK9o4)

---

### Post by dennis90 on 2009-04-07
Thank you for your answers!

I will take my time and choose the best. I already took a look at those which you've mentioned. KGLengine seems to be really sympathic but it's qt based, isn't it? And I somehow I don't wanna mix qt and gtk stuff. 

By the way how do for example animations in cairo-dock run so smooth? I couldn't find any tutorials about it. And I changed my opinion, I would accept pure cairo in c as well because it has so many features and clean code. (If I found a good tutorial I would definitely stick to cairo.)

---

