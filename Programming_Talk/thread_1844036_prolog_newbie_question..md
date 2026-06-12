---
title: "prolog newbie question."
date: 2011-09-14
forum: Programming Talk
---

### Post by abhilashm86 on 2011-09-14
I'm trying to draw some textual figure astrrick on screen using prolog recursion, like the following. 

> 
?- bars(3).
  *
 ***
*****
  *
  *
?- bars(4).
   *
  ***
 *****
*******
   *
   *

Till now i'm able to draw till this much, i could not figure out how exactly to draw this textual figure. So i ended up writing this junk!

bars([]).

bars([N|L]) :-
  stars(N),nl,
  bars(L).

stars(N) :-
  N>0,
  write(*),
  N1 is N-1,
  stars(N1).
  
stars(N) :-
  N=<0.

Any help would be appreciated. I'm not able to print and show proper asterick in forum post too, basically it starts from middle n descends.

---

