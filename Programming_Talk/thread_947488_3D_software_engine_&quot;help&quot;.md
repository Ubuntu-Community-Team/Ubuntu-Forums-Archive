---
title: "3D software engine &quot;help&quot;"
date: 2008-10-14
forum: Programming Talk
---

### Post by Ferrat on 2008-10-14
Well just for fun I would like to try and create a simple software based 3D engine, I've done a little OpenGL programming and got a "basic" understanding of how 3D engines work but this seems more fun to learn really. 
I'm not out to make a stunning graphics mega complex one with the super shaders etc just a very basic one and take it from there, been looking at the code for Id's software engines but looking for more examples and possible solutions and was wondering if anyone could give any good examples that I could look at. 

I know this might be out of my current expertise but still would be fun to see what I could possibly do, so any help on what to look at and any hints would be welcome :)

---

### Post by theirishfozz on 2008-10-14
I've been down that road. I dont think it's worth creating a 3d engine personally. There are so many good ones out there. Ogre, Jmonkey etc. 

First of all, like with any engine, you need your render and update loops. You need timing control to make sure that they only run up to a certain fps so it doesnt burn out your computer, and vice versa if they're runninga little slow make it skip a render.

Next up you need to set up your list of "objects". Make a generic object class which you can later extend with position, orientation, velocity, (possibly acceleration), and angular rate (possibly angular acceleration too). 

In your update function you have to update position, orientation etc, simple enough.

Then things get tricky. In the render function you need to build a tree of all your objects to work out which are invisible (clipping) as they are off camera and which are invisible because they are obscured. You also need to clip triangles not visible (back face clipping). This is probably the hardest part and most costly.

Another tricky part is perspective. An easy way to begin could be to build a wireframe engine. Then its just a matter of drawing lines at different lengths and widths based on position and distance from the camera. Start by just setting up a drawLine function to draw a line between two points and that should provide a basis for you to draw your objects recursively. Then you need to pick the two points out of 3d space, work out each objects position based on the position and focal length of the camera (perspective equations). Then a start would be to simply draw a line between the two positions on your screen. This will give poor depthperception though. The next step is to work out each points distance from the camera and reduce the line width accordingly. At a certain point it will be impossible to reduce the line width any further so try just blending it with black. Lines that are not perpendicular to the camera will have the line width change along the line which means each line will have to be drawn pixel by pixel. 

This is as good a reason as any to use an existing 3d engine. 

If you intend to do this I suggest you get hold of "Tricksof the 3d game programming gurus: Advanced graphics and 3d rasterization".

---

### Post by Ferrat on 2008-10-14
Well the point isn't really to make a game or anything of it, just want to give it a go :) if I took a finished 3D engine that would defeat the point of why I'm doing this ^^ 

Yeah I got the basic outlines of what is needed just want to see some more solutions and get inspiration (so to speak) of a software based one, I like the idea of a less fixed engine, it might be more work since you need to create everything from scratch in another way compaired to DX3D and OpenGL but that's also the fun :)

---

