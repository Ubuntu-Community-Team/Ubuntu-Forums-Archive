---
title: "BASH Total CPU Percentage"
date: 2012-11-16
forum: Programming Talk
---

### Post by eklikeroomys on 2012-11-16
Hi,

I've been searching for a neat way of finding the total instantaneous CPU usage as a %, and found all sorts of tedious solutions.

I thought I'd share a simple one-liner that accomplishes the task really simply:

```
 top -bn 1 | awk '{print $9}' | tail -n +8 | awk '{s+=$1} END {print s}' 
```

Basically, it grabs the CPU column from top and sums all the values together. Simple as that.

Enjoy!

---

### Post by Habitual on 2012-11-16
very slick. :)

---

### Post by Vaphell on 2012-11-16
this will do the same
```
top -bn 1 | awk 'NR>7{s+=$9} END {print s}'
```

imho that code shows wrong number, you have to divide by number of cores.
in my case system monitor shows approx: 20/20/10/10
code: 60
```
top -bn 1 | awk 'NR>7{s+=$9} END {print s/4}'
```

why not print the 3rd line where 'ingredients' of CPU load are listed?
```
top -bn 1 | sed -n 3p
```
or assuming cpu load = 100% - idle%
```
top -bn 1 | awk 'BEGIN{FS="[ \t%]+"} NR==3{ print 100-$8 }'
```

---

### Post by eklikeroomys on 2012-11-16
I agree that dividing by the number of CPUs will give the actual percentage of total CPU usage if you have more than one core. Thanks!

---

