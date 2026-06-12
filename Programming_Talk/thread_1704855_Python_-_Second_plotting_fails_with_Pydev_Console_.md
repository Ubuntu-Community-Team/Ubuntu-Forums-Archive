---
title: "Python - Second plotting fails with Pydev Console with pyplot"
date: 2011-03-11
forum: Programming Talk
---

### Post by mehmet.ali.anil on 2011-03-11
Hi!

I'm using Eclipse with PyDev in order to code a simulation. 
In this simulation I have a 2D array of bits that I want to visualize using matplotlib.pyplot the code that I'm using for that, stripped down, 

     plt.imshow(num.array(self.state),cmap='grayscale')
     plt.show()

pylab being imported as:

import numpy as num
import networkx as nx
import matplotlib.pyplot as plt

But regardless of the fact that which model calls plt.show(), only the first figure is displayed within a window, when I close that window and call show() again, the figure is not plotted.

This happens on Pydev console. Within command line, subsequent plotting works like a charm.

---

