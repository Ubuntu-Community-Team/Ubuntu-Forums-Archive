---
title: "Super Star Trek: Made of Magic?"
date: 2006-05-24
forum: Programming Talk
---

### Post by DirtDawg on 2006-05-24
I've been playing this old skool game: [Super Star Trek]("http://almy.us/sst.html"). It's old, so I assume the programming is somewhat simple (by today's standerds), but here's what I can't figure out,

The map is based on an 8X8 grid, which I assume they used a matrix to build (the equivalent of a dictionary in Python?). So it looks something like the following.
```

  0 1 2 3 4 5 6 7 8
1 .  * .  .  .  .  .  .  .
2 .  .  .  .  .  .  * .  .
3 .  .  E .  .  .  .  .  .
4 .  .  .  .  .  .  .  .  .
5 .  .  .  .  * .  .  .  .
6 .  .  .  .  .  .  .  .  .
7 .  .  .  .  .  .  k .  .
8 .  .  .  .  .  .  .  .  .  

```
(This looked a lot better between the CODE tags when I wrote it, but you get the idea.)

Where 
E= Enterprise
k= Klingon
*= star

So if the Enterprise shoots a photon torpedo, what method did the programmers use to calculate a hit or whether there's an obstacle in the way? 

Would they have usesd the matrix system? Like -- while position<9: (3,3) +(1,1) +(1,1)? If this is the case, how would the player hit anything not lying directly on a path (exactly diagonal/straight)?

It also occured to me they may have used math (eeeek!). Perhaps they used (y2-y1)/(x2-x1) to determine a firing line? But how would they translate these numbers to the matrix system to determine hits or interferance? 

I've looked at both the ansi-C code and [the original code]("http://www.atariarchives.org/basicgames/showpage.php?page=157"), but I'm a hobbyist programmer and really only understand Python with any great depth and, frankly, can't make heads or tails out of the code.

I'm immensly curious about this and have been milling over it for several days as well as attempting to code a duplicate in an attempt to learn, but I'm stumped.

Anyone willing to humor my curiousity would have my undying gratitude. :KS

---

### Post by nanotube on 2006-05-24
well, even though it is a discrete matrix of positions (i assume an object cannot be between gridpoints?), each dot/object can still be assigned coordinates in a simple 2d cartesian system - and then it is a simple matter of determining if there are any other objects on the line segment between you and your target (yes, some basic math :) ).

at least that would be my guess on how they implemented this. i have never played or even heard of this game before in my life...

---

### Post by thumper on 2006-05-24
Stop assuming that just because it is old that it is simple.

Also I'd not store the map as a dictionary, but as an object with coordinates for the "things".

Have a go writing it based on what you observe and enjoy :)

---

### Post by DirtDawg on 2006-05-25
[QUOTE=nanotube]well, even though it is a discrete matrix of positions (i assume an object cannot be between gridpoints?), each dot/object can still be assigned coordinates in a simple 2d cartesian system - and then it is a simple matter of determining if there are any other objects on the line segment between you and your target (yes, some basic math :) ).

at least that would be my guess on how they implemented this. i have never played or even heard of this game before in my life...[/QUOTE]

Sweet. A quick Google on "cartesian system" brings all kinds of info(i didn't know the true name of what I refer to as "that graph thingy"). I still don't entirely understand, but a direction is really great. Thanks a ton.

---

### Post by DirtDawg on 2006-05-25
[QUOTE=thumper]Stop assuming that just because it is old that it is simple.

Also I'd not store the map as a dictionary, but as an object with coordinates for the "things".

Have a go writing it based on what you observe and enjoy :)[/QUOTE]

I knew I'd get scolded about the 'simplicity' remark. I tried to shield myself with the 'relatively' statement. Considering I don't understand how Super Star Trek even works, I consider it complex. However, it is easier for me to wrap my head around than, say, World of Warcraft.

I wondered about the Dictionary/Array. I went to Powell's Technical Bookstore (I love Portland) and looked through this book about retro gaming which introduced me to the idea of 'arrays'. The closest Python equivalent I can imagine is a dictionary of nested lists. Classes are a given, but my skillz aren't sharp enough to piece everything together yet. 

Thanks for the input. I'm having fun stumbling along. If I get stumped again, I hope I can come back for more ideas.
Peace :mrgreen:

---

