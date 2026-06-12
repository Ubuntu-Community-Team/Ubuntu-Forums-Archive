---
title: "good graphical interface"
date: 2012-01-06
forum: Programming Talk
---

### Post by bigrockcrasher on 2012-01-06
I am looking for a good graphical interface using opengl like GLUT that works well with Ubuntu, up to date. I like GLUT, very simple, low level, can do mostly what i want, very stable but it is just to old. I have been doing some research to find a newer toolkit and i find mostly high level languages, not my style. I also noticed GLX but I have not found any tutorials so I am presuming it is not popular. I am looking for some thing that is low level, has features utilizing opengl 4, and popular. I mainly write in c++.  Is there anyone that can assist me.

---

### Post by Simian Man on 2012-01-06
What features do you want?  You say "graphical interface", but GLUT doesn't really have much in the way of interface elements.  If you just need something that will setup a window for you, and perform input, I'd recommend SDL.  It is mature, commonly used, well-designed, and portable.  It also gives you nice bonuses like audio, threads, timers, image loading and networking (when you use the add-on libraries at least).  It's one of the best libraries of any kind I've used.

If you want an actual graphical interface, with buttons, textboxes and so on, then there isn't really a clear-cut answer.  If you can separate your graphical and interface elements, using QT with OpenGL views is a good option.  There is also CEGUI, which I don't especially like, but is effective.  There are others, but I haven't used them before.

I wouldn't recommend GLX at all, as you limit your code to working only on X-Windows for no real benefit.

---

