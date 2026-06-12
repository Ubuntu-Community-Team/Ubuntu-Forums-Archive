---
title: "OpenGL Per-Pixel collision detection"
date: 2008-06-16
forum: Programming Talk
---

### Post by AZzKikR on 2008-06-16
For starters: I know OpenGL is a graphics library, and collision detection needs to be handled by custom code. 

I've searched the net for some ideas how to do collision detection  per pixel with OpenGL, but I only came to ideas using the stencil buffer, and using occlusion queries (whatever they might be).

I realised that for the engine I'm working on, true per-pixel collision isn't exactly needed (so I'll just specify rough bounding boxes - easier for me, and easier for the CPU and/or GPU). I am still wondering however, if I **eventually** may need it... how would one accomplish such a thing?

---

### Post by slavik on 2008-06-16
there are 3-4 levels of collision detection. from simplest to most difficult/intense:
1. sphere
2. axis aligned bounding box
3. bounding box
4. "polygon soup"

In polygon soup, what you do is check each polygon in 1 model against each polygon in another model.

Look up a library called "coldet." It was made to be used with OpenGL (the calls you make are similar). You create a model in coldet by using calls similar to what you would use to make OpenGL draw it (glBegin(GL_TRIANGLES)) and then if you do any transformations/rotations to it, you also tell coldet to do it (OpenGL does it to the visual world, coldet does it to the physical world). Then you ask coldet to look at 2 objects you are interested in. AFAIK, coldet will first do sphere collision check for near collision and if that returns positive, it will do a more thorough check.

BTW, are you looking for collision detection between 2 objects in the world or to see where the mouse is pointing (as if shooting a bullet in an FPS)?

---

### Post by Wybiral on 2008-06-16
> **slavik said:**
> AFAIK, coldet will first do sphere collision check for near collision and if that returns positive, it will do a more thorough check.

I don't know anything about coldet, but I will say that the best performance you will get out of collision detection is with some kind of spacial optimizations on top of the "bounding sphere"->...->"poly collision" refining. Even something as simple as a [quad tree]("http://en.wikipedia.org/wiki/Quadtree") to segment the world up into spacial bounds will improve the amount of potential collisions you can cull. Depending on the world, this might be good enough, but in some cases you will get way better performance with some form of [binary partitioning]("http://en.wikipedia.org/wiki/Binary_space_partitioning"), creating a binary tree of planes where traversing the tree creates a smaller and more refined area at each level, this allows you to cut precise chunks into the world where potential collisions might be higher, breaking them up.

Of course, the size of the world, number of polygons, and the shape of the objects/world are all factors.

---

### Post by slavik on 2008-06-16
> **Wybiral said:**
> I don't know anything about coldet, but I will say that the best performance you will get out of collision detection is with some kind of spacial optimizations on top of the "bounding sphere"->...->"poly collision" refining. Even something as simple as a [quad tree]("http://en.wikipedia.org/wiki/Quadtree") to segment the world up into spacial bounds will improve the amount of potential collisions you can cull. Depending on the world, this might be good enough, but in some cases you will get way better performance with some form of [binary partitioning]("http://en.wikipedia.org/wiki/Binary_space_partitioning"), creating a binary tree of planes where traversing the tree creates a smaller and more refined area at each level, this allows you to cut precise chunks into the world where potential collisions might be higher, breaking them up.

Of course, the size of the world, number of polygons, and the shape of the objects/world are all factors.
yeap.

EDIT: It also depends on how many moving objects you have. if you have 1, there is really no need to partition the space (unless it is huge or the number of objects is huge). IE: If it's a ball in a room, I wouldn't partition the space, but if it's a lot of balls in a large cube (jezzball on steroids) then space partitioning definitely helps.

---

### Post by Wybiral on 2008-06-16
> **slavik said:**
> yeap.

EDIT: It also depends on how many moving objects you have. if you have 1, there is really no need to partition the space (unless it is huge or the number of objects is huge). IE: If it's a ball in a room, I wouldn't partition the space, but if it's a lot of balls in a large cube (jezzball on steroids) then space partitioning definitely helps.

I don't get why moving has anything to do with it. Suppose you have the player in a level full of 10,000 statues (for instance)... Without partitioning, how do you plan on handling the collision with every statue? Would you do a bounding sphere for all 10,000 statues? Or would you break the room into smaller pieces where each partition has a finite limit on the number of statues in it?

Even for smaller numbers, you'll only end up at one or two levels of partitioning, so it's not going to cause any performance overhead, it's just prepared for handling even more.

---

### Post by slavik on 2008-06-16
> **Wybiral said:**
> I don't get why moving has anything to do with it. Suppose you have the player in a level full of 10,000 statues (for instance)... Without partitioning, how do you plan on handling the collision with every statue? Would you do a bounding sphere for all 10,000 statues? Or would you break the room into smaller pieces where each partition has a finite limit on the number of statues in it?

Even for smaller numbers, you'll only end up at one or two levels of partitioning, so it's not going to cause any performance overhead, it's just prepared for handling even more.
when you have an object, and you do a call to glRotate to rotate the object, the physical world has to follow the visual world.

as for 10,000 statues, if there is only 1 thing moving around them, then it is not a big deal to check each one and you would probably save the center coordinates of every statue when importing them anyway.

---

### Post by Wybiral on 2008-06-16
> **slavik said:**
> when you have an object, and you do a call to glRotate to rotate the object, the physical world has to follow the visual world.

as for 10,000 statues, if there is only 1 thing moving around them, then it is not a big deal to check each one and you would probably save the center coordinates of every statue when importing them anyway.

I'm sorry, but this is really bad advice for anything that plans to be more than a handful of objects. There's absolutely no reason to do that many collision checks when you can simply partition the world up a bit. If they're not moving, it's even easier, you just build the quad-tree or bsp-tree before hand and traverse it when you need to do your collision.

---

### Post by AZzKikR on 2008-06-17
Okay.... thanks for the information though, it seems it loads up quite a discussion :)

I'm in the making of a 2D game engine, so we'll probably use 2D sprites only. A character has to walk over a sort of 'dynamic' terrain, and that is why I am interested in collision detection.

I've been drawing out sort of ideas how to do the collision detection I want. Hope it will work out.

---

### Post by slavik on 2008-06-17
> **AZzKikR said:**
> Okay.... thanks for the information though, it seems it loads up quite a discussion :)

I'm in the making of a 2D game engine, so we'll probably use 2D sprites only. A character has to walk over a sort of 'dynamic' terrain, and that is why I am interested in collision detection.

I've been drawing out sort of ideas how to do the collision detection I want. Hope it will work out.
Ahh, 2D ... even simpler!!!

one thing you can do here is XOR the two sprites' and see if you get any zeroes in the result, if you do, they are intersecting at those pixels.

---

