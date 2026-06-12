---
title: "measuing program run time with statistics"
date: 2010-02-02
forum: Programming Talk
---

### Post by ssam on 2010-02-02
i am interested in measuring run time of a program, can the effectiveness of optimisation flags.

the simplest method is just
```
time progname
```
but, this does not show the run to run variations.

next one could sum/average over several runs
```
time (for x in `seq 10`; do progname ; done )
```

but it would be better to know the mean and standard deviation run time. does anyone know of a existing program to do this? or should i make one myself. would other people find this useful?

---

### Post by ssam on 2010-02-03
here is a first attempt.

you can run:
```
timer.py -n10 programname
```
and it will run the program 10 times, and output mean and std deviation

---

### Post by lavinog on 2010-02-03
Should you ignore the first run because of caching?
Also would you want to redirect stdout to something besides the screen to reduce delays caused by screen refreshes?

---

### Post by ssam on 2010-02-04
thanks. i added those features and a few others.

```
Usage:
timer.py  [options] "progname args"
Options:
  -b, --baseline mean,stddev
  -l, --log logfile
  -n, --number NUMBER_OF_RUNS
    default: 10
  -p, --prerun yes/no
    Pre-run the program to warm caches
    default: yes
  -q, --quiet
    suppress program output
  -r, --ref refernce name (for logfile)
```

if you give a baseline, it will tell you the relative time. so you can run your code, and record the mean and stddev, then make a change, and run again to see the improvement. It shows the difference compared to the stddev (sigma), if this is less than 1 then the change is probably insignificant.

using log and ref, you can run the timer several times, and record the results eg:
```
#compile code with -O0
timer.py --log logfile --ref "O0" progname
#compile code with -O1
timer.py --log logfile --ref "O1" progname
...
```
then you can load the logfile into your favourite tool and plot graphs.

---

