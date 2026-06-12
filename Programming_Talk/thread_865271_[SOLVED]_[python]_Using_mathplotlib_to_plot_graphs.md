---
title: "[SOLVED] [python] Using mathplotlib to plot graphs against time"
date: 2008-07-20
forum: Programming Talk
---

### Post by durand on 2008-07-20
I've posted this on the python mailing list but I didn't get many replies. I'm a bit confused as to how to plot a graph of a variable against the date/time. I did get this:

[PHP]import pylab, random 
from datetime import datetime, timedelta 

today = datetime.now() 

dates = [today + timedelta(days=i) for i in range(10)] 
values = [random.randint(1, 20) for i in range(10)] 
pylab.plot_date(pylab.date2num(dates), values, linestyle='-')
[/PHP]

...from arsyed on the python mailing lists but it doesn't really work for a list of dates...I'm not even sure what format to list dates as. In this example, the dates are generated but I need to use real data which can't be generated. Any ideas?

Thanks.

---

### Post by WW on 2008-07-20
Have you already seen the "Plotting dates" section of [this tutorial](http://matplotlib.sourceforge.net/tutorial.html)?  (It's near the end.)

---

### Post by durand on 2008-07-20
Yeah, I have but I have no idea what this bit means:
[PHP]date1 = datetime.date( 1952, 1, 1 )
date2 = datetime.date( 2004, 4, 12 )
delta = datetime.timedelta(days=100)
dates = drange(date1, date2, delta)[/PHP]

EDIT: Well, the delta bit anyway...

---

### Post by durand on 2008-07-20
Nevermind, arsyed solved it:

[PHP]import dateutil, pylab

datestrings = ['2008-07-18 14:36:53.494013','2008-07-20 14:37:01.508990', '2008-07-28 14:49:26.183256']
dates = [dateutil.parser.parse(s) for s in datestrings]
pylab.plot_date(pylab.
date2num(dates), values, linestyle='-')[/PHP]

---

