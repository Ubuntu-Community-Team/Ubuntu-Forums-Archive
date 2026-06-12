---
title: "Dynamic graphs during Python run"
date: 2008-12-28
forum: Programming Talk
---

### Post by Gregory@Feanor on 2008-12-28
I want to plot data and view the graph while the program is running, and hence, while the data is changing.

I'm programming a genetic algorithm in Python and I want to view statistical data of each generation once it has been made. I want to see this while the program is running, not after it is completed.

I've looked around and I can find lots of libraries and extentions that plot data in a python program, but this seems to produce static graphs, as a picture file, after the program is complete. I want to see the graph (in a seperate window?) change as each new generation is made.

So after that long explanation, does anyone know something I could use? Thanks.

---

### Post by slavik on 2008-12-28
GTK/Qt, OpenGL are the three that come to my mind, not sure if Tk/Wx can do this, but GTK/Qt definately should be able to.

---

### Post by Gregory@Feanor on 2008-12-28
As I understand it GTK and Qt are for making GUIs, and OpenGL is for making 2D and 3D graphics.

I'm looking to make graphs. So I was hoping to use GnuPlot or Matplotlib or something similar to make them.

The problem with these is that all I can see them do is make a static graph of the results of a program, whereas I want to make a dynamic graph that will change as the variables are altered by the program, and view the graph as these variables are changing.

---

### Post by matja on 2008-12-28
I'm not a 100% sure I've understood your problem, but have you discovered the interactive mode of matplotlib?

```

import pylab
import random
import time


def main():
    pylab.ion()       # Turn on interactive mode.
    pylab.hold(False) # Clear the plot before adding new data.
    x = range(10)
    for i in range(10):
        y = random.sample(xrange(100), 10)
        pylab.plot(x, y)
        time.sleep(1)


if __name__ == '__main__':
    main()

```

This will avoid the call to pylab.show(), which blocks the program. You'll have to call pylab.plot (or whatever you use to produce your plot) for each new generation of your data, however, maybe that is what you wanted to avoid?

Regards, Mattias

---

### Post by imoccs on 2009-07-13
:guitar: Thanks very much~ That's what I want of dynamic ploting~

---

