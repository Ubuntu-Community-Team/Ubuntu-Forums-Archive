---
title: "Modelling variously shaped &quot;gameboards&quot;."
date: 2010-05-23
forum: Programming Talk
---

### Post by jwbrase on 2010-05-23
I've been pondering how one might model a good approximation of the surface of a spherical planet for a strategy game, and have some ideas, but I'm not sure entirely how one would go about coding them.

To start off with, I'll go with what I do understand:

A flat, finite, square board, could be represented as a 2-dimensional array:

```
gameSquare[xsize][ysize] board;
...
//Boundary conditions
move (xAmount, yAmount)
{
   xLocation += xAmount;
   yLocation += yAmount;

   if (xLocation > xsize)
   {
       xLocation = xsize;
   }
   if (yLocation > xsize)
   {
       yLocation = xsize;
   {
   if (xLocation < 0)
   {
       xLocation = 0;
   }
   if (yLocation < 0)
   {
       yLocation = 0;
   }
}

```

To use C or Java-like pseudo-code.

Many games (The Civilization series, for example) will let the x axis wrap around to give a "round" map, although this is only a cylinder:

```

move(xAmount, yAmount)
{
    xLocation = (xLocation + xAmount) % xSize;
    //code for handling y movement
}

```

Sometimes you'll see games with toroidial maps, where the y axis wraps as well. The problem is that a torus is not a sphere any more than a cylinder is.

I have several other ideas, but am not quite sure how they would be implemented.

Firstoff, a cube. This can be represented by two square arrays at the "poles" and one rectangular one at the equator, with a height equal to that of the polar arrays and a width four times that (or, alternatively, by six equal-sized square arrays). Stepping off the north edge of the equatorial array moves a unit to somewhere or the perimeter of the north polar array, according to where it stepped off, stepping off the south edge puts it on the perimeter of the south polar array. The problem is that I'm not sure how one would code the transition.

An even better approximation of a sphere would be an icosahedron. This would have triangular faces, so we'd need to implement 20 triangular maps.

A triangular map could be modeled as an array of arrays where row number one is an array of length 1, row 2 has length 2, row three has length three, and row n has length n. The trouble is that I'm not sure how to implement such an array, and, as with the cube, I'm unsure how to implement the joining of the maps once I've implemented them.

Any pointers?

---

### Post by tookyourtime on 2010-05-23
I was thinking polar coordinates, but I dont know where that would leave collision detections and actual rendering...

---

### Post by jwbrase on 2010-05-23
> **tookyourtime said:**
> I was thinking polar coordinates, but I dont know where that would leave collision detections and actual rendering...

Well, I was thinking more of discrete "square by square" (or "hex by hex") coordinates for a turn-based game. (Like chess, checkers, Civilization, battle for Wesnoth, etc).

---

### Post by wmcbrine on 2010-05-23
Declare the polar regions as uninhabitable/untraversable? :) Hey, it worked for Mercator...

---

### Post by Letrazzrot on 2010-05-23
> **jwbrase said:**
> 

Firstoff, a cube. This can be represented by two square arrays at the "poles" and one rectangular one at the equator, with a height equal to that of the polar arrays and a width four times that (or, alternatively, by six equal-sized square arrays). Stepping off the north edge of the equatorial array moves a unit to somewhere or the perimeter of the north polar array, according to where it stepped off, stepping off the south edge puts it on the perimeter of the south polar array. The problem is that I'm not sure how one would code the transition.


Best visualized as 6 rectangular arrays.  Get out a piece of graph paper and "unfold" a cube -- the links from and two each edge of each face should be clear enough to sort out.  Note that "up" will not always be "north" depending on which face you place the poles.  See here for a discussion of actual cubic projections: [http://www.progonos.com/furuti/MapProj/Dither/ProjPoly/projPoly2.html](http://www.progonos.com/furuti/MapProj/Dither/ProjPoly/projPoly2.html)


> 
An even better approximation of a sphere would be an icosahedron. This would have triangular faces, so we'd need to implement 20 triangular maps.

A triangular map could be modeled as an array of arrays where row number one is an array of length 1, row 2 has length 2, row three has length three, and row n has length n. The trouble is that I'm not sure how to implement such an array, and, as with the cube, I'm unsure how to implement the joining of the maps once I've implemented them.
Like this?: 


[IMG]http://home.comcast.net/%7Ethinlines/hexmaps/PlanetMap.gif[/IMG]


Again, the links can be mapped out.  This gets more complicated, however, since hexes are involved.  However, Google should rope in some good algorithms for dealing with hex-->cartesian and vice versa.

I think that most times toroidal maps are used because of their simplicity.  Trying to portray a 3d object on an unmoving flat plane (i.e. a computer screen or game board), and keep it from confusing the player, would be difficult.  I can't think of a game where this has been done, although I'm not a fan of wargames where one might see this.

---

### Post by jwbrase on 2010-05-28
> **Letrazzrot said:**
> Best visualized as 6 rectangular arrays.  Get out a piece of graph paper and "unfold" a cube -- the links from and two each edge of each face should be clear enough to sort out.  Note that "up" will not always be "north" depending on which face you place the poles.  See here for a discussion of actual cubic projections: [http://www.progonos.com/furuti/MapProj/Dither/ProjPoly/projPoly2.html](http://www.progonos.com/furuti/MapProj/Dither/ProjPoly/projPoly2.html)


Like this?: 


The geometry I'm clear on. That's exactly what I was thinking of. What I'm not clear on is: A) Implementing a triangular array. B) The code to *implement* the joining of the maps (especially given the lines of hexes along the edges, and the individual pentagons at the vertexes). I'm perfectly clear on *how* they join.

I was actually going to use triangles instead of hexes, with movement being along the edges of triangles (instead of between their centers), but that's geometrically equivalent. The tricky part, with both my plan and the map you're showing there, is that you have rows of hexes/triangle vertices along the edges of the icosahedron that are split between two triangular sub-maps, and the vertices of the icosahedron are each split between five maps. I'm uncertain enough of how to code the join on a cube, and doing it on an icosahedron is rather daunting. Thus this thread asking for advice.

> 
Again, the links can be mapped out.  This gets more complicated, however, since hexes are involved.  However, Google should rope in some good algorithms for dealing with hex-->cartesian and vice versa.

I'm more focusing on the computer's internal representation of the map at the moment than displaying it on screen.

> 
I think that most times toroidal maps are used because of their simplicity.  Trying to portray a 3d object on an unmoving flat plane (i.e. a computer screen or game board), and keep it from confusing the player, would be difficult.  I can't think of a game where this has been done, although I'm not a fan of wargames where one might see this.

I think I've seen a few references to such a system being used in pencil-and-paper wargames/rpgs, but none to its use in computer games. I even once saw it used in a computer program meant to help with pen-and-paper rpg-ing, but the way it was put together was more meant to make for easy printout than for play on the computer (plus, it wasn't scalable to different numbers of hexes-per-edge, which I'd like). Furthermore, the program in question was freeware, but not F/OSS, so I have no access to the source code in question.

---

