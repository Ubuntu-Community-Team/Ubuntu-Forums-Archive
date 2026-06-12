---
title: "OpenGL Statistics ( e.g Vertex Count )"
date: 2008-06-02
forum: Programming Talk
---

### Post by Xyem on 2008-06-02
Pretty simple question I hope.

Does OpenGL ( or GLUT? ) provide any way to get statistics? Such as vertex/face count? It is mainly just for curiosity, so I can see how 'complex' my scene is. I can't find anything with the obvious keywords.

I'm using the OpenGL module for Perl, if it matters.

Thanks

---

### Post by skullmunky on 2008-06-03
maybe search for profiling ... ?

if you're doing just raw opengl you'd probably know the vertex count, b/c it's just how many times you call glVertex() :)  

are you loading objects or something?

is that before or after view frustum culling?

---

### Post by Xyem on 2008-06-03
Hadn't thought of profiling but nothing seems to come up ( that I am looking for ).

I'm looking to display the vertex/polygon count in the corner ( like I have with the frame rate ) and I just thought that OpenGL would know this..

I'm not loading objects now, but I will in future. Display lists would also cause an issue if I did a count "manually"..

It's not a big deal if I can't do it, as I said, it is only for my curiosity.

---

### Post by geirha on 2008-06-03
If there were any such thing, it would probably have been mentioned [here](http://www.opengl.org/resources/faq/technical/performance.htm), though it has some pointers on making some simple ones yourself.

---

### Post by Sockerdrickan on 2008-06-03
You have your vertices and stuff in vectors and just get foo.size()

---

### Post by Xyem on 2008-06-03
> **Tux0r said:**
> You have your vertices and stuff in vectors and just get foo.size()

Does OpenGL/GLUT provide 'foo'?

---

### Post by Sockerdrickan on 2008-06-03
No you load data from model files into your own vectors

---

### Post by Xyem on 2008-06-03
Then that is manually counting.. and will be rather inaccurate ( or has the possibility of being at least ).

I'm somewhat surprised OpenGL won't tell you how many glVertex ( or similar if display lists etc do differently ) calls it has done.. then again, it is for drawing and that is what it does.

---

### Post by Sockerdrickan on 2008-06-03
It will not be inaccurate... how would an int be inaccurate if it reports nVertices

also, please don't use glVertex

---

### Post by Xyem on 2008-06-03
It *may* be inaccurate because it relies on me recording a count of vertices for anything I draw regardless of how it is drawn ( i.e. manually, display lists, any other way of drawing something [ I'm quite new to OpenGL/GLUT etc. ] ).

And how do I not use glVertex? There is another way to tell OpenGL where the vertices of a polygon/triangle/etc. are?

---

### Post by stroyan on 2008-06-03
OpenGL implementations are more focused on fast rendering instead of
spending precious time on keeping statistics.

You might prefer to use a wrapper library that intercepts OpenGL calls.
Have a look at [http://www.opengl.org/sdk/tools/BuGLe/](http://www.opengl.org/sdk/tools/BuGLe/) .

You could also consider using the OpenGL feedback buffer approach.
That will fill in a buffer area with coordinate data for primitives
that get past the clipping stages.  See the reference pages for
glFeedBackBuffer and glRenderMode.  It will require an extra pass over
a frame to count the primitives.  But it could tell how many vertices
were rendered in the harder cases such as display lists or gluNurbsSurface.

---

### Post by rnodal on 2008-07-09
> **Xyem said:**
> 

And how do I not use glVertex? There is another way to tell OpenGL where the vertices of a polygon/triangle/etc. are?

Maybe the suggestion is to not use OpenGL intermediate mode which is very slow when things get more complex. That's the only reason that I can come up with.


-r

---

### Post by Xyem on 2008-07-14
> OpenGL intermediate mode

I have no idea what that is, I've never heard of it ( or that there were different modes )

---

### Post by rnodal on 2008-07-14
OpenGL intermediate mode is when you call glDraw, glVertex etc every time you want to draw something. That way of doing things is not efficient. Graphic cards like to tortured :), they want you to send them a bunch of data all at once instead of sending little data a bunch of time. If you are just learning OpenGL do not worry about it now. Once you have things working then worry about making them fast.

---

### Post by Xyem on 2008-07-14
Oh, do you mean like display lists, VBO, FBO etc?

---

### Post by rnodal on 2008-07-14
> **Xyem said:**
> Oh, do you mean like display lists, VBO, FBO etc?

Yea that is the way to go. Code using intermediate mode and rendering something like, I don't know, 500 polygons or any shape I think will be very slow. Don't quote me on that since I have never really done any benchmarking.

---

### Post by Xyem on 2008-07-14
I see. Well at the moment, as you seem to have figured, I am just starting to learn OpenGL ( and game programming in general ) so I am taking the simplest route right now.

I will look into VBO's and FBO's when I actually get my game to work :)

Thanks for all the input, much appreciated!

---

### Post by rnodal on 2008-07-14
That is a good idea. I'm not a OpenGL expert by any means. As a matter of fact I also recently started doing OpenGL. I'm working in my senior project and I decided to do an 2D Game Engine using OpenGL/SDL/C++. I also made the mistake of thinking that intermediate mode was the only way to go. Good luck in whatever you decide to do and take advantage of the forums. Really nice people live in these forums.

---

### Post by Xyem on 2008-07-14
> take advantage of the forums. Really nice people live in these forums. 
Hear hear :)

---

