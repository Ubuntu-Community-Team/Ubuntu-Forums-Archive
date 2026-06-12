---
title: "OpenGL and python"
date: 2009-05-24
forum: Programming Talk
---

### Post by elbarto_87 on 2009-05-24
Hi,

Has anybody found any good (basic for beginner) tutorials for pyOpenGL ? I have searched but haven't found much. I managed to find an example in C, but not having any knowledge of the language makes learning by example difficult in that case.

Regards Elbarto

---

### Post by unutbu on 2009-05-24
This is not exactly what you asked for, but I often find having example code a useful addition to documentation. Here is some code you might find useful: [http://ubuntuforums.org/showthread.php?p=6536131#post6536131](http://ubuntuforums.org/showthread.php?p=6536131#post6536131)

---

### Post by elbarto_87 on 2009-05-25
Thanks for the link,

I will keep looking around to see what I can find. Is openGL as good as any graphics library to start out with in python?

Thanks, Elbarto

---

### Post by unutbu on 2009-05-25
I don't know that much about graphics programming, so perhaps I'm not the right person to answer this question. 

My inexpert impression is that openGL allows one to do shading and 3D effects like rotation of surfaces. If you want to do 2D drawing, I think python-cairo might be easier to use. Your Ubuntu probably has python-cairo already installed, and there are a few examples of things you can do with it at /usr/share/doc/python-cairo/examples/. (See also [http://zetcode.com/tutorials/pygtktutorial/snake/](http://zetcode.com/tutorials/pygtktutorial/snake/).)

If you want to blit sprites to a window, you can do that with pygame ([http://www.pygame.org/docs/](http://www.pygame.org/docs/)).

I think there are also some basic drawing facilities built into pygtk ([http://www.pygtk.org/pygtk2reference/index.html](http://www.pygtk.org/pygtk2reference/index.html)).

---

