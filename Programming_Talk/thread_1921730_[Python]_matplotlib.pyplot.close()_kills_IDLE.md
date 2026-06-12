---
title: "[Python] matplotlib.pyplot.close() kills IDLE?"
date: 2012-02-07
forum: Programming Talk
---

### Post by kramer65 on 2012-02-07
Hello,


I need to create some graphics using matplotlib. I set up a little test-script for this as follows:
```
import matplotlib
import matplotlib.pyplot as plt
import datetime
datums_in_string = ['2010-01-03', '2010-03-08', '2010-03-30', '2010-04-01', '2010-09-19']
datums_datetime = []
for datum in datums_in_string:
    datums_datetime.append(datetime.datetime.strptime(datum, '%Y-%m-%d'))

datums_float = matplotlib.dates.date2num(datums_datetime)
lijn1 = [2,4,6,8,10]

plt.figure(1)
plt.plot_date(datums_float, lijn1, fmt='b-', tz=None, xdate=True, ydate=False, hold=None)
plt.savefig('grafiek1.png', format=None, dpi=None)
#plt.close(1)

```

This works perfectly well. Since I am going to create a lot of different plots within that script I do want to close every plot before creating a new one. That is why I included the last line (which is currently commented out). When I uncomment that line (to close the plot), IDLE immediately halts with some error, which I am unable to read, because IDLE also immediately closes after the error occurs.

I wouldn't know why this closing of the figure would kill IDLE altogether? Would anybody know what I am doing wrong here?

([SIZE="1"]I am running on Ubuntu 11.10 with Python 2.7.2 with all software installed from the repositories.[/SIZE])

---

