---
title: "Traversing a maze using Dijkstra's algorithm."
date: 2007-11-17
forum: Programming Talk
---

### Post by SOULRiDER on 2007-11-17
The other day during class, we had to use a Backtracking algorithm to traverse a maze and find the path from the entrance to the exit (or vice-versa) that makes the less turns.

Last night i wrote a solution using Dijkstra's algorithm instead of using a backtracking technique. Here is the source code, i hope its clear for everyone to understand.

To try out the program just call it as you normally would and then give the different rows as arguments like this:

For a maze that looks like
111111
11x001
1101x1
call the program this way:
./Laberintos.py 111111 11x001 1101x1 (please note, a 1 means a wall, 0 a free space and x mark entrances/exits. The program is intended to work on a rectangular amze with just 2 x;s, i dont know how it may react in other conditions :P)

Here it goes, enjoy!

---

### Post by CptPicard on 2007-11-17
Cool. I actually wrote an applet that does the same thing as a project when I was a student :)

I hope you're using a heap to find the minimum node? :)

---

### Post by SOULRiDER on 2007-11-17
I was planning on doing that, but i dont know if Python has one implemented (it most likely does) and i didnt want to implement one :P

---

### Post by CptPicard on 2007-11-18
Well.. there is the module heapq, but doing this by hand into an array would be a great exercise -- a binary heap in array is a nice, simple, illustrative data structure.

---

### Post by SOULRiDER on 2007-11-18
I ahve already implemented a Priority Queue using a Heap, but in C++, i think ill make one for python and use it for this problem too. Ill post it here as soonas  it gets done (if ever :P)

---

### Post by CptPicard on 2007-11-18
Next algorithm you might want to consider implementing is A*...

---

