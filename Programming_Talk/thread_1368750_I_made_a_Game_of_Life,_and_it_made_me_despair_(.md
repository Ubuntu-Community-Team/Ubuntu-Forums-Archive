---
title: "I made a Game of Life, and it made me despair :("
date: 2009-12-31
forum: Programming Talk
---

### Post by nmccrina on 2009-12-31
Ok, so I just finished a basic implementation of the Game of Life, and it uses 10% of my CPU (this is *just* my program; the shell is using extra). It is in C++, so there's not even any virtual machine/interpreter involved. I didn't ever look, but when I played WoW it didn't seem like the CPU was straining too much, so it was probably using less than 50% on average. Is my code really inefficient to the point that entire virtual worlds can be rendered with only a marginal increase in processing cost over my wimpy #'s in the console? There are a few areas where I think I could optimize my algorithm a little bit, but *still*. :(

---

### Post by Some Penguin on 2009-12-31
If you're mostly CPU-bound and do very little waiting for I/O to/from network or disk, and you don't have it set to a low priority or deliberately yielding to other processes, what else would you expect?

---

### Post by wmcbrine on 2009-12-31
I'd have to see your code to judge if it's efficient, but I think Life will absorb as much CPU as you want to throw at it. I figure, if you're not pegging the CPU, then you aren't running your generations fast enough, and/or your grid is too small. :)

I spent way, way too much time trying to optimize Life for the Z80 -- specifically, the Timex/Sinclair 2068 -- back in the day.

---

