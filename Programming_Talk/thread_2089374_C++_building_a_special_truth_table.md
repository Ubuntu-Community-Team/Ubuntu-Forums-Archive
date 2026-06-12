---
title: "C++: building a special truth table"
date: 2012-11-29
forum: Programming Talk
---

### Post by erotavlas on 2012-11-29
Hi,
I would like to generate a "truth table" in which are  present only certain configurations. If I have two variables x,y of cardinality 2,3 then I need  to build the truth tables as: 

```

x
0 1 
1 0
y
0 0 1
0 1 0
1 0 0

```
The final truth table is the composition of the previous: 

```


xy
0 1 0 0 1
0 1 0 1 0
0 1 1 0 0
1 0 0 0 1
1 0 0 1 0
1 0 1 0 0

``` I thought about a  variable number of nested loop to build the table. Do you have suggestions? Thank you for help.

---

### Post by dwhitney67 on 2012-11-29
And I would love to get rewarded for every time someone asks for help with their school work.

---

