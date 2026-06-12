---
title: "Finding Neighbors in a Two-Dimensional Array"
date: 2008-07-09
forum: Programming Talk
---

### Post by Billy the Kid on 2008-07-09
I have been trying to find the "neighbors" of certain elements within a two-dimensional array.  For example, in the array listed below, the neighbors of 'F' would include 'G', 'K', 'J', 'I', 'E', 'A', 'B' and 'C'.

```
char[][] example = {
        { 'A', 'B', 'C', 'D' },
        { 'E', 'F', 'G', 'H' },
        { 'I', 'J', 'K', 'L' },
        { 'M', 'N', 'O', 'P'}
    };
```

The solution I'm seeking does _not_ require "wrapping" of the neighbors but I still can't figure how to do it without a gigantic if..else ladder, which is obviously impractical.  Any algorithms, explanations, psudo-code or example code that can solve this problem would be greatly appreciated.

Thanks, Billy

---

### Post by CptPicard on 2008-07-09
Well, for anything at coordinates (i,j), neighbours are of course (i-1,j), (i-1,j-1), (i,j-1)... and so on, with appropriate bounds-checking.

---

### Post by Can+~ on 2008-07-09
The neighbors of a matrix (m x n), is just a submatrix (where i, j is the position of the desired element):

```

[ (i-1, j-1) (i, j-1) (i+1, j-1) ... ]
[ (i-1, j).. (i, j).. (i+1, j) ..... ]
[ (i-1, j+1) (i, j-1) (i+1, j+1) ... ]
[ .................................. ]
```

and removing the middle element (i, j) from it.

And if you're doing the task on C, make sure you don't go off the bounds (checking if the i-1, or j-1 is negative and i+1 and j+1 are smaller than the m, n.

---

### Post by Billy the Kid on 2008-07-09
Thanks for the quick reply CptPicard!

"Well, for anything at coordinates (i,j), neighbours are of course (i-1,j), (i-1,j-1), (i,j-1)... and so on, with appropriate bounds-checking."

Yes, but it seems that bounds checking requires more conditional statements than necessary.  Are there any easier methods?

---

### Post by Billy the Kid on 2008-07-09
Thanks both of you!  Can+~, your post cleared things up; I just completely overlooked the submatrix concept because I was imagining it returning a single value!  In retrospect, I have no idea where that notion came from.  If I had written a separate method for it from the beginning, I think I would have realized how silly that was.  Thank you both.

---

### Post by Tony Flury on 2008-07-10
Since you seem to be writing in C or C++, you can always use the conditional operators instead of if then else to do your bounds checking :

```

// Assume rootX and rootY are already defined
// as are maxX and maxY (the upper bounds of your array)

int minSubX = ((rootX -1) < 0) ? 0 : rootX -1 ;
int minSubY = ((rootY-1) <0) ? 0 : rootY -1 ; 
int maxSubX = ((rootX +1) > maxX) ? maxX : rootX +1 ;
int maxSubY = ((rootY+1) >= maxY) ? maxY : rootY +1 ;

for (int pX = minSubX ; px <= maxSubX ; px ++)
{
    for (int pY = minSubY ; px <= maxSubY ; py ++)
    {
      processNeighbour( pX, pY, rootX, rootY); 
    }
} 

```

I should say that I neither compiled or tested this code but it should work - fingers crossed.

---