### Post by nanotube on 2006-05-25
[QUOTE=DirtDawg]Sweet. A quick Google on "cartesian system" brings all kinds of info(i didn't know the true name of what I refer to as "that graph thingy"). I still don't entirely understand, but a direction is really great. Thanks a ton.[/QUOTE]
heh, good luck. ;) i will note though, that if you are interested in programming games, you will definitely need to improve your basic algebra/geometry skills. for example, in this case, you must know how to find the equation for a straight line, given two points on that line, and then see if another point is also on that line. 
so, if that is "new stuff" for you, i suggest picking up a math textbook. :)

---

### Post by nanotube on 2006-05-25
[QUOTE=DirtDawg]I knew I'd get scolded about the 'simplicity' remark. I tried to shield myself with the 'relatively' statement. Considering I don't understand how Super Star Trek even works, I consider it complex. However, it is easier for me to wrap my head around than, say, World of Warcraft.

I wondered about the Dictionary/Array. I went to Powell's Technical Bookstore (I love Portland) and looked through this book about retro gaming which introduced me to the idea of 'arrays'. The closest Python equivalent I can imagine is a dictionary of nested lists. Classes are a given, but my skillz aren't sharp enough to piece everything together yet. 

Thanks for the input. I'm having fun stumbling along. If I get stumped again, I hope I can come back for more ideas.
Peace :mrgreen:[/QUOTE]

a one-dimensional array of C is basically the same as your basic list in python. a two-dim array in C is basically a m by n matrix of numbers, indexed by integers. in python, the equivalent would be a nested list - one list of length m, containing m lists of length n. three-dim: add another layer of nesting.

of course, lists in python are more powerful than your basic C arrays, but there's your basic idea. :)

the dictionary data structure does not enter into this at all - since dicts are indexed by keys, and there is no such thing is C.

---

### Post by DirtDawg on 2006-05-25
[QUOTE=nanotube]heh, good luck. ;) i will note though, that if you are interested in programming games, you will definitely need to improve your basic algebra/geometry skills. for example, in this case, you must know how to find the equation for a straight line, given two points on that line, and then see if another point is also on that line. 
so, if that is "new stuff" for you, i suggest picking up a math textbook. :)[/QUOTE]

Tell me about it. I took pre-calculus last year, but I'm no math whizz and have forgotten nearly all of it. I've been scouring my old textbook to find relevant formulas, so I'll find it sooner or later. Now that I know that's the direction I need to go, it makes it easier to stay on track.

I played around with nested lists as a matrix last night and it worked out rather well. Here's my idea of a dictionary matrix vs. what I discovered last night:
```

matrixD= {
               1:[0,1,2,3,4,5],
               2:[0,1,2,3,4,5],
               3:[0,1,2,3,4,5],
               4:[0,1,2,3,4,5],
               5:[0,1,2,3,4,5]
               }

matrixL= [
              [0,1,2,3,4,5],
              [0,1,2,3,4,5],
              [0,1,2,3,4,5],
              [0,1,2,3,4,5],
              [0,1,2,3,4,5]
              ]

```

What I thought of as an advantage in the first method was I could access a vector like 'sooper-ship.location= matrixD[4][3]'. The list method seems just as effective, however, and indexing seems like a better way to manage things than keys. My lack of understanding about such basics is a testament to absence of formal training.    

Who knows if I'll actually make a game or not, but I find screwing around with code is not only fun, but relaxing. Thanks for all the tips! :)

---

### Post by nanotube on 2006-05-25
[QUOTE=DirtDawg]Tell me about it. I took pre-calculus last year, but I'm no math whizz and have forgotten nearly all of it. I've been scouring my old textbook to find relevant formulas, so I'll find it sooner or later. Now that I know that's the direction I need to go, it makes it easier to stay on track.

I played around with nested lists as a matrix last night and it worked out rather well. Here's my idea of a dictionary matrix vs. what I discovered last night:
```

matrixD= {
               1:[0,1,2,3,4,5],
               2:[0,1,2,3,4,5],
               3:[0,1,2,3,4,5],
               4:[0,1,2,3,4,5],
               5:[0,1,2,3,4,5]
               }

matrixL= [
              [0,1,2,3,4,5],
              [0,1,2,3,4,5],
              [0,1,2,3,4,5],
              [0,1,2,3,4,5],
              [0,1,2,3,4,5]
              ]

```

