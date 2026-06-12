---
title: "Group arrays in octave"
date: 2009-10-22
forum: Programming Talk
---

### Post by RocketRanger on 2009-10-22
Hi

I currently have this problem in octave where I would like to group arrays together, like an array of arrays in c.

I would like to do something like:
b = [1, 2, 3]
a(2) = b

Hope you can help.

---

### Post by 80aless on 2009-10-22
I am a matlab user, but it shoould be about the same. 
I think what you are looking for are the cells: 

b = [1, 2, 3]
a={'a',b}
Then you can do a{1} and a{2} to obtain 'a' and [1, 2, 3] respectively. 
you cannot make arrays of arrays

---

### Post by RocketRanger on 2009-10-22
Thank you! That was it exactly.

Just wondering if the reason there aren't arrays of arrays are a mathematical one because the cells accomplish this function perfectly?

---

### Post by 80aless on 2009-10-22
>Just wondering if the reason there aren't arrays of arrays are a >mathematical one because the cells accomplish this function >perfectly? 

If I understand you correctly: cells and arrays are different things. arrays are matrices (of numbers), cells are collection of objects as numbers, strings, structs. So probably the arrays of arrays in c are the equivalent of the cells in Matlab/Octave. Consider also that Matlab/Octave are based on matrices, so I suppose it is important that arrays are distinct from a collection of objects as the cells. 
In addition, let's say that you have an e.g. 2x2 array, and you try to put a 3x1 column in the first element; Then you would not obtain a **mathematically** representable matrix anymore, because the columns one and two would be of different length (4 and 2, respectively).
Hope it helps

---

