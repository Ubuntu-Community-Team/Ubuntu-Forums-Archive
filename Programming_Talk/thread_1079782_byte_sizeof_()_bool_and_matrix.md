---
title: "byte sizeof () bool and matrix"
date: 2009-02-24
forum: Programming Talk
---

### Post by monkeyking on 2009-02-24
Hi, I got myself somewhat confused with this relative simple subject.

If I want to know how many megs a 2dim matrix of bools take of memory is this math correct

sizeof(bool) =1 //1byte

so a bool matrix of dim(500,2^15) would be

500*2^15
500* 32678 =  16384000

thats 16 megs? right?

thanks in advance

---

### Post by croto on 2009-02-24
sir, your math is impeccable.

---

### Post by geirha on 2009-02-24
If you use vector<bool> to store the booleans, then you can divide that by 8. [http://cplusplus.com/reference/stl/vector/](http://cplusplus.com/reference/stl/vector/)

---

### Post by mdurham on 2009-02-24
or would this work and be much safer?

bool array[SIZE1][SIZE2];

size = sizeof(array);

---

