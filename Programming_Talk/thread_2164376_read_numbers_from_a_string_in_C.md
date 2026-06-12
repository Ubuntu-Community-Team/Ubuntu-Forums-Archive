---
title: "read numbers from a string in C"
date: 2013-07-31
forum: Programming Talk
---

### Post by zazzle on 2013-07-31
I'm now writing a C program that read 2 line of strings from the screen like this:
```
2x + 3y = 1
3x + 5y = 2
```
and judge if the 2 equation is parallel or intersecting. 
I know the algorithm but i don't know how to get the coefficient from the equations. 
note that the input format may vary like 2*x + 3*y = 1.
need help, thank you!

---

### Post by ofnuts on 2013-07-31
Use regular expressions: [http://stackoverflow.com/questions/1085083/regular-expressions-in-c-examples](http://stackoverflow.com/questions/1085083/regular-expressions-in-c-examples)

Regular expression would be something like

```

(\d+(\.\d+)?)\*?x\s*[+-]\s*(\d+(\.\d+)?)\*?y\s*=\s*(\d+(\.\d+)?)

```
(not the full regexp to support all cases... )

---

### Post by Bachstelze on 2013-07-31
Also, do you really need to do this in C?

---

