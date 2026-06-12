---
title: "Numpy array?"
date: 2009-09-04
forum: Programming Talk
---

### Post by filifunk on 2009-09-04
Lets say you want to plot in matplotlib from a csv file of historical stock data the 1st and 8th column on a graph.

I tried this and it didn't work:

```

figure()
plot(values[[:,0], [:,7]])
show()

```

---

### Post by jpkotta on 2009-09-04
> **filifunk said:**
> Lets say you want to plot in matplotlib from a csv file of historical stock data the 1st and 8th column on a graph.

I tried this and it didn't work:

```

figure()
plot(values[[:,0], [:,7]])
show()

```

Looks like your subscripting syntax is wrong.  You probably want something more like:
```

t = range(len(values[:,0]))
plot(t, values[:,0], t, values[:,7])

```

---

