---
title: "Weird C problem"
date: 2010-05-24
forum: Programming Talk
---

### Post by ibarash on 2010-05-24
Hello,
Sorry for my not so good english
 
I am taking a C programing course in my university and got an exercise.
 
I created an header which has:
```

#define SIZE 4
typedef double mat[SIZE][SIZE];

```
 
and declared 6 global matrixs:
```

mat mat_a, mat_b, mat_c, mat_d, mat_e, mat_f, mat_g;

```
 
but, when i insert values into mat_b, it somehow affects mat_a (starting at line 2).
i insert values to mat_c and it starts from line 3 in mat_a, and affects line 1 in mat_b.
 
I just dont get it.
oh, it works just fine under windows.
 
Please help me....

---

### Post by lisati on 2010-05-24
It sounds to me like a problem with a rogue subscript that's causing your program to access memory outside the range assigned to the array you wish to update. Without seeing more of your code.....

---

### Post by ibarash on 2010-05-24
OK,
thanks
 
and how do i fix it?

---

### Post by Tony Flury on 2010-05-24
Without seeing your code we can't tell you have to fix it, but since your arrays are double[4][4]
you must ensure that your subscripts into any array of this type is between 0 and 3 - any subscript lower than 0 or greater than 3will cause problems not unlike the ones you are seeing.

Depending on how the arrays are arranged in memory - then it is quite possible that access saying mat_b[4][4] might actually overwite something in mat_a - and since the problems are dependent on a OS specific choice - i.e. how to arrange variables in memory - then it is quite possible that your code "works" under one OS, and not in another.

Notice i put "works" in inverted commas deliberately. If you are going outside your array bounds under windows and the program is not misbehaving, it is not because it works, it is because you are being lucky - most security bugs in most OS's are due to memory overruns exactly like you have here.

---

