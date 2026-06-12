---
title: "python real time plots of data using matplotlib"
date: 2012-06-09
forum: Programming Talk
---

### Post by brushman on 2012-06-09
I have data files that are continuously being updated as another program is run. I want to make plots of this data and continuously update my plots as data comes in using a python script and matplotlib.

Basically I did this by placing draw statements in a loop, but unfortunately this seems to be very limiting. I can't do anything with the graphs besides look at them as they appear. The buttons don't work, I can't resize, etc. Is there a better way of doing this? (also one of the graph annoyingly flashes but I think I can fix this later). I attached a snapshot of my plots as they are currently if that matters.

Thanks.

---

### Post by HarryTorry on 2012-06-10
I've done something similar to this before in Java, but this was a LONG time ago!
Anyway, I would set a loop to check the data file for an update (by checking the last modified time, from a loop and then if it's different to add the new data to the plot).

```
os.stat(filename).st_mtime
```

---

### Post by MadCow108 on 2012-06-11
> **HarryTorry said:**
> I've done something similar to this before in Java, but this was a LONG time ago!
Anyway, I would set a loop to check the data file for an update (by checking the last modified time, from a loop and then if it's different to add the new data to the plot).

```
os.stat(filename).st_mtime
```

the more modern way to do that would be using inotify or a similar event based pooling method to not wake up the cpu unnecessarily.

resizing and zooming seems to work for me using the wx backend and wxmpl
see the stripchart example in python-wxmpl
are you relinquishing control back to the event loop when you are pooling for new data?

---

