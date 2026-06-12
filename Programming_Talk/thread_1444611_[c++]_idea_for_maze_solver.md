---
title: "[c++] idea for maze solver"
date: 2010-04-01
forum: Programming Talk
---

### Post by Xender1 on 2010-04-01
So I want to work on my skills with graphs and graph traversal etc. and I came up with a project that reads in a file that is (eventually will be able to generate) a maze and then finds the route through the maze to solve it. (this will just be simple like # for a wall and a space for a path)

First off, I want to know if this is even a good way for practice (is solving a maze via a graph a smart way to go about it?). Since I want to be able to do all sorts of mazes (ones with cycles etc.), i was thinking of making each cell a vertex, then have an edge connecting that cell (vertex) to the adjacent cells on the open path. doing it this way i feel like a BFS of this graph would yield a result (not most efficient way though). 

Think this is a good idea? And also I did some research on maze traversal algorithms and found a few, do you have a favorite of your own and why?

---

### Post by azagaros on 2010-04-01
if you have the grid pattern of '#' and ' ' for open area's there are recursive search algorithms for those kind of mazes.  I have been aware of them for 20years.  A maze generator is the same kind of algorithms.  Check out the game of Angband or Moria if you can find them.  The original forms of them didn't have graphics.  They would be open source and give you a starting point in C I believe.

---

### Post by johnl on 2010-04-01
I would recommend either [_A*_](http://en.wikipedia.org/wiki/A*_search_algorithm) or [_Dijkstra's Algorithm_](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) (which is simpler than A*).

---

### Post by Xender1 on 2010-04-01
Yea i will be using Dijkstra's as I have actually already done an implementation of that in the past. Now i have sort of another questions and its something i have always wanted to know. 

So sure its nice to be able to solve a maze when its in text form, but i feel like most of the time the maze would be a picture (png/gif/etc.) for example this maze here [URL="http://www.astrolog.org/labyrnth/maze/cruiser1.gif"]. Now, I have never really worked with images before, so is there a way to read this and conver it to text or... like have my c++ be able to understand the image (like the black and white pixels). Is there a way to do this? 

Thanks.

---

### Post by Lux Perpetua on 2010-04-01
> **Xender1 said:**
> Yea i will be using Dijkstra's as I have actually already done an implementation of that in the past. Now i have sort of another questions and its something i have always wanted to know. 

So sure its nice to be able to solve a maze when its in text form, but i feel like most of the time the maze would be a picture (png/gif/etc.) for example this maze here [URL="http://www.astrolog.org/labyrnth/maze/cruiser1.gif"]. Now, I have never really worked with images before, so is there a way to read this and conver it to text or... like have my c++ be able to understand the image (like the black and white pixels). Is there a way to do this? 

Thanks.Sure. It's just a matter of reading an image file and seeing it as a 2D array of pixel values, and any imaging library will do this for you. I've usually used SDL (with SDL_image) in the past, but there's also imagemagick, etc.

---

### Post by nvteighen on 2010-04-02
> **Xender1 said:**
> Yea i will be using Dijkstra's as I have actually already done an implementation of that in the past. Now i have sort of another questions and its something i have always wanted to know. 

So sure its nice to be able to solve a maze when its in text form, but i feel like most of the time the maze would be a picture (png/gif/etc.) for example this maze here [URL="http://www.astrolog.org/labyrnth/maze/cruiser1.gif"]. Now, I have never really worked with images before, so is there a way to read this and conver it to text or... like have my c++ be able to understand the image (like the black and white pixels). Is there a way to do this? 

Thanks.

A nice solution would be to have two mazes... The real one and the one the user sees. The real one would be a data structure (a matrix?) that uses some conventional signs to represent the maze; the maze the user sees would be the graphical one, first generated from the data structure and then updated each time that the real one is updated.

The great advantage of such an approach is that it makes it really easy to separate UI code from implementation. The "bridge" between both will be the updating procedures.

... In other words, what I've just described is a Model-View-Controller design :p

---

### Post by pbrane on 2010-04-02
You could always have a look at the Maze hack in xscreensaver.

---

