---
title: "Simple 3D plot in python"
date: 2009-05-14
forum: Programming Talk
---

### Post by elbarto_87 on 2009-05-14
Hi,

I was hoping one of the python users here might be able to make some suggestions for me.

I want to replicate the (arbitary) plot attached that was generated with this matlab script:
```

%Geometry between the nodes
x = [0 5 5 0 2.5];
y = [0 0 5 5 2.5];
z = [0 2.5 2.5 0 5];

lines = [1 2;2 3;3 4;4 1;1 5;2 5;3 5;4 5];%Lines between nodes

scatter3(x,y,z,'filled')%plot nodes
hold on
for i=1:length(lines)
    plot3(x(lines(i,:)),y(lines(i,:)),z(lines(i,:))) %plot each line
end
hold off

xlabel x
ylabel y
zlabel z
title 'Simple 3D Plot'
grid off
view(30,30)

```

The result is a pretty simple 3D plot, but I haven't found a python package that will let me make a plot like this. Matplotlib did have some* support in previous versions, but have pulled the support on 3D plotting for now. I thought I would try here first as I now there are a lot of python users in the community, so I am hoping for a few suggestions about what works for you.  

Thanks, Elbarto

---

### Post by mungewell on 2010-06-15
You could try plplot, which has python bindings.

They have commands to draw lines/polygons in a 3D plot:
[http://plplot.sourceforge.net/docbook-manual/plplot-html-5.9.6/plpoly3.html](http://plplot.sourceforge.net/docbook-manual/plplot-html-5.9.6/plpoly3.html)

Cheers,
Munge.

---

### Post by Calmor on 2010-06-16
Looks like there are some modules on the Python wiki that might do it:

[http://wiki.python.org/moin/NumericAndScientific/Plotting](http://wiki.python.org/moin/NumericAndScientific/Plotting)

Also, this guy talks about all kinds of Matlab-related Python modules that might help you.

[http://vnoel.wordpress.com/2008/05/03/bye-matlab-hello-python-thanks-sage/](http://vnoel.wordpress.com/2008/05/03/bye-matlab-hello-python-thanks-sage/)

Personally, I've just used Octave for most of what I needed to do for class, but never got into 3D plotting.  I don't know if it will handle it or not, but Octave is very similar to Matlab as far as syntax goes.

Good luck!

---

### Post by Calmor on 2010-06-16
P.S. - 

[http://www.scipy.org/Cookbook/Matplotlib/mplot3D](http://www.scipy.org/Cookbook/Matplotlib/mplot3D)

I think this is what you're looking for?

---

### Post by uOpt on 2010-06-16
Everybody hates GNUplot, but GNUplot does pretty much everything along those lines.

---

### Post by rrashkin on 2010-06-16
I'm not claiming this is great but it can be extended to do what you want.  I wrote it long ago in BASIC and have translated into each language I moved to since.  It plots a vector in 3D using GTK.

---

### Post by anton_09 on 2011-04-04
> **rrashkin said:**
> I'm not claiming this is great but it can be extended to do what you want.  I wrote it long ago in BASIC and have translated into each language I moved to since.  It plots a vector in 3D using GTK.


Could you please tell me more detail? I have a data file which contains 40 vectors each vector has three components x,y,z.
How can I use you code?
Thanks,

---

