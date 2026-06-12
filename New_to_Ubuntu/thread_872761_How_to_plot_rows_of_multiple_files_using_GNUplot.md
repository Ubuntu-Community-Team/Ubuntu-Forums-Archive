---
title: "How to plot rows of multiple files using GNUplot"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ahjiefreak on 2008-07-28
Hi,

I have multiple files such as file1.txt file2.txt......file100.txt
Each of this having 10 rows of data. Basically I wanted to plot 
graph for each row from file1 to file100. In other words, i would have 10 graphs which each of them have 100 line-graphs. 

My basic data e.g is something like below:-

File1.txt 
v1 28 14 1.72414 1.72414 1.72414 1.72414 1.72414
v2 77 7 7.47126 6.89655 7.47126 6.89655 6.89655
v3 156 3 21.2644 21.2644 20.6897 21.2644 20.6897
v4.........

...
v10

file2.txt
v1 160 1 20.6897 20.6897 20.6897 20.6897 20.6897
v2 154 5 8.62069 8.62069 8.62069 8.62069 8.62069
v3 43 1 1.72414 11.4943 1.72414 1.72414 11.4943
v4 .........

...
v10

The same goes for other files.I wanted to plot for each graph having v1 data where y-row points are from column 4 to column 8 with respect to default x-row of 10%,20%,30% ,40%and 50%. 

I tried to use  plot '<grep -w v1 File*.txt' using 1:2 but it is giving me error. This is because the 1:2 is incorreclty used. I am not sure how to represent and plot this graph automatically using gnuplot. By using hand to plot for 100 files would be impossible.

Please advise. Appreciate alot. Thanks.


Rgrds,

---

### Post by beren.olvar on 2008-07-28
I would try doing a shell script like this one:
```

#!/bin/bash

for i in `seq 1 100`; do
name="plot${i}.eps"

gnuplot << EOF
set terminal postscript color
set out $name

set xtics ("10" 1, "20" 2, "30" 3, "40" 4, "50" 5)
plot "<grep v1 file$i.txt|cut -d' ' -f4-" matrix w l

EOF
done


```

but if you can rewrite the text files i would advice to change the way you write your data if you are going to need to do more plots
normally

x1 y1
x2 y2
x3 y3

x1' y1'
...

is easier to use with gnuplot

cheers!

EDIT: ups! not what you need, but at least the "cut" and "matrix" part works well, try using it with the method you are using.

---