What I thought of as an advantage in the first method was I could access a vector like 'sooper-ship.location= matrixD[4][3]'. The list method seems just as effective, however, and indexing seems like a better way to manage things than keys. My lack of understanding about such basics is a testament to absence of formal training.    

Who knows if I'll actually make a game or not, but I find screwing around with code is not only fun, but relaxing. Thanks for all the tips! :)[/QUOTE]

heh well, i don't have any formal training either - everything i learned about python was on python.org website, under documentation :) i just like screwing around with code for the hell of it, too. so, that means, 1: don't take what i say as absolute truth, and 2: if i could do it, so can you :)

---

### Post by yaaarrrgg on 2006-05-25
a couple rough thoughts...

you probably want to take the approach that each cell will have a finite number of display states.  internally though, your sprites can be moving on imaginary smooth lines.

you really need to understand the equation of a line:

```

y = m*x + b

```

then you use math functions like mod() and floor(), when you snap an imaginary line to the closest display block.

really, not that much difference from programming any game, except the screen resolution is lower.

---

### Post by hod139 on 2006-05-25
[quote=yaaarrrgg]
you really need to understand the equation of a line:

```

y = m*x + b

``` 
then you use math functions like mod() and floor(), when you snap an imaginary line to the closest display block.
[/quote]

Be careful with that formula; it is undefined for vertical lines since the slope *m* = infinity.  For computers it's even worse since they have finite precision; that formula won't work for lines that are "close" to vertical.

There are 2 solutions that I can think of off hand.
Solution 1 (the easiest) would be to special case vertical lines.
Solution 2 would be to use[ polar coordinates]("http://mathworld.wolfram.com/PolarCoordinates.html"), which are always defined.

---

### Post by yaaarrrgg on 2006-05-25
> **hod139]Be careful with that formula said:**
>  polar coordinates[/URL], which are always defined.

Yes that's true... Also, might use the parametric version of the equation...

```

x = m1 * t + b1
y = m2 * t + b2

```

or, can think of it as some change of x and y, recursively defined:

```

x_new = x_old + dx
y_new = y_old + dy

```

where dx and dy are two constants.  

then, if you need bullets comiing out of a rotation ship, this use sin() and cos():

```

x_new = x_old + cos(angle) * speed
y_new = y_old + sin(angle) * speed

```

these changes are applied at each iteration of the main game loop.

this probably covers the all the math you need for the game (aside from collision detection).

---

### Post by DirtDawg on 2006-06-02
A week ago, I had no idea what on Earth you folks were mathing about. Since then, I've done some studying. I tried the y=mx+b formula first as it seemed the easiest to understand. Once I figured out why a y-intercept was important and how to find it, I managed to draw some rudamentary lines on my star map. But I couldn't quit get it right. (Also, as mentioned, vertical lines did not work)

Since then, I've done lots of reading about polar coordinates (which are pretty neat) and angles of right triangles, etc. I'm still not entirely clear how everything works or how to apply the mathamatics to actual programming practice, but I'm starting to "get it". 

I will say this: when there is an immediate, applicable scenario to which one can apply the mathimatics one is learning, the mathimatics not only become easier to comprehend, but also way "awsomer".

Thanks again for the input everybody and I'll keep screwing around until I get bored or fail school finals because I'm too distracted by puzzles.

Peace :mrgreen:

---

### Post by nanotube on 2006-06-03
[QUOTE=DirtDawg]A week ago, I had no idea what on Earth you folks were mathing about. Since then, I've done some studying. I tried the y=mx+b formula first as it seemed the easiest to understand. Once I figured out why a y-intercept was important and how to find it, I managed to draw some rudamentary lines on my star map. But I couldn't quit get it right. (Also, as mentioned, vertical lines did not work)

Since then, I've done lots of reading about polar coordinates (which are pretty neat) and angles of right triangles, etc. I'm still not entirely clear how everything works or how to apply the mathamatics to actual programming practice, but I'm starting to "get it". 

I will say this: when there is an immediate, applicable scenario to which one can apply the mathimatics one is learning, the mathimatics not only become easier to comprehend, but also way "awsomer".

Thanks again for the input everybody and I'll keep screwing around until I get bored or fail school finals because I'm too distracted by puzzles.

Peace :mrgreen:[/QUOTE]
haha that's great dude! keep having fun! :)
(but it might be prudent to delay the fun until finals are over... )

---

