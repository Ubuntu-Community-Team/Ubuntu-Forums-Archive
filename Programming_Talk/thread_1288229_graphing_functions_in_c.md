---
title: "graphing functions in c"
date: 2009-10-11
forum: Programming Talk
---

### Post by Vichfret on 2009-10-11
I want to make a program to graph mathematical functions in c but I don't know how, can you help me with this? I've never used graphics when programming. When I learn this I'll try to make a program to graph fractals :)

---

### Post by matmatmat on 2009-10-11
Look for allegro, or SDL (C++). Also try gnuplot.

---

### Post by Themaister on 2009-10-11
I have made a little library in C/SDL for school that you might be interested in using :)
[http://code.google.com/p/sdl-grapher/](http://code.google.com/p/sdl-grapher/)

There is some documentation in the header file, along with an example file.

The example.c file is maybe a bit too much, but let's say you want to print
out a y = x^2 graph

```


#include <sdlgraph.h>

int main()
{
  Graph myGraph;
  
  myGraph.xMin = -10.0;
  myGraph.xMax = 10.0;
  myGraph.yMin = 0.0;
  myGraph.yMax = 100.0;
  myGraph.xScale = 1.0;
  myGraph.yScale = 1.0;
  myGraph.height = 800;
  myGraph.width = 800;

  init_graph(&myGraph);
  draw_grid(&myGraph, 0, 2);
  update_screen(&myGraph);

  float x, y;
  set_color(&myGraph, 255, 0, 0);
  for ( x = -10.0; (int)x < 10; x += 0.01 )
{
  y = x*x;
  print_pixel ( &myGraph, x, y );
  update_screen(&myGraph);
}

idle();
quit();
return 0;
}

```

---

