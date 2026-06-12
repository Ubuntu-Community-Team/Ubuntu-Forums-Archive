---
title: "gnuplot surface with non-grid data"
date: 2013-03-25
forum: Programming Talk
---

### Post by mattia.tamellini on 2013-03-25
Hello everyone!


I have a problem that has been driving me mad for the whole day. Basically, I need to plot a 3D data series as a 2D heat map with GNUPlot.


If I had a structured mesh, I could arrange the output of my simulation like:
```
x_1   y_1   z_11
x_1   y_2   z_12
..
x_1   y_n   z_1n


x_2   y_1   z_21
..
x_2   y_n   z_2n


..


x_m   y_1   z_m1
..
x_m   y_n   z_mn
```


and then I could get what I want with
```
set terminal png
set output "out.png"
set view map
splot "grid_data.txt" with pm3d pal notitle 
```


(am I wrong?)


The problem is that my data are not arranged in a grid, since I do not have the same number of points for every x.


So I added the command "set dgrid3d" to the gnuplot script above in order to be able to plot non-grid data as a heat map. And here I get to my questions:
1) how should I arrange my data for such a plot? I am currently using this format:
```
x_1   y_1   z_1
x_2   y_2   z_2
x_3   y_3   z_3
x_1   y_1   z_1


x_4   y_4   z_4
x_5   y_5   z_5
x_6   y_6   z_6
x_4   y_4   z_4


...
```
(that is: I am dividing my data in blocks, with every block containing the coordinates of the vertices of every triangle in the mesh and the value of the solution in such vertex). Is that right or is there a better way?


2) the command "set dgrid3d" is particularly slow, and with a file of a million lines (roughly 50 MB) it fills up all of my RAM (8 GB) and freezes my laptop, forcing me to kill the process. Is there a faster way to plot non-grid data? Or am I doing something completely wrong, and this is not the way one plots non-grid data with gnuplot?


3) should I change software at all? :)


I'm starting to think that I have missed something about gnuplot.


Thanks a lot!!

---

