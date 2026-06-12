---
title: "fortran and plotting?"
date: 2006-12-10
forum: Programming Talk
---

### Post by neoflight on 2006-12-10
hi

is there any good plotting (2D ad 3D) library for fortran. i mean easy to use ...intuitive like that of matlab? 

if yes..how would i use the library? i mean where would i put it...i have intel 90 compiler installed..thank you...

---

### Post by &lt;mawe&gt; on 2006-12-10
Hi!

I guess the most popular for Fortran is [pgplot](http://www.astro.caltech.edu/~tjp/pgplot/). It's easy to use, but only 2D. The other one I know is [DISLIN](http://www.mps.mpg.de/dislin/) which can do 2D and 3D. Can't say if its easy to use, but the examples on their homepage don't look too complex :)

Hope this helps.

PS: I don't really use Fortran for plotting. I calculate data with it, and plot with some other program, mostly Gnuplot or matplotlib (a Python library). For 3D simulations I like VPython ;)

Regards, mawe

---

### Post by neoflight on 2006-12-10
> **<mawe> said:**
> Hi!

I guess the most popular for Fortran is [pgplot](http://www.astro.caltech.edu/~tjp/pgplot/). It's easy to use, but only 2D. The other one I know is [DISLIN](http://www.mps.mpg.de/dislin/) which can do 2D and 3D. Can't say if its easy to use, but the examples on their homepage don't look too complex :)

Hope this helps.

PS: I don't really use Fortran for plotting. I calculate data with it, and plot with some other program, mostly Gnuplot or matplotlib (a Python library). For 3D simulations I like VPython ;)

Regards, mawe

thank you... after reading i was thinking of the same. write to a txt file and plot using gnuplot or xls....thanks

---

### Post by junglepeanut on 2006-12-11
fortranposix creates a call for gnuplot library kinda of thing.

---

