---
title: "Pylab and function plotting"
date: 2006-10-26
forum: Programming Talk
---

### Post by TitusDalwards on 2006-10-26
```

from scipy import *
from pylab import *
t=arange(0.0,3.0,0.05)
s=sin(2*pi*t)
plot(t,s)
show()
```

with these codes i can plot a simple sinus graphic, lets thing i have a polynom like this:
p=poly1d([1,2,3]) and i want to plot it like sinus but i can't do this.

If you have any idea could you please share with me.

---

### Post by earth_walker on 2007-08-21
A little late, but here's how you'd do it.
```
>>> p = poly1d([1,2,3]) #This defines a function instance
>>> p
poly1d([1, 2, 3])
>>> x = range(10)                     # An array from 1 to 10
>>> x
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> y = p(x)                              # Call the function for x
>>> y
array([  3,   6,  11,  18,  27,  38,  51,  66,  83, 102])
>>> plot(x,y)

```

Basically, poly1d defines a function, and so you need to still generate the x values and f(x) values to plot. 

Another tip - matplotlib uses seperate arrays of x and y (and z) data for most of its plot types, and so if your data is in ordered pairs you'll need to reshape it.

For example:
```

>>>data = [(1,1), (2,2), (3,3)]
>>>data_for_pylab = [[data[i][0] for i in range(len(data))], [data[j][1] for j in range(len(data))]]

>>># now you can either separate the data into x,y:
>>>x,y = data_for_pylab
>>> x
[1, 2, 3]
>>> y
[1, 2, 3]
>>>plot(x,y)

>>># or you can use the * operator to send each element of the dataset seperately
>>>plot(*data_for_pylab)


```

The matplotlib cookbook examples from their website are very useful.

EW

---

