---
title: "help with boxplots in pylab"
date: 2009-04-01
forum: Programming Talk
---

### Post by magnus86 on 2009-04-01
Hello.
I've been trying to work out how to change the color of a boxplot in pylab. by default the box is blue, but I want to change it to red.
I've been looking for a way to do this, however I've been unable to find anything.
I was wondering if anyone had any suggestions of how to do this?

---

### Post by WW on 2009-04-02
boxplot() returns a dictionary.  The keys correspond to different parts of the boxplot, and the values are lists of Line2D objects.  Here is an example that shows how you can manually set the attributes of different parts of the boxplot:
```

from numpy.random import randn
from pylab import boxplot, show


# Create some random data for the boxplot.
x = randn(20,5)

b = boxplot(x)

# Change the box lines to red, with linewidth 2.
boxlines = b['boxes']
for line in boxlines:
    line.set_color('r')
    line.set_linewidth(2)

# Change the median lines to green, with linewidth 2.
medlines = b['medians']
for line in medlines:
    line.set_color('g')
    line.set_linewidth(2)

show()

```

---

### Post by magnus86 on 2009-04-02
Aha!
Thank you :).

---

