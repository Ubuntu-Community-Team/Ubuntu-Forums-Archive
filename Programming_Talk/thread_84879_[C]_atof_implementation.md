---
title: "[C] atof implementation"
date: 2005-11-01
forum: Programming Talk
---

### Post by scorpio2002 on 2005-11-01
Hi there! I'm new to programming and I'm studying C on the famous book by Kernighan and Ritchie. I was stuck at chapter 4 where the authors described an algorithm for evaluating a reverse polish string. 

The problem was that on my pc the algorithm returned a topsy-turby result instead of the right one. I've then found out what the problem was.

At first, like suggested by the book, I used the implementation of the function atof in <math.h>. Then, after some days of searching, I tried to use another implementation of atof belonging to <stdlib.h> and the algorithm worked fine. 

Now comes my question: why are there two different implementations of atof? and why does the one in math.h do anything but what's supposed to do?

thx,
Donato :-)

---

### Post by darth_vector on 2005-11-02
hi,

have a read of this: [http://docs.hp.com/en/B3782-90716/ch06s12.html](http://docs.hp.com/en/B3782-90716/ch06s12.html)

apparently atof used to be declared in math.h but, but is implemented in stdlib.h and hence there is only one implementation.

as to why the math.h function call does something... thats beyond me.

---

