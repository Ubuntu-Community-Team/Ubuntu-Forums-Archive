---
title: "[Python] How to plot multiple lines with plot_date() in matplotlib"
date: 2012-01-09
forum: Programming Talk
---

### Post by kramer65 on 2012-01-09
Hello,

I need to plot an image with two independent lines which I am trying to do with matplotlib. I have no trouble creating an image using two lines:

```
import matplotlib.pyplot as plt
import numpy as np
t = np.arange(0., 5., 0.2)
g = np.arange(0., 10., 0.4)
plt.plot(t, t, 'r--', t, g, 'bs')
```

I now want the x-axis to be a line of dates, so I need to use plot_date for that. I first created an image using only one line (using date2num to create the desired floats):

```
import matplotlib.pyplot as plt
import datetime
import matplotlib
dates_in_string = ['2010-01-01', '2010-01-02', '2010-02-03', '2010-04-05', '2010-07-19']
dates_datetime = []
for d in dates_in_string:
	dates_datetime.append(datetime.datetime.strptime(d, '%Y-%m-%d'))
dates_float = matplotlib.dates.date2num(dates_datetime)
list1 = [1,2,3,4,5]
plt.plot_date(dates_float, list1, linestyle='-', tz=None, xdate=True, ydate=False)
plt.show()
```
So far so good.

I now however, want to plot two lines using plot_date, and I don't seem to be able to get that working. I tried the following:
```
list2 = [1,2,4,8,16]
plt.plot_date(dates_float, list1, linestyle='-', dates_float, list2, linestyle='--', xdate=True, ydate=False)
```
and
```
list2 = [1,2,4,8,16]
plt.plot_date(dates_float, list1, linestyle='-', tz=None, xdate=True, ydate=False, dates_float, list2, linestyle='--', tz=None, xdate=True, ydate=False)
```
Both of these however, result in: *SyntaxError: non-keyword arg after keyword arg*

I wouldn' t really know what I am doing wrong here though. As far as I know I give all arguments correctly.

Does anybody have any idea how I could create two lines in one plot_date image?

---

### Post by kramer65 on 2012-01-10
Alright! I got it working!

After a while I found out that I shouldn't do it in one plot_date(), but that I can/need to do it two plot_date()'s.

So for future reference; I solved it like this:
```
import matplotlib.pyplot as plt
import datetime
import matplotlib
dates_in_string = ['2010-01-01', '2010-01-02', '2010-02-03', '2010-04-05', '2010-07-19']
dates_datetime = []
for d in dates_in_string:
   dates_datetime.append(datetime.datetime.strptime(d, '%Y-%m-%d'))
dates_float = matplotlib.dates.date2num(dates_datetime)
list1 = [1,2,3,4,5]
list2 = [1,2,4,8,16]
plt.plot_date(dates_float, list1, linestyle='-', xdate=True, ydate=False)
plt.plot_date(dates_float, list2, linestyle='-', xdate=True, ydate=False)
plt.show()
```

Cheers!

---

