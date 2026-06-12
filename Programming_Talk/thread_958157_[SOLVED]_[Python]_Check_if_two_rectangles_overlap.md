---
title: "[SOLVED] [Python] Check if two rectangles overlap?"
date: 2008-10-25
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-25
How to check if two rectangles overlap, and perhaps return the overlapping area?

---

### Post by pp. on 2008-10-25
In this kind of problem, the sides of the rectangles usually are strictly horizontal and vertical, respectively.

Also, rectangles usually are given by four magnitudes: x ordinates of the left and right side, y ordinates of the top and bottom.

Take a piece of paper and draw a few rectangles, keeping in mind what I just wrote.

---

### Post by crazyfuturamanoob on 2008-10-25
Umm... I define my rectangles with top left corner and bottom right corner. Ok?
Both corners are tuples, presenting the x and y coords.

---

### Post by pp. on 2008-10-25
> **crazyfuturamanoob said:**
> Umm... I define my rectangles with top left corner and bottom right corner. Ok?
Both corners are tuples, presenting the x and y coords.

Yes. Hence you know the top, right, bottom and left edge, don't you?

---

### Post by crazyfuturamanoob on 2008-10-25
Never mind I found a module for rects and points with google that I can use. Solved.

---

### Post by fiddler616 on 2008-10-25
I'd still think about what pp. said, in the interest of tight code.

```

  A,B         
  ---------------
  |             |
  |   A',B'|----|----|
  |        |    |    |
  |--------|----|    |
           |  C,D    |
           |---------|
                      C',D'

```
Compare A' with A and C, and B' with B and D.

---

### Post by pp. on 2008-10-25
> **crazyfuturamanoob said:**
> Solved.

:lolflag:

---

