---
title: "Give me a hint please"
date: 2011-01-18
forum: Programming Talk
---

### Post by sum1nil on 2011-01-18
Hi. I need an algorithm that would take x items as input and then figure 
how many columns and rows it would take to display them all in a grid shaped like a square.

So, say if you have 512 points that you want to display as a rectangle
how many rows and columns would it take assuming something near a square? ty

Not asking for someone to do the coding (feel free)
but just a push in the right direction.

---

### Post by unknownPoster on 2011-01-18
You could check whether or not the number is a perfect square and then go from there.

---

### Post by NovaAesa on 2011-01-18
Find the square root, then take the floor and ceiling of that number. Then iterate upwards and downwards (simultaneously) on those numbers until one of them evenly divides the input. Once you have a divisor, simply divide the input by that divisor and you have the correct dimensions.

---

### Post by worksofcraft on 2011-01-18
> **sum1nil said:**
> Hi. I need an algorithm that would take x items as input and then figure 
how many columns and rows it would take to display them all in a grid shaped like a square.

So, say if you have 512 points that you want to display as a rectangle
how many rows and columns would it take assuming something near a square? ty

Not asking for someone to do the coding (feel free)
but just a push in the right direction.

If you want a square then square root is the function you want.

e.g. a chess board has 64 items (positions) and sqrt(64) = 8... so that means 8 columns x 8 rows..

Now if the number not is an exact square then you have some empty places e.g. sqrt(512) = 22.627... 23 x 23 = 529 will leave you with a few unused

OTOH if you want to make an exact rectangle... well it could degenerate to a single row if the number is a prime number... e.g there is no way to completely fill a grid with 13 items other than as one row/column of 13.

---

