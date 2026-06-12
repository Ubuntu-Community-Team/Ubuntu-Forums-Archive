---
title: "Overloading [] to allow modification. (C++)"
date: 2009-02-17
forum: Programming Talk
---

### Post by mrbiggbrain on 2009-02-17
i want to do something similar to how you can...

int a[4]
a[0] = 5;

however with a custom class. iv already overloaded the [] operator to read, how do i add it so i can also use other operators +, -, =, ect.

```
double operator[] (int number)
            {
                   return line_length[number];
            }

```

currently that's all i have, it simply outputs the line so calling

cout << core1[1];

displays the length of side 2 on my console window.

can anyone help me, id like to be able to set things like

```
core[0] = 1;
core[1] = 2;
core[2] = 2;
```

thanks in advance

---

### Post by Npl on 2009-02-17
return a reference to a double ( double& operator[] (int) ), then you can modify it.

If you want a ready to use class, look at STL`s map

---

### Post by mrbiggbrain on 2009-02-17
> **Npl said:**
> return a reference to a double ( double& operator[] (int) ), then you can modify it.

If you want a ready to use class, look at STL`s map

perfect! sorry to be a total, noob... iv spent a few years trying my hardest to avoid pointers. so i wasnt aware of how to call a refrence, or that wou could.  but its all wroking now, and i learned something i know i can apply to my every day tasks, thanks again

---

