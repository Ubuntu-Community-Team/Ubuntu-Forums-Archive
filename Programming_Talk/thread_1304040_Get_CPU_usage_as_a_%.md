---
title: "Get CPU usage as a %"
date: 2009-10-28
forum: Programming Talk
---

### Post by H4F on 2009-10-28
> **jerome bettis said:**
> ^ that won't give you an accurate measure.

i wrote a python script for someone a while ago to do this.  i read some stuff on how to calculate it.  i'm 100% sure this is correct - i adapted it from a C program someone who knows what they're talking about wrote.

[php]#!/usr/bin/env python

import time

TIMEFORMAT = "%m/%d/%y %H:%M:%S"
INTERVAL = 2

def getTimeList():
    statFile = file("/proc/stat", "r")
    timeList = statFile.readline().split(" ")[2:6]
    statFile.close()
    for i in range(len(timeList))  :
        timeList[i] = int(timeList[i])
    return timeList

def deltaTime(interval)  :
    x = getTimeList()
    time.sleep(interval)
    y = getTimeList()
    for i in range(len(x))  :
        y[i] -= x[i]
    return y

if __name__ == "__main__"  :
    while True  :
        dt = deltaTime(INTERVAL)
        timeStamp = time.strftime(TIMEFORMAT)
        cpuPct = 100 - (dt[len(dt) - 1] * 100.00 / sum(dt))
        print timeStamp + "\t" + str('%.4f' %cpuPct)[/php]

sorry to bump the tread.
but could any one good in perl say how accurate this script will calculate the cpu % on 2 cores, 4 cores , ? may be small cluster of 5 PC ?

---

