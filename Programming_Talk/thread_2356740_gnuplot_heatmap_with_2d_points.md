---
title: "gnuplot heatmap with 2d points"
date: 2017-03-26
forum: Programming Talk
---

### Post by Canonon on 2017-03-26
Hello,
I basically want to draw 2d heatmap of rosenbrock function    f(x,y) = (a-x)^2  + b * (y-x*x) ^2     
and append some points (x,y) on this image.

Sample file with points looks as follows:

#x #y
15.00000 12.00000
8.00000 9.00000
...


I am trying to use multiplot to draw function with splot and points from file with plot and the thing is,
 gnuplot do not draw both data in the same coordinate system what can be seen on the following image:

[[IMG]https://s4.postimg.org/aj6j88cft/output.png[/IMG]]("https://postimg.org/image/aj6j88cft/")
[IMG]https://postimg.org/image/aj6j88cft/[/IMG]

What I want to do is just to put data from file correctly.


gnuplot code:

```

#!/usr/bin/env gnuplot
reset
set terminal png size 700,700
enhanced set output 'output.png'
set tmargin screen 1
set bmargin screen 0
set border 0 back
set size square
xr=20
yr=20
set xrange [-xr:xr]
set yrange [-yr:yr]
unset key #disablegraph name 
unset colorbox 
set surface
 set multiplot
set view map
set cntrparam levels 10# contour tenderness
set style data pm3d
set pm3d
set contour
a=1 #rosenbrock parameter
b=1 #rosenbrock parameter

#set isosamples 50
splot (a-x) * (a-x) + b * (y-x*x) * (y-x*x) # 2d rosenbrock
unset view
unset pm3d
plot 'data.dat' pt 5,           'data.dat'  using 1:2:($0+1) with labels offset 1 notitle

```

---

