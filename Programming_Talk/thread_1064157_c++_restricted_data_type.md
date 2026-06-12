---
title: "c++ restricted data type"
date: 2009-02-08
forum: Programming Talk
---

### Post by cguy on 2009-02-08
It may have been discussed before, but I have no idea on what search queries to use.

Is it possible to define a float data type which is bigger than 0, but smaller than 1?

eg:
float n ; // + the restriction
0.3
1
.054
are all valid numbers
but
cin >> n
and giving n a value of 1.23 should spit an error message.

---

### Post by CptPicard on 2009-02-08
Nope, you can't declare ranges like that beforehand, you need to explicitly check in code.

EDIT: Although you could technically write yourself some sort of number class that contains these sorts of range guards, and then you'd just pass in the limits in the constructor...

---

### Post by cguy on 2009-02-08
I already settled for a class. (which I wanted to avoid)
Thanks anyway.

---

### Post by CptPicard on 2009-02-08
For additional credit, make it a template class so you can use it on anything that has comparison operators ... so you can have

```

Ranged<float> x = Ranged<float>(0, 3.1415);

```

and then just throw an exception at violation of limits in assignment operator etc.

---

### Post by cguy on 2009-02-08
I'm getting stupid. Edited!

----

Good idea on using a template.

---

