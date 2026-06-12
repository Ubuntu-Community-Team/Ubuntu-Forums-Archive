---
title: "Please help(regarding until loop and ! operator)"
date: 2018-02-09
forum: Programming Talk
---

### Post by mak. on 2018-02-09
A ! has been put to reverse the less than condition so it becomes a greater than condition It loops until a becomes greater than 10. Why am I getting the output only till 9? It should reach 11, when its greater than 10, right? How do I fix this?

Code: 

[COLOR=#880000]#!/bin/bash[/COLOR]

a[COLOR=#666600]=[/COLOR][COLOR=#006666]0[/COLOR]

[COLOR=#000088]until[/COLOR] [COLOR=#666600][[/COLOR] [COLOR=#666600]![/COLOR] $a [COLOR=#666600]-[/COLOR]lt [COLOR=#006666]10[/COLOR] [COLOR=#666600]][/COLOR]
[COLOR=#000088]do[/COLOR]
   echo $a
   a [COLOR=#666600]=[/COLOR] [COLOR=#008800]`expr $a + 1`[/COLOR]
[COLOR=#000088]done[/COLOR]
Output: 
0
1
2
3
4
5
6
7
8
9

---

### Post by TheFu on 2018-02-09
But ! LT isn't a GT.  The opposite of LT is GE (greater than or equal).
 
I've never used an "until" in 25+ yrs of programming. Not once. Zero.

Also, in bash, you can increment a counter using (a++).  Much more efficient than the old-school way of calling an external program.

---

### Post by mak. on 2018-02-10
Thanks a lot.

---

