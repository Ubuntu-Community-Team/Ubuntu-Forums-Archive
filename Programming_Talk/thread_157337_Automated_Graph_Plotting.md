---
title: "Automated Graph Plotting"
date: 2006-04-08
forum: Programming Talk
---

### Post by krypto_wizard on 2006-04-08
My python program spits lot of data. I take that data and plot graphs using OfficeOrg spredsheet. I want to automate this task as this takes so much of time. I have some questions.

1. which is the best graph plotting utility in linux. I know little about gnuplot. If you know any better tool without much learning curve please tell me.

2. I want to write a script such that my python code writes to a file, some graph utility like gnuplot takes that data from the file and I get my graph ready made. Do you think its possible ?

Any feedback regarding above is appreciated.

Thanks

---

### Post by hod139 on 2006-04-10
Gnuplot is the way to go.  There are a ton of tutorials available too.  Here is an example file I have laying around to create a png for a plot of position versus time from a datafile called EXAMPLE5.1.  Time is column 1, position is column 2
```

set terminal png
set output "q1plot.png"
set title "Plot of q1(t) for Problem 1"
set xlabel "Seconds"
set ylabel "Meters"
unset key
plot "EXAMPLE5.1" u 1:2 t "q1(t)" w lines

```
A quick google search will find many tutorials for more advanced stuff.

---

### Post by Kresten Kjaer on 2006-04-10
Well, since it is in python already. Why not use matplotlib ?
[http://matplotlib.sourceforge.net/screenshots.html](http://matplotlib.sourceforge.net/screenshots.html)
It is great for graphs, you can view some source on that page too. Its a great plotlib.

---

### Post by xtan on 2011-04-13
Take a look at DataScene ([http://www.cyber-wit.com](http://www.cyber-wit.com)). Its data monitoring feature might be useful to your applications.

---

### Post by Iowan on 2011-04-13
Closed!

Hopefully, they've found a solution in the last five years.

---

