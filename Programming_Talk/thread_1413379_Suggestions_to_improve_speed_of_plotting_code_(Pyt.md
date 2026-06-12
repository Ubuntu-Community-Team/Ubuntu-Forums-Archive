---
title: "Suggestions to improve speed of plotting code (Python/matplotlib)"
date: 2010-02-22
forum: Programming Talk
---

### Post by sprince09 on 2010-02-22
I'm writing some code for a robotics project that requires some plots of the robot. In a perfect world, I'd like 4 plots: 1 3D plot and 3 2D plots of the XYZ coordinates of all the joints in the robot. I'm trying to improve my Python coding skills, so I opted to do this project in Python rather than MATLAB which would have been by my usual first choice for a project like this. Anyway, I've got the plots drawing all nice and pretty (excluding the 3D plot, which I haven't tried to use yet), but now I'm looking to improve the speed of my code. I've traced the source of the slowness to my 'draw_plot' function:

```

# Setup plot data
        n = robot.n_joints+1
        s = np.max(np.sum(robot.a), np.sum(robot.d)) * np.array([-1, 1, -1, 1])
        s = s * 1.125
        
        x = robot.p[0,:].transpose()
        y = robot.p[1,:].transpose()
        z = robot.p[2,:].transpose()
        
        
        # Draw plots
        robot.plot_window = pyplot.clf();
        pyplot.subplot(221)
        pyplot.title('fixme: 3D plot goes here...')
        
        pyplot.subplot(222)
        pyplot.plot(x, y, color='blue')
        pyplot.plot(x, y, marker='o', color='blue')
        pyplot.plot(x[0,0], y[0,0], marker='o', color='black')
        pyplot.plot(x[n-1,0], y[n-1,0], marker='o', color='green')
        pyplot.axis(s)
        pyplot.title('X-Y')
        pyplot.xlabel('X')
        pyplot.ylabel('Y')
        
        pyplot.subplot(223)
        pyplot.plot(x, z, color='blue')
        pyplot.plot(x, z, marker='o', color='blue')
        pyplot.plot(x[0,0], z[0,0], marker='o', color='black')
        pyplot.plot(x[n-1,0], z[n-1,0], marker='o', color='green')
        pyplot.axis(s)
        pyplot.title('X-Z')
        pyplot.xlabel('X')
        pyplot.ylabel('Z')
        
        pyplot.subplot(224)
        pyplot.plot(y, z, color='blue')
        pyplot.plot(y, z, marker='o', color='blue')
        pyplot.plot(y[0,0], z[0,0], marker='o', color='black')
        pyplot.plot(y[n-1,0], z[n-1,0], marker='o', color='green')
        pyplot.axis(s)
        pyplot.title('Y-Z')
        pyplot.xlabel('Y')
        pyplot.ylabel('Z')
        
        # Re-draw plot
        pyplot.ion()
        pyplot.draw()


```


The above function gets called inside a loop, end executes far slower than any other function in my program (~.3 to ~.5 seconds compared to <.01 seconds!), so it significantly slows down the program. I've implemented schemes like this in MATLAB before without this sort of slow down, so I'm wondering if anyone could offer some suggestions to help improve the speed of this function.

---

### Post by LKjell on 2010-02-22
You can use vectorization by defining a function. There are no loops. Just make a range beforehand then call the function with that range.```
#for easyviz plotting. Can use matplotlib as backend.
#the advantage is that you have matlab like syntax
from scitools.std import *

#if you do not have scitools numpy works as well
from numpy import *

x = linspace(0,5,100)
#or this.. There are plenty.. But you cannot have a list
x = array([0.1*i for i in range(50)])

def so(x):
	return x*x

y = so(x)

print y

```

---

### Post by sprince09 on 2010-02-22
Well, it's not really the calculation in the for loop that's slowing me down... it's the act of updating the plot window.

I suppose a more apt description of my problem is something like this:

```


for t in timespan:
    t += dt
    x = some_func(x)
    
    update_plot(t, x)
    

```

What I gave before was just the 'update_plot' part of the program. The actual calculations to obtain 'x' is nonlinear in 't' and so, from my understanding of vectorization, 'x' is non-vectorizable with respect to 't' (I've tried in the past :( ). 

What I'm more interested in are ways to instruct matplotlib to only re-draw the parts of the plot that have changed, similar to the 'replace-children' option in MATLAB's plot interface.

---

### Post by sprince09 on 2010-02-22
Digging around the matplotlib documentation led me to this page which seems to be what I'm looking for:

[http://matplotlib.sourceforge.net/examples/animation/index.html](http://matplotlib.sourceforge.net/examples/animation/index.html)

---

### Post by LKjell on 2010-02-22
I am not familiar with matplotlib since I use the frontend of it. But in easyviz you can disable all plot showing and spesific showing one when you want to. That way plotting goes much faster. Otherwise be patience I guess. Do not thing python support multi threading..

[http://code.google.com/p/scitools/wiki/EasyvizDocumentation](http://code.google.com/p/scitools/wiki/EasyvizDocumentation)

---

