---
title: "top question"
date: 2005-09-14
forum: Programming Talk
---

### Post by marguz on 2005-09-14
Does anyone know who top gets it %cpu usage? I know it's from the /proc, but I dont know where inside /proc. 

I would like to script the %cpu usage every 1 sec and have the output saved into a file with a time stamp on every line.


TIA

---

### Post by jerome bettis on 2005-09-14
hi

the file you're interested in is /proc/stat ... i wrote a simple python script to calculate the % a while back, i just modified it to add a time stamp.

```
#!/usr/bin/env python

import time

TIMEFORMAT = "%m/%d/%y %H:%M:%S"
INTERVAL = 1

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
		print timeStamp + "\t" + str('%.2f' %cpuPct) + "\t%"
```

you can put that in a file with a .py extension, do chmod 755 filename.py and ./filename.py to run it ... you can do ./filename.py > logfile to redirect the output to a file but i'm sure you knew that.

let me know if it works ok and if you want me to explain it .. if you have more than one cpu it might not behave right but that's an easy fix.

---

### Post by marguz on 2005-09-15
SWEET!

Thanks!

---

