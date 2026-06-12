---
title: "Python's Matplotlib Not Displaying Plots"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by AustenG on 2012-05-16
Hey, 

I've recently upgraded to 12.04, and I'm trying to get Enthought Python (v 7.2.2) to work. I've installed it and everything seems to be working well, except I got the error that wxpython needs to be version 2.8 or higher. I found a post telling me to comment out the line in matplotlibrc having to do with the backend, and voila, I was able to import pylab and matplotlib.pyplot successfully. The only thing is, now no plots will actually show up. 

```

from pylab import *
plot(1,1,"ro")
show()

```
This just gives me nothing (no errors, warnings, or anything else).

Can anyone actually explain to me what a backend is, and why commenting the one line in matplotlibrc file allows me to import the modules but not show plots?

Thanks a bunch!

---

### Post by diesch on 2012-05-16
The backend is the system that is used to display plots. If it is set to something that doesn't work on your system you may get an error when importing the module.

Try one of the backends GTK,  Qt4Agg or TkAgg

---

### Post by AustenG on 2012-05-17
Thanks! TkAgg was the solution. Apparently there are a few copies of matplotlibrc on my system, but the one that did it for me was in:

```
~/epd-7.2-2-rh5-x86_64/lib/python2.7/site-packages/matplotlib/mpl-data
```

Cheers, 
~Austen

---

