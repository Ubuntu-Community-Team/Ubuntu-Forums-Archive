---
title: "OpenGL Running Hot"
date: 2010-09-15
forum: Programming Talk
---

### Post by ChurroLoco on 2010-09-15
I noticed in multiple projects when I make an OpenGL window on my laptop it quickly runs hot even when drawing only a triangle.  I normally would expect this but found that other software that uses OpenGL contexts such as Blender will only make really heat up  if you are continually animating or moving the orientation of the camera with the mouse.

This makes me believe they might not be redrawing the scene if nothing has changed... which leads me to believe that if instead of letting it try to draw as fast as possible, locking the framerate might help it run cooler and use less battery.

Do you think this might help?

Thanks

---

### Post by Simian Man on 2010-09-15
That is exactly the problem.  It is not a big deal for games, because they generally want to render as fast as possible, but for other software - such as Blender - it is.

How are you doing input/windowing?

---

### Post by ChurroLoco on 2010-09-15
I think even in simple game I don't need the framerate past 75fps. I'm really sensitive to frame rate and even I can't notice anything higher than that.  It is definitely worth capping if it going to make my game run better on laptops and help save battery.

> How are you doing input/windowing?

I do windowing a bunch of different ways for different projects. I have noticed this issue in a few different platforms. Straight up X window, FreeGlut, standard MS Windows API (OpenGL & DirectX).  If I'm not using Glut it should be pretty easy to put a timer in the messaging system.  Not sure how easy it is in FreeGlut to cap the framerate.

Maybe I could run the rending on one frame-capped thread and do other logic (Game Stuff?) on another thread.  I'm sure lots of people do that... And I'm sure its not as easy as it sounds.

Thanks for your help.  You gave me some food for thought.
:D

---

### Post by kahumba on 2010-09-15
OpenGL itself has nothing to do with your issue, I'm pretty sure the app/the developer is to blame, i.e. it probably keeps animating when it shouldn't and/or doesn't care about using less frame rates or none in special cases for example when the window is minimized.
For instance a while ago I read a forum thread about a guy developing in SDL (thus OpenGL) claiming his hw is working like crazy even when doing a very simple animation, later he was told that he forgot to write the code that adjusts the framerate hence SDL kept rendering as many frames as possible by default.

---

### Post by ChurroLoco on 2010-09-16
> OpenGL itself has nothing to do with your issue, I'm pretty sure the app/the developer is to blame

Oh yes, I never meant to imply that OpenGL was the cause of the heat.  I was just curious as to how to use OpenGL without the heat problems.  If OpenGL is rendering at 1200fps per second I'm sure it's doing more work than it needs to. ;)

I haven't done any tests yet, but it makes sense that capping the framerate should do the trick.  I wonder if it will fix the problem of my GeForce 8800 squeeling when there is nothing to draw.  The funny thing is as you add more complexity to a scene you will notice the squeeling get lower pitch till you can't here it.  Must be a funny EE quirk.

---

