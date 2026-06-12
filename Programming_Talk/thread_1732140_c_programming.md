---
title: "c programming"
date: 2011-04-17
forum: Programming Talk
---

### Post by polaris90 on 2011-04-17
HI, I have to do an assignment for my C programming class. I have to write a function that takes two arrays as arguments, calculates their discrete convolution and prints out the resulting function in 2 columns. It should do the calculation only for non-zero numbers. The problem is that I don't even know how a convolution works, i'm just taking calculus right now. The function is supossed to look like this
[code] void convolution(int array_1[x][y], int array_2[x][y])
[/code/

where the arrays are going to be input in the main function
can anybody help? I would appreciate it :)

If someone can explain me exactly how the convolution works, that would be great

---

### Post by Vaphell on 2011-04-18
[http://en.wikipedia.org/wiki/Convolution#Discrete_convolution](http://en.wikipedia.org/wiki/Convolution#Discrete_convolution)
it's pretty straightforward and look at this pic which shows the general rule
[http://en.wikipedia.org/wiki/File:Convolution3.PNG](http://en.wikipedia.org/wiki/File:Convolution3.PNG)

one range is fixed, second gets mirrored and slides against the first one
for each position matching values are multiplied and summed.

for 1 2 3 and 4 5 6 you'd get
```
1 2 3
      6 5 4
```
arrays don't overlap -> 0
```
1 2 3
  6 5 4
```
1 doesn't match anything so 1*0, 2 matches 4 so 2*6, 3*5, 4*0
value of convolution for that setup is 2*6 + 3*5
Set of sums is the result

---

