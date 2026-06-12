---
title: "renaming files with sed"
date: 2007-04-05
forum: Programming Talk
---

### Post by moimies on 2007-04-05
I have thousands of irc log files, named channel-DD-MM-YYYY. I found out (after years of logging :)) that this isn't the best way to sort log files, so I want now rename my files.

The new naming would be YYYY-MM-DD-channel. How to extract YYYY into variable YEAR, MM into variable MONTH and so on, so I can rename files with bash script? I thought sed would do that, but I don't know how to use it.

---

### Post by bashologist on 2007-04-05
Something like this maybe?
for L in *; do L="${L: -11}"; echo "${L:7}${L:3:4}${L:1:2}"; done

If that gives the output you're looking for then you could use mv:
for i in *; do L="${i: -11}"; mv -i "$i" "${L:7}${L:3:4}${L:1:2}"; done

---

### Post by WW on 2007-04-05
Use **rename**, e.g.
```

$ rename 's/(.*)-(.*)-(.*)-(.*)/$4-$3-$2-$1/'  *

```
(I assume that the channel doesn't contain a dash.)

---

### Post by frodon on 2007-04-05
Thanks WW, i didn't know rename and in addition it supports regular expressions, just great ! i'll use it in some scripts for sure :) 
Till now i always did that through perl but rename is far more quick and easy.

---

### Post by moimies on 2007-04-06
Thanks, I didn't know rename either. It worked like a charm! :)

---

### Post by lapique on 2011-07-29
> **bashologist said:**
> Something like this maybe?
for L in *; do L="${L: -11}"; echo "${L:7}${L:3:4}${L:1:2}"; done

If that gives the output you're looking for then you could use mv:
for i in *; do L="${i: -11}"; mv -i "$i" "${L:7}${L:3:4}${L:1:2}"; done

If you don't have rename like in the Mingw shell on Windows, sed can come in handy. Here is how I use it. You can use all the power of your imagination and of the regexp.
```

for f in *.csv; do fn=`echo $f|sed "s/-/_/g"`; mv $f $fn; done

```The previous example replaces '-' with '_' in a set of files. fn contains the new file name. If f or fn have spaces, you must enclose them in double quotes in the mv command.

Before :
```
thermoUsb-20070824.csv  thermoUsb-20070827.csv  thermoUsb-20070830.csv
thermoUsb-20070825.csv  thermoUsb-20070828.csv
thermoUsb-20070826.csv  thermoUsb-20070829.csv
```After:
```
thermoUsb_20070824.csv  thermoUsb_20070827.csv  thermoUsb_20070830.csv
thermoUsb_20070825.csv  thermoUsb_20070828.csv
thermoUsb_20070826.csv  thermoUsb_20070829.csv
```

---

