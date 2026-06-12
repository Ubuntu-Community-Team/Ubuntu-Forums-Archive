---
title: "Retro Game to 3D... Phase 2..."
date: 2006-12-27
forum: Programming Talk
---

### Post by tocleora on 2006-12-27
Ok, so I got SDL working, can compile stuff with g++, I'm assuming I got OpenGL working cause I can create the rotating cube and it looks great.  What I need now are some very easy to follow instructions on how to take this to a FPS game.  Would like to actually learn the language, not copy and paste everything, but it seems all the instructions I've found only show you parts of what to do.  I'd like to find instructions online that walk you through everything, from the typical "hello world" (or equivalent) to (obviously) the FPS level I want to be.  Anyone know where I can find these instructions?  Thanks in advance!

---

### Post by Wybiral on 2006-12-27
Well, first I would suggest learning to load and render levels and models. The simplest type of FPS to make are the parallel cube style of levels (like in wolf3d and doom)... The graphics will look a lot better than those because it isn't raycasted, but the level loading and collision is very simple. The simplest type of model to load is the wavefront ".obj" model, it's usually just raw vertex and face information.

But... You may take the route of making a game from a pre-built engine. In that case, ogre and crystal source might be work looking into.

---

### Post by tocleora on 2006-12-27
Yes, wolf3d and doom are perfectly fine, I'm not expecting to sell this or anything, it's just something I've wanted to do.  This game is very popular and just the first scene of the game is very well known, I have this vision of starting the game in that scene in 3d, like you would see it in real life.  I know that sounds corny, but once I get a little further into it I'll post what I'm working on and hopefully people will understand. :)  I should mention this game takes place outside for the most part.  Will this cause problems since both wolf3d and doom seemed to be indoors for the most part?

I'll look into "wavefront ".obj" model,".  Thanks!

---

### Post by Mickeysofine1972 on 2006-12-27
You might find what your looking for on The Ubuntu Games Developer Resource Wiki

heres the link:
[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Mike

---

### Post by Wybiral on 2006-12-27
> Will this cause problems since both wolf3d and doom seemed to be indoors for the most part?

Not at all... Outside stuff is actually really easy, it just requires a terrain. Terrain rendering and collision is actually just as easy as cube-based collision and would be very easy to integrate into the cube engine (most likely as a tile object-type).

Basically, the simplest kind of engine will be set up like this...

The levels will be stored in a grid, the grid will contain a value for each unit cube in the level, as an example, this is kindof what a 3x3x3 cubical level would look like...

```

3 3 3

1 1 1
1 2 2
1 2 2

0 0 0
0 3 3
0 3 3

0 0 0
0 0 0
0 0 3

```

First, you can denote the dimensions of the level that the file is about to describe (3x3x3), Then the next 3x3 section would be the floor, the second would be the second layer, and the last would be the last layer. Essentially, each number will represent the type of object that's in that space, they could be a cube for the wall... A static model... A chunk of a terrain... Then, when you load it, you can simply create an array to hold each integer value. If you have less than 255 object types, you use unsigned char's in your file format to describe the levels, this will make your level files tiny...

Then, when it comes time to render and do the real time action, you have a nice array of your level to read from.

My advice with an OpenGL game, would be to load as much of the static parts (non-moving, such as terrain, walls, scenery) in a display list. Another optimization would be to use logic when creating the levels, and when rendering the cubes for the display list... In that example level for instance, the 2's on the floor layer are useless because they are being blocked by the 3'2 above them. Assuming that 0's are empty and 1's, 2's, and 3's are all cubes, you would never get to see those 2's, or the 3 in the bottom right corner of the second layer because it's obstructed by the 3 on top of it. So, rendering those each frame would be wasteful.

Also, with a cube, when two cubes are next to each other... Rendering the quads that are touching is wasteful, they will never be seen. So, a cube that is completely surrounded by cubes, will never get rendered.

One thing to clear up about the cube type objects... The number is usually used to represent the texture of that cube. When you have successive cubes of the same texture next to each other, why not fuse them into one large object when rendering and save polygons?

Btw, I mentioned wavefront ".obj" models as being simple... The only downside is that they aren't very standardized, one modeling program will output them slightly different than the next. As a reference, I can explain blender's ".obj" format because blender is free and widely used (and my favorite)...

The ".obj" file generally looks like this...

```

v 0 1 0
v 1 0 0
v 0 0 1
f 1 2 3

```

That tiny model file creates a triangle... Each line that begins with "v" means that it is a vertex, and will be followed by three values storing the x, y, and z. When a line begins with an "f" it will store either 3 or 4 values (if you triangulate your models it will always be 3 which makes things much easier) which stores the vertices that face connects. So, in that model, the first face connects the vertices (0,1,0)-(1,0,0)-(0,0,1). Larger models have many many more vertices and faces, but the same concept applies to loading them. When you render it, just iterate over the face array drawing the face by connecting the vertices it indexes.

Terrains are very similar to black-and-white images, the intensity of each "pixel" or "height point" represents the height of that point on the terrain. I've started a terrain tutorial [HERE.]("http://ubuntu-gamedev.wikispaces.com/Terrain+Tutorial+Part+1") It's not finished, and not edited, but it does explain some basic introductory usage of terrains.

Anyway, if you need some help at any point, just post or contact me. Good luck!

---

