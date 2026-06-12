---
title: "[Python, Matplotlib]Text on X-axis overlaps"
date: 2012-02-08
forum: Programming Talk
---

### Post by kramer65 on 2012-02-08
Hello,


I am creating a plot in Python using matplotlib and its [plot_date]("http://matplotlib.sourceforge.net/api/pyplot_api.html#matplotlib.pyplot.plot_date") function as follows (the resulting plot is attached below):
```
plt.figure(1)
plt.subplot(221)
plt.plot_date(date_line, numbers1, fmt='b-', tz=None, xdate=True, ydate=False, hold=None)
plt.plot_date(date_line, numbers2, fmt='r--', tz=None, xdate=True, ydate=False, hold=None)
# this 4 times for all the plots.
plt.close(1)
```
As you can see in the attached image, the dates on the X-axis overlap so that you can't read any of it anymore.

Is there a way to display only what fits? So for example only the first and the last date, or when the data spans several years display only the whole years, and not every day..

All tips are welcome!

---

### Post by MadCow108 on 2012-02-08
the usual way to handle dates on the axis is to angle them so more fit properly:
[http://matplotlib.sourceforge.net/examples/api/date_index_formatter.html](http://matplotlib.sourceforge.net/examples/api/date_index_formatter.html)
the example also shows how to distance the dates

you can also combine it tight_layout to get better automatic results with multiple plots (if your matplotlib is new enough)
[http://matplotlib.sourceforge.net/users/tight_layout_guide.html](http://matplotlib.sourceforge.net/users/tight_layout_guide.html)

---

### Post by kramer65 on 2012-02-10
Thanks madcow108!

autofmt_xdate() helped fixing the problem. In the attachement there is an example of how it looks now.

Have a beautiful day!

---

