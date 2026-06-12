---
title: "A* and 15 puzzles"
date: 2008-05-06
forum: Programming Talk
---

### Post by joebanana on 2008-05-06
I am working on algorithm for 15 puzzles. I am trying to implement A* and I just cant figure out how the formula is for evaluating h in heuristic function. I am following this tutorial. [A*]("http://www.geocities.com/jheyesjones/astar.html")
It includes explanation for h but maybe it's just that my English is so bad and I can't see it from the picture. :) Thx for help.

---

### Post by mike_g on 2008-05-06
Theres various ways to get the heuristic, but to find the shortest path you must never overestimate the minimum possible move cost to the target.

The way I did it in the past was to use Pytharoras to get a striaght line distance based on the minimum move cost. In pseudo code for a 2d grid:
```
dx = pos_x - target_x;
dy = pos_y - target_y;
distance = square_root_of( (dx*dx)+(dy*dy) );
heuristic = distance * base_move_cost;

```
This can be expensive tho if you are doing realtime pathfinding in a game or something. So if you want something quick, that does not necessarily get the shortest path you could just do:
```
heuristic = (dx + dy) * base_move_cost;
```

---

### Post by joebanana on 2008-05-07
So you used an euclidian distance. I found a number of suggestion that with 15 puzzles it's good to follow Manhattan distance(which is almost the same except diagonal movement). In the case of a 8 puzzles which goal is:
```

A B C
H   D
G F E

```
I found a Nelson sequence(on the above link) which converges quickly. Does anybody know a heuristic similar function for 15-puzzles in the shape:
```

1  2  3  4
5  6  7  8
9  10 11 12
13 14 15

```
that converges faster than minimum Manhattan distance? (If there is any other criteria.)

---

### Post by Lster on 2008-05-07
You may be interested in this link:

[http://www.policyalmanac.org/games/aStarTutorial.htm](http://www.policyalmanac.org/games/aStarTutorial.htm)

This is what I used when learning A* searching. I found the section, "Summary of the A* Method", to be especially useful. :)

---

