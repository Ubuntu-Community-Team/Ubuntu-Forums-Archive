---
title: "[C++] What's going on here? (Structs)"
date: 2009-08-24
forum: Programming Talk
---

### Post by Drone022 on 2009-08-24
Hey,

I was looking at some c++ code and I came across this:

```
struct Vec {
  double x, y, z;
  **Vec(double x2, double y2, double z2) : x(x2), y(y2), z(z2) {}**
};
```

At first I wasnt sure what that second line was doing exactly, is it so the struct can be instantiated and that acts as its constructor? Does it mean I can do this...

```

Vec myVector = new Vec(2,4,6);

```

Then in myVector x = 2, y = 4, z = 6?

Thanks

---

### Post by TheStatsMan on 2009-08-24
Yes that is correct. The second line is the constructor and the part after the : is an initisation list. 

The second part of your code isn't quite correct. Simply:

[PHP]
Vec v(2,4,6);

where

v.x=2, etc.

[/PHP]

---

### Post by Drone022 on 2009-08-24
Thank you very much.

---

