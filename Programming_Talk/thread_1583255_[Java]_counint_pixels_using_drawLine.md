---
title: "[Java] counint pixels using drawLine"
date: 2010-09-27
forum: Programming Talk
---

### Post by hanniph on 2010-09-27
Hey, 

I've started reading 'Computer graphics for Java programmers' and ran into this problem:

**How many pixels are put on the screen by the following call?**

```
g.drawLine (10, 20, 100, 50);

```

Both the answer **91** and the short explanation(100 - 10 + 1) are unclear to me. It would be great if somebody could explain it (for example, why we add 1?) or give some hints on this. I'm new to graphics :)

Thanks

---

### Post by Reiger on 2010-09-27
Fairly simple: consider the delta's in x and y coordinates. 90 and 30 respectively. There will be no duplicate x coordinates because 30 divides 90 cleanly (90/30 = 3).
In other words it works out as 3 to the right, per 1 down, i.e the line is approximated by placing pixels in a pattern like this where (.) is a single coloured pixel:
```

...
   ...
      ...

```

So 90 pixels to draw *from* (10,20) [inclusive] to (100,50) [exclusive], and one pixel to draw (100,50).

---

### Post by hanniph on 2010-09-27
Nice one. That's right, it wasn't that hard. Thanks for clearing this :)

---

