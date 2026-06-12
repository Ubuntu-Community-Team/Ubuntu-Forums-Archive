---
title: "transparent plots in python matplotlib"
date: 2010-04-13
forum: Programming Talk
---

### Post by capybara! on 2010-04-13
Dear all, 

I am using the python bindings for matplotlib and need to plot three overlapping regions for a report:

```

import matplotlib.pyplot as plt
import scipy

seq = scipy.sin(range(0,10))
xpts = scipy.concatenate((range(0,10), range(0,10)[::-1]))
plt.figure()
for diff, color in zip([1,2,3], ["blue", "red", "yellow"]):
    ypts = scipy.concatenate((seq - diff, (seq - diff * 2)[::-1]))
    plt.fill(xpts, ypts, alpha=0.4, fc=color, ec="black", lw=2, label=str(diff))
plt.legend()
plt.show()

```


Works all very well, but it does not look good. It looks like 4 overlapping regions and not like 3, because red and yellow together give orange which looks like a separate region. 
I'll attach the bad looking figure.

Does anybody know a good color combination and good values for the transparancy parameter 'alpha' so the plot looks good and unambigious?

Any help is appreciated,

thanks in advance...

---

### Post by gmargo on 2010-04-13
I don't understand what your goal is.  If you don't want the colors to blend, then either don't overlap or use alpha=1.

---

### Post by capybara! on 2010-04-14
The problem is that my actual data does overlap and I have to show that somehow. If I use alpha=1, only the upper and lower bound of the region I plotted last is clearly visible. I am searching for a combination of colors and alpha values, so that the blending does not create too strong colors which then appear to be a distinct region...

---

